### Version 1.0.0-beta01

Release date: 2014/10/17

#### Paradox is going Open Source! 

We are thrilled to announce that Paradox is going [open source on github](https://github.com/SiliconStudio/paradox)! This is an important step toward the **empowerment of game developers**. We hope that this will make you more confident in using Paradox. You will have also an unique opportunity to contribute to the project and see by yourself how Paradox engine is working.

More details at [http://paradox3d.net/blog/new-version-open-sourcing](http://paradox3d.net/blog/new-version-open-sourcing).

#### New Platforms 

 - **Windows RT/Store**
 - **Windows Phone**
 
#### New Samples

- **SimpleTerrain** that demonstrates how to generate an entity model/mesh at runtime by displaying a heightmap terrain
- **SimpleDynamicTexture** that demonstrates how to dynamically upload CPU textures to the GPU
- **RenderSceneToTexture** that shows how to render your models in a render target from another camera point of view and display in a texture

#### New Features
- Assets: Materials can be compiled into a shader without being attached to a mesh. Use the key MaterialAsset.GenerateShader in your pdxfxlib file to allow this feature.
- Engine: Add support for Windows Store and Windows Phone projects.
- Misc: Assemblies are now all signed.
- Studio: Create Windows Store and Phone Projects.
- Studio: Deploy Windows Phone project directly from Game Studio.
- Studio: Add and remove platforms of existing game. Force to regenerate platform specific projects.
- Studio: Choose what platforms to create when starting from a sample.
- UI: Add support for MouseOver on Windows (mainly MouseOverState property/event in UIElement)

#### Enhancements
- Samples: Load material and lighting configuration for the stand in ForwardLighting and DeferredLighting.
- Shaders: Incorrect shaders are no longer cached preventing NullReferenceException errors at compilation time.
- Studio: Generated solutions are created with VS2013 as default.
- Studio: The 'sprite' editor can now be used on UIImages too.
- UI: Improve default design of Button and EditText.
- UI: Make the EditText's caret blink and dissociate caret/selection colors.
- UI: Add support for mouse selection in EditText on Windows.
- UI: Create default design for ImageToggle.
- UI: UIImages are now regrouped into UIImageGroup the same way as SpriteGroup. The runtime-time and assets classes share the same hierarchy.

#### Issues fixed
- Assets: Orientation of meshes from the assimp importer is now correct ([#22](https://github.com/SiliconStudio/paradox/issues/22)).
- Assets: Mesh and materials are correctly associated during assimp import.
- Materials: Material always contains a diffuse part even if their color is black.
- Samples: Exhaustive shaders permutations for DeferredLighting.
- Shaders: The default shader is correct even when there is no parameter to generate it (no diffuse, no specular...).
- Shaders: Fix specular in deferred shading.
- Shaders: Correctly rename class in AmbientMapShading.pdxsl.
- Shaders: Fix issues related to geometry shader creation.
- Studio: New LightingAsset asset can be created in GameStudio.
- Studio: Unsupported assets are ignored when trying to be imported ([#42](https://github.com/SiliconStudio/paradox/issues/42)).
- Studio: Fix issue with asset thumbnails sometimes not being updated.
- Studio: Some properties of the Material assets displayed with wrong/missing controls.
- UI: Fix problem in Canvas MeasureOverride method when measured with infinite values.

#### Breaking changes
- Assets: SpriteGroup asset field 'Sprites' has been renamed 'Images' (.pdxsprite files can recovered by renaming the field inside the file).
- Assets: UIImage assets does not exist any more and have been replaced UIImageGroup assets. The old .pdxuiimg files cannot be easily recovered. The new .pdximage files can be easily created using the GameStudio 'sprite' editor.
- UI: EditText's EditInactiveImage and EditActiveImage properties have been renamed InactiveImage and ActiveImage.
- UI: Simplify ToggleButton. It now behaves like a Button with persistent states.

#### Known Issues
- iOS: On slow phones, app might be too slow to start with Visual Studio attached (it gets killed by iOS). We will rearrange our initialization sequence.
- iOS: Rebuild might sometime not use latest version.
- Samples: Due to the way we now create platform-specific projects, samples specific icons on non-Windows platforms are currently gone. Later, a project setting page in Game Studio should make this setting available again.
- Samples: Since there is no accelerometer Input API yet, Accelerometer sample is currently removed.
- Windows Store/Phone: UI EditText and Game Resume/Destroy cycles are not implemented.
- Windows Store/Phone: SharpFont.dll is still compiled against .NET 4.5 (might not pass certifications).
___

### Version 1.0.0-alpha11

Release date: 2014/10/10

#### Issues fixed
- Graphics: OpenGL ES rendering was broken due to a bug in Vertex Array Object.
- iOS: GraphicsDevice.UpdateSubresource() was using wrong OpenTK overload on iOS ([#35](https://github.com/SiliconStudio/paradox/issues/35)).
- iOS: libcore.a has been recompiled with libc++, to make it compatible with iOS 7+ ([#37](https://github.com/SiliconStudio/paradox/issues/37)).
- Shaders: Remove culture-dependant shader instanciation ([#38](https://github.com/SiliconStudio/paradox/issues/38)).

___

### Version 1.0.0-alpha10

Release date: 2014/10/06

#### New Features
- Studio: Cut/copy/paste assets and asset directories (also works between different instances of Paradox Studio).

#### Enhancements
- Assets: Allow to use materials with missing Texture references at runtime (nodes with missing reference are replaced by black color node).
- Assets: Increase FBX importer robustness to unsupported features (Log potential problems instead of failing).
- Assets: Improve Assimp importer to have a similar behavior to the FBX one.
- Assets: Added warnings for unsupported shaders features from materials (emissive, bump and reflection maps).
- Engine: Enhance Entity/EntityComponent API. Add collection initializers for Entity. Add easier method for getting a component.
- Shaders: Specular intensity, power and color are compositions, thus can be values or textures. This reflects the changes done in the FBX importer.
- Studio: Double-clicking on an Effect shader or an Effect compositor will open the shader file with a text editor (customizable in the settings).
- Studio: It is now possible to open an asset file either with a text editor, or any custom application associated with the file extension.
- Studio: Open the source file of an asset (texture, model...) in the context menu.

#### Issues fixed
- iOS: Paradox is now compatible with Xamarin iOS 8.2+ (Xamarin 3.7+).
- Graphics: Allow SpriteBatch to use a custom effect ([#30](https://github.com/SiliconStudio/paradox/issues/30)).
- Graphics: Use only space character in all pdxfx/pdxsl shaders ([#27](https://github.com/SiliconStudio/paradox/issues/27)).
- Shaders: Fix SV_InstanceID type in ShaderBase ([#33](https://github.com/SiliconStudio/paradox/issues/33)).
- Studio: Some windows being bigger than the screen resolution on low-resolution displays.
- Studio: Assets that were just added in the selected directory (from import, new, undo-delete...) were incorrectly sorted.
- Studio: SpriteGroup build is no longer re-triggered on selection.

___

### Version 1.0.0-alpha09

Release date: 2014/09/24

#### New Features
- Assets: Shadow map size is now editable on the LightComponent.
- Core: Add ray/rectangle collision method.
- Graphics: Variance shadow maps are available. HorizontalVsmBlur and VerticalVsmBlur need to be added to the pdxfxlib file of the project.
- Graphics: Shadow maps can be forced to fit within a constrained budget. Any extra shadow map won't be rendered. The processor classes handling this behavior are LightShadowProcessorWithBudget and LightShadowProcessorDefaultBudget. To ignore a shadow map budget, use DynamicLightShadowProcessor class. The later class is the one currently used in the Default pipeline.
- UI: Add a new UI element: Border.

#### Enhancements
- Assets: Rename ShadowMapLevelCount into ShadowMapCascadeCount in LightComponent.
- Assets: Rename LevelCount into CascadeCount in pdxlightconf files.
- Assets: Better handling of assets loading with same ids.
- Engine: Improve performance of shader live reloading (Windows only).
- Engine: Change some keys names from LightingKeys.xxx to Lighting.xxx. Xamarin Studio in the Settings menu to open solutions ([#5](https://github.com/SiliconStudio/paradox/issues/5)) ([#14](https://github.com/SiliconStudio/paradox/issues/14)).
- Engine: Raw asset files are now accessible through either AssetManager.FileProvider, or /asset mount point in VirtualFileSystem.
- Graphics: Share shadow map textures between shadow maps when it is possible.
- Studio: Add possibility to zoom in/out in asset preview with mouse wheel.
- Studio: Allow to choose between Default, Visual Studio 2012, Visual Studio 2013 and Xamarin Studio.
- Studio: Automatically reload source images in the Sprite Editor when they are modified by an external tool.
- Studio: Main window won't go outside of the screen even on small resolution ([#13](https://github.com/SiliconStudio/paradox/issues/13))
- Studio: Save window size and state (maximized/normal) when exiting, and restore these properties at next launch
- Studio: Improve zooming in the texture/sprite previews.
- Studio: Can undock Preview to a float window
- UI: Perform hit tests on CPU instead of GPU to avoid GPU stalls.
- UI: Add background color property to UIElement
- UI: Merge the different UI batch into a single one (more efficient batching and cleaner code).

#### Issues fixed
- Graphics: Fix false positive effect change detection.
- Graphics: Fix deferred lighting when there are several directional lights, spot lights or directional lights with shadow.
- Input: Support gamepads reconnected ([#20](https://github.com/SiliconStudio/paradox/issues/20))
- Input: Breaking changes: Input.KeyPressed, KeyReleased removed in favour of Input.KeyEvents ([#21](https://github.com/SiliconStudio/paradox/issues/21)).
- Input: Filter ALT, F10 keys to avoid blocking game ([#21](https://github.com/SiliconStudio/paradox/issues/21)).
- Shaders: Use light intensity in deferred lighting.
- Studio: Fix creating game or sample with spaces and dot in project name, and dots in namespace ([#16](https://github.com/SiliconStudio/paradox/issues/16)) ([#17](https://github.com/SiliconStudio/paradox/issues/17)).
- Studio: Fix settings saving when Paradox is installed on another drive that the system drive.
- Studio: Avoid compiling reference assemblies when creating a game from a sample template.
- Studio: Fix the time scale being sometimes incorrect in the animation preview.
- Studio: Fix crash when removing assets after being imported to a project
- UI: Fix elements' linear sampling by adding W component to vertices in UIImageBatch.
- UI: Fix TextBlock text positioning when element is rotated in 3D.
- Visual Studio Package: Ignore projects that are not C# (csproj) ([#18](https://github.com/SiliconStudio/paradox/issues/18)).
- Visual Studio Package: .pdxsl/.pdxfx code generator was not working without VSSDK installed ([#19](https://github.com/SiliconStudio/paradox/issues/19)).

___

### Version 1.0.0-alpha08

Release date: 2014/09/10

#### New Features
- Materials: detection of emissive maps when importing a FBX file.

#### Enhancements
- Assets: Lighting configurations are compiled like any assets which will speed up project compilation, especially when a configuration is shared by many meshes.
- Graphics: Better internal management of shadow maps. Once the entity the light is attached to is removed from the EntitySystem, the associated shadow map is destroyed. Turning a light on and off does not destroy it.
- Graphics: Add support in BatchBase for any vertex input layout and dynamic index buffer.
- Graphics: Add support for Texture.GetData with DoNotWait (desktop)
- Graphics: Better handling of full screen modes listing (desktop)
- Studio: Improve layout of the welcome page
- Studio: Sprite editor instances can be open only once for a given asset, and are properly closed when switching to another solution or if the asset is deleted.
- Studio: Display full MSBuild log when building projects (there were only errors before).
- Studio: Paradox Studio launcher can be moved and minimized.
- UI: Improve grid children measure process (fix some layout bugs).
- Samples: Improve layout of GameMenu sample.

#### Issues fixed
- Engine: Breaking change for GameTime class. Cleanup properties, remove GameTime.ElapsedGameTime/ElapsedUpdateTime and rename to Elapsed/Total.
- Graphics: Switch to fullscreen on desktop is now working properly.
- Graphics: Disabling sync with vertical retrace is now working properly.
- Graphics: Some intermediate render targets and textures weren't correctly destroyed when a renderer was removed.
- Graphics: Intel doesn't seem to support properly feature level 9.x (crash during creation of shader). Now fallbacks to level 10.
- Setup: Fix installation program and allow to change installation directory ([#2](https://github.com/SiliconStudio/paradox/issues/2))
- Studio: Fix "New Game Project" that was generating invalid projects with pdxfxlib files  
- Studio: Build is now correctly reevaluated when Visual Studio projects are changed from outside
- Studio: Some textboxes in the property grid were resetting the value when pressing Ctrl+S just after editing.
- Studio: Some keyboard shortcuts (Ctrl+A, Ctrl+I...) were not working until an asset was selected.
- Studio: The Sprite editor does not lock source image files anymore.
- Studio: Paradox Studio crashed when adding an Effect.Name (or any string) parameter to an Effect Library asset.
- UI: Fix bug in StackPanel measure process when children virtualization is enabled.
- Assets: Fix the problem of StaticSprite asset data not updating when changing the character set source file content.
- Visual Studio: When Paradox version is updated, Visual Studio plugin will now offer to update files so that IntelliSense can refresh its cache ([#10](https://github.com/SiliconStudio/paradox/issues/10)).

___

### Version 1.0.0-alpha07

Release date: 2014/09/04

#### Issues fixed
- Studio: Exiting the Paradox Studio was generating errors.

___

### Version 1.0.0-alpha06

Release date: 2014/09/04

#### New Features
- Integrated release notes in the welcome menu.
- Welcome to the new workspace!
- Integrate release notes in the new workspace.
- Engine: Reload automatically shaders at runtime when they are modified on the disk (Windows only).
- Shaders: New DiscardTransparentThreshold shader. Set the threshold below the one a pixel will be discarded.
- Shaders: New shaders dealing with normal and tangent skinning.
- Materials: Add UseTransparentMask parameter key in material to disable alpha blending and use the alpha channel as a mask of the texture. Use AlphaDiscardThreshold parameter key to set the desired threshold below the one a pixel will be discarded.
- Assets: Support for `TGA` and `PSD` files for textures.
- UI: Add horizontally align text in EditText using property TextAlignment.
- UI: Add mouse wheel delta value since last frame using property `IInputManager.MouseWheelDelta`.
- UI: Add image stretch type `StretchType.FillOnStretch` and modify `StretchType.Fill` behavior (previous `StretchType.Fill` mode is now implemented by `StretchType.FillOnStretch`).

#### Enhancements
- General: Visual Studio Express 2013 can now open Paradox Projects (with some limitations) ([#4](https://github.com/SiliconStudio/paradox/issues/4))
- Engine: Change default Windows output type to Windows Application ([#8](https://github.com/SiliconStudio/paradox/issues/8)): By default, a console is only opened when there is a message, assemblies are created in debug and the debugger is not attached.
- Engine: Add anisotropic texture filtering on mobile platforms that support it.
- Sample: AnimatedModel. Add lighting to the model. Use default Paradox pre defined shaders.
- Sample: ForwardLighting. Add transparent meshes.
- Sample: Set the same orientation for all samples on Android.
- Studio: Modal windows are not displayed in the taskbar anymore
- Studio: Improvement in the sprite editor: possibility to drop image files in the interface, improved region selection rectangle.
- Studio: Performance improvement in the editor, particularly in the sprite editor
- UI: Allow 0-sized strip definition in Grid.
- UI: Allow mixing of relative/absolute element positioning in Canvas.
- UI: Allow user to modify values of the UIRenderingContext.

#### Issues fixed
- Build: Android project fails to build ([#3](https://github.com/SiliconStudio/paradox/issues/3))
- Studio: GameStudio was using 100% of one CPU core ([#1](https://github.com/SiliconStudio/paradox/issues/1))
- Studio: Splash Screen always on top ([#6](https://github.com/SiliconStudio/paradox/issues/6))
- Studio: Fix GameStudio crash when importing assets using the add files button ([#9](https://github.com/SiliconStudio/paradox/issues/9))
- Studio: Build log is now displaying build feedback
- Studio: Fixed the Hue selection in the color picker
- Engine: Reduce effect change detection footprint (for example when changing the lighting configuration of the scene).
- Engine: Reuse rendering states.
- Shaders: Fix incorrect normal and tangent skinning in shaders.
- Shaders: Fix converter Hlsl to Glsl.
- Input: Fixed InputManager crash when window size is reach 0.
- Physics: Character Controller was not working properly on iOS.
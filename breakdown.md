Breakdown of the rendering process for FNA3D
- SDL initializes
- SDL window
- FNA3D device (needs FNA3D presentation parameters)
- - On resize: FNA3D Reset Backbuffer device, presentation parameters
- FNA3D vertex buffer (needs FNA3D device)
- For each render target (including the main RT & the window, finally)
- - FNA3D Set Viewport device, viewport
- - FNA3D Set Render Targets device, render target
- - FNA3D Clear
- - Load camera matrix into SpriteEffect shader's MatrixTransform
- - FNA3D Apply Effect SpriteEffect
- - Fill out SpriteBatch vertices
- - FNA3D Set Vertex Buffer Data device, vertex buffer, SpriteBatch vertices
- - FNA3D Apply Vertex Buffer Bindings device, vertex buffer binding (which contains vertexbuffer)
- - FNA3D Sampler State create
- - For each group of vertices using the same texture
- - - FNA3D Draw Primitives device, vertex index
- - - FNA3D Verify Sampler device, sampler state
- FNA3D Swap Buffers device
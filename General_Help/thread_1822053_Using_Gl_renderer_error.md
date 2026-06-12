---
title: "Using Gl renderer error"
date: 2011-08-10
forum: General Help
---

### Post by sinbowden on 2011-08-10
I get this error when i try to lanch openra

Using Gl renderer

Unhandled Exception: System.InvalidOperationException: GL Error: 1282
  at OpenRA.Renderer.Glsl.GraphicsDevice.CheckGlError () [0x00000] in <filename unknown>:0                            
  at OpenRA.Renderer.Glsl.Shader..ctor (OpenRA.Renderer.Glsl.GraphicsDevice dev, System.String type) [0x00000] in <filename unknown>:0                                           
  at OpenRA.Renderer.Glsl.GraphicsDevice.CreateShader (System.String name) [0x00000] in <filename unknown>:0          
  at OpenRA.Graphics.Renderer..ctor () [0x00000] in <filename unknown>:0                                              
  at OpenRA.Game.Initialize (OpenRA.Arguments args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0

---


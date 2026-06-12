---
title: "cant get bastion to work"
date: 2012-06-01
forum: General Help
---

### Post by vexaxv on 2012-06-01
whenever i run it if i move my mouse it closes and i ran it through the terminal
[http://pastebin.com/7SSV6DnN](http://pastebin.com/7SSV6DnN)

---

### Post by Mr Fat Bat on 2012-06-01
Bump on this one.  Got the same issue.

Occurs whenever I move the mouse, I get:

> Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for OpenTK.Input.Mouse ---> System.DllNotFoundException: libXi
  at (wrapper managed-to-native) OpenTK.Platform.X11.Functions:XISelectEvents (intptr,intptr,OpenTK.Platform.X11.XIEventMask&,int)
  at OpenTK.Platform.X11.Functions.XISelectEvents (IntPtr dpy, IntPtr win, XIEventMask mask) [0x00000] in <filename unknown>:0 
  at OpenTK.Platform.X11.XI2Mouse..ctor () [0x00000] in <filename unknown>:0 
  at OpenTK.Platform.X11.X11Factory.CreateMouseDriver () [0x00000] in <filename unknown>:0 
  at OpenTK.Input.Mouse..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at OpenTK.Platform.X11.X11GLNative.ProcessEvents () [0x00000] in <filename unknown>:0 
  at OpenTK.NativeWindow.ProcessEvents (Boolean retainEvents) [0x00000] in <filename unknown>:0 
  at OpenTK.NativeWindow.ProcessEvents () [0x00000] in <filename unknown>:0 
  at OpenTK.GameWindow.Run (Double updates_per_second, Double frames_per_second) [0x00000] in <filename unknown>:0 
  at OpenTK.GameWindow.Run (Double updateRate) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.GameWindow.Run (Double updateRate) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.LinuxGamePlatform.RunLoop () [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run (GameRunBehavior runBehavior) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run () [0x00000] in <filename unknown>:0 
  at GSGE.App.Run[App] () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeInitializationException: An exception was thrown by the type initializer for OpenTK.Input.Mouse ---> System.DllNotFoundException: libXi
  at (wrapper managed-to-native) OpenTK.Platform.X11.Functions:XISelectEvents (intptr,intptr,OpenTK.Platform.X11.XIEventMask&,int)
  at OpenTK.Platform.X11.Functions.XISelectEvents (IntPtr dpy, IntPtr win, XIEventMask mask) [0x00000] in <filename unknown>:0 
  at OpenTK.Platform.X11.XI2Mouse..ctor () [0x00000] in <filename unknown>:0 
  at OpenTK.Platform.X11.X11Factory.CreateMouseDriver () [0x00000] in <filename unknown>:0 
  at OpenTK.Input.Mouse..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at OpenTK.Platform.X11.X11GLNative.ProcessEvents () [0x00000] in <filename unknown>:0 
  at OpenTK.NativeWindow.ProcessEvents (Boolean retainEvents) [0x00000] in <filename unknown>:0 
  at OpenTK.NativeWindow.ProcessEvents () [0x00000] in <filename unknown>:0 
  at OpenTK.GameWindow.Run (Double updates_per_second, Double frames_per_second) [0x00000] in <filename unknown>:0 
  at OpenTK.GameWindow.Run (Double updateRate) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.GameWindow.Run (Double updateRate) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.LinuxGamePlatform.RunLoop () [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run (GameRunBehavior runBehavior) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run () [0x00000] in <filename unknown>:0 
  at GSGE.App.Run[App] () [0x00000] in <filename unknown>:0 


Cheers!

---

### Post by Mr Fat Bat on 2012-06-01
Scrap that, solution here for me:
[http://ubuntuforums.org/showpost.php?p=11987368&postcount=38](http://ubuntuforums.org/showpost.php?p=11987368&postcount=38)

Cheers!

---

### Post by Grandma_DOG on 2012-06-02
> **Mr Fat Bat said:**
> Scrap that, solution here for me:
[http://ubuntuforums.org/showpost.php?p=11987368&postcount=38](http://ubuntuforums.org/showpost.php?p=11987368&postcount=38)

Cheers!

-1 

Doesn't work for me. Tried it at the begining and the end of the file.
I'm trying to launch from Kubuntu by searching for 'Bastion' which it finds, i choose, it looks busy then crashes. 

When I hunt down Bastion it is in my /usr/local/games/Bastion
the executable looks like bastion.bin.x86 which i launch and it gives the error message of
 at Microsoft.Xna.Framework.Game.Initialize () [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run (GameRunBehavior runBehavior) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run () [0x00000] in <filename unknown>:0 
  at GSGE.App.Run[App] () [0x00000] in <filename unknown>:0 
  at GSGE.App.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.EntryPointNotFoundException: glProgramParameteri
  at (wrapper managed-to-native) OpenTK.Graphics.OpenGL.GL/Core:ProgramParameteri (uint,OpenTK.Graphics.OpenGL.AssemblyProgramParameterArb,int)
  at OpenTK.Graphics.OpenGL.GL.ProgramParameter (Int32 program, AssemblyProgramParameterArb pname, Int32 value) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Graphics.EffectPass.ApplyPass () [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Graphics.Effect.DefineTechnique (System.String techniqueName, System.String passName, Int32 vertexIndex, Int32 fragmentIndex) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Graphics.SpriteEffect..ctor (Microsoft.Xna.Framework.Graphics.GraphicsDevice graphicsDevice) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Graphics.SpriteBatch..ctor (Microsoft.Xna.Framework.Graphics.GraphicsDevice graphicsDevice) [0x00000] in <filename unknown>:0 
  at GSGE.ExceptionGame.LoadContent () [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Initialize () [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run (GameRunBehavior runBehavior) [0x00000] in <filename unknown>:0 
  at Microsoft.Xna.Framework.Game.Run () [0x00000] in <filename unknown>:0 
  at GSGE.App.Run[App] () [0x00000] in <filename unknown>:0 
  at GSGE.App.Main (System.String[] args) [0x00000] in <filename unknown>:0 

so I've written off the game from Humble Bundle. It isn't my job to fix their software.

---

### Post by jim_deadlock on 2012-06-02
As well as the solution above, you should also install to your home folder rather than the default path. Doing both of these things fixed it for me. I would recommend perseverance, it's a fantastic game.

---


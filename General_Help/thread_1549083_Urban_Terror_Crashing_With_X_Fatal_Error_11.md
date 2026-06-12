---
title: "Urban Terror Crashing With X Fatal Error 11"
date: 2010-08-09
forum: General Help
---

### Post by Augustus Maxim on 2010-08-09
Quake 3, Tremulous, and Urban Terror crash with XIO: fatal error 11. The screen briefly goes blank and then the monitor gives the me the same message as if the computer is off and there is no video output. ("Off in 5 seconds," or something like that.) You can't switch to a new TTY session, it doesn't respond to input, but if you quickly hit the power button (not long enough for the machine shutdown, just long enough for the system to recognize there was a button hit) the Ubuntu logo with dots comes up and shuts the machine down. Here is the STDERR from Urban Terror:
```
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
8032 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 845G GEM 20091221 2009Q4 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G GEM 20091221 2009Q4 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 7.7.1
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "pulse".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  256
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
 8192 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x98ccb00 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 518 milli seconds
UI menu load time = 334 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: Onyx
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
../../intel/intel_bufmgr_gem.c:1152: Error setting memory domains 2 (00000040 00000000): Input/output error .
../../intel/intel_bufmgr_gem.c:1152: Error setting memory domains 1 (00000040 00000000): Input/output error .
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0" 
      after 41 requests (39 known processed) with 0 events remaining.
```Any help is appreciated and thank you in advance,
Augustus.

---


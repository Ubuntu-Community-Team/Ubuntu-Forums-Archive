---
title: "the sims 8 in 1, Wine, need help"
date: 2010-06-14
forum: General Help
---

### Post by Nimbus-cloud on 2010-06-14
I downloaded the sims 8 in 1, its the full all 8 original sims games all in one package it installed all of them at once (its great ^_^) but when i click on applications/wine/maxis/sims 8 in 1 it trys to open it, it makes the screen go black it trys to render the screen the resolution gets real big then goes black again and goes back to normal then nothing.

i cant seem to see what the problem is, id rather you email me but you can post too ill just have to get on here more often ^_^.  [EMAIL="Nimbus-cloud@hotmail.com"]Nimbus-cloud@hotmail.com[/EMAIL]

I almost forgot heres the debug I have..  
```
 nim@Nebula:~/.wine/drive_c/Program Files/Maxis/The Sims 8 in 1/The Sims$ wine "Sims.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x32f26c,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0x161f20) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x1624a0 with type 1,WINED3DRTYPE_SURFACE
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
err:ddraw:PixelFormat_DD2WineD3D Unknown Pixelformat!
err:ddraw:IDirectDrawImpl_CreateNewSurface Unsupported / Unknown pixelformat
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 88760091
wine: Unhandled page fault on read access to 0xffffffff at address 0xffffffff (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0xffffffff).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:ffffffff ESP:0032f980 EBP:0032fa14 EFLAGS:00210202(   - 00      - -RI1)
 EAX:0032fab0 EBX:009b2e78 ECX:0032fc30 EDX:7d986d70
 ESI:009b3b0c EDI:0032f9fc
Stack dump:
0x0032f980:  005c8b2f 0032fab0 009b2f84 009b2e78
0x0032f990:  00000000 0000007c 00001007 00000258
0x0032f9a0:  00000320 00000000 00000000 00000000
0x0032f9b0:  00000000 00000000 00000000 00000000
0x0032f9c0:  00000000 00000000 00000000 00000000
0x0032f9d0:  00000000 00000000 00000000 00000020
Backtrace:
=>1 0xffffffff (0x0032fa14)
  2 0x005c8367 in sims (+0x1c8367) (0x0032fabc)
  3 0x004fb8c7 in sims (+0xfb8c7) (0x0032fc3c)
  4 0x004ef5eb in sims (+0xef5eb) (0x0032fdf8)
  5 0x00602f5b in sims (+0x202f5b) (0x0032fe14)
  6 0x005d5cee in sims (+0x1d5cee) (0x00676a6c)
  7 0x00602ee4 in sims (+0x202ee4) (0x00602e48)
0xffffffff: -- no code accessible --
Modules:
Module    Address            Debug info    Name (100 modules)
PE      390000-  3b5000    Deferred        ijl10
PE      400000-  70d39e    Export          sims
PE    60000000-600e0000    Deferred        gimex
ELF    7b800000-7b93d000    Deferred        kernel32<elf>
  \-PE    7b820000-7b93d000    \               kernel32
ELF    7bc00000-7bca7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c156000-7c1a2000    Deferred        dsound<elf>
  \-PE    7c160000-7c1a2000    \               dsound
ELF    7c1e2000-7c24e000    Deferred        msvcrt<elf>
  \-PE    7c1f0000-7c24e000    \               msvcrt
ELF    7c24e000-7c277000    Deferred        msvfw32<elf>
  \-PE    7c250000-7c277000    \               msvfw32
ELF    7d4a2000-7d714000    Deferred        i965_dri.so
ELF    7d714000-7d777000    Deferred        libgl.so.1
ELF    7d777000-7d88c000    Deferred        wined3d<elf>
  \-PE    7d790000-7d88c000    \               wined3d
ELF    7d8d6000-7d8fd000    Deferred        dmusic<elf>
  \-PE    7d8e0000-7d8fd000    \               dmusic
ELF    7d8fd000-7d907000    Deferred        libdrm_intel.so.1
ELF    7d907000-7d911000    Deferred        libdrm.so.2
ELF    7d92f000-7d987000    Deferred        ddraw<elf>
  \-PE    7d940000-7d987000    \               ddraw
ELF    7d987000-7d99c000    Deferred        midimap<elf>
  \-PE    7d990000-7d99c000    \               midimap
ELF    7d99c000-7d9c4000    Deferred        msacm32<elf>
  \-PE    7d9a0000-7d9c4000    \               msacm32
ELF    7e1c5000-7e1cb000    Deferred        libattr.so.1
ELF    7e1cb000-7e1d2000    Deferred        libgdbm.so.3
ELF    7e1d2000-7e1d7000    Deferred        libcap.so.2
ELF    7e1d7000-7e236000    Deferred        libpulse.so.0
ELF    7e236000-7e23f000    Deferred        librt.so.1
ELF    7e23f000-7e307000    Deferred        libasound.so.2
ELF    7e309000-7e30c000    Deferred        libxdamage.so.1
ELF    7e30c000-7e325000    Deferred        msacm32<elf>
  \-PE    7e310000-7e325000    \               msacm32
ELF    7e325000-7e35c000    Deferred        winealsa<elf>
  \-PE    7e330000-7e35c000    \               winealsa
ELF    7e39c000-7e3cf000    Deferred        uxtheme<elf>
  \-PE    7e3a0000-7e3cf000    \               uxtheme
ELF    7e3cf000-7e3d8000    Deferred        libxcursor.so.1
ELF    7e3d8000-7e3dd000    Deferred        libxfixes.so.3
ELF    7e3dd000-7e3e1000    Deferred        libxcomposite.so.1
ELF    7e3e1000-7e3e9000    Deferred        libxrandr.so.2
ELF    7e3e9000-7e3f3000    Deferred        libxrender.so.1
ELF    7e3f3000-7e3f6000    Deferred        libxinerama.so.1
ELF    7e3f6000-7e3fb000    Deferred        libxdmcp.so.6
ELF    7e3fb000-7e415000    Deferred        libxcb.so.1
ELF    7e415000-7e419000    Deferred        libxau.so.6
ELF    7e419000-7e41e000    Deferred        libuuid.so.1
ELF    7e41e000-7e50d000    Deferred        libx11.so.6
ELF    7e50d000-7e51d000    Deferred        libxext.so.6
ELF    7e51d000-7e523000    Deferred        libxxf86vm.so.1
ELF    7e523000-7e53b000    Deferred        libice.so.6
ELF    7e53b000-7e544000    Deferred        libsm.so.6
ELF    7e544000-7e54b000    Deferred        libasound_module_pcm_pulse.so
ELF    7e562000-7e5fd000    Deferred        winex11<elf>
  \-PE    7e570000-7e5fd000    \               winex11
ELF    7e6ca000-7e6f1000    Deferred        libexpat.so.1
ELF    7e6f1000-7e71e000    Deferred        libfontconfig.so.1
ELF    7e71e000-7e734000    Deferred        libz.so.1
ELF    7e734000-7e7ab000    Deferred        libfreetype.so.6
ELF    7e7c9000-7e7ea000    Deferred        imm32<elf>
  \-PE    7e7d0000-7e7ea000    \               imm32
ELF    7e7ea000-7e87e000    Deferred        winmm<elf>
  \-PE    7e800000-7e87e000    \               winmm
ELF    7e87e000-7e893000    Deferred        lz32<elf>
  \-PE    7e880000-7e893000    \               lz32
ELF    7e893000-7e8a9000    Deferred        libresolv.so.2
ELF    7e8ac000-7e8c7000    Deferred        version<elf>
  \-PE    7e8b0000-7e8c7000    \               version
ELF    7e8c7000-7e8e6000    Deferred        iphlpapi<elf>
  \-PE    7e8d0000-7e8e6000    \               iphlpapi
ELF    7e8e6000-7e949000    Deferred        rpcrt4<elf>
  \-PE    7e8f0000-7e949000    \               rpcrt4
ELF    7e949000-7e9ef000    Deferred        ole32<elf>
  \-PE    7e960000-7e9ef000    \               ole32
ELF    7e9ef000-7eab4000    Deferred        comctl32<elf>
  \-PE    7ea00000-7eab4000    \               comctl32
ELF    7eab4000-7eb0f000    Deferred        shlwapi<elf>
  \-PE    7eac0000-7eb0f000    \               shlwapi
ELF    7eb0f000-7ec23000    Deferred        shell32<elf>
  \-PE    7eb20000-7ec23000    \               shell32
ELF    7ec23000-7ec76000    Deferred        advapi32<elf>
  \-PE    7ec30000-7ec76000    \               advapi32
ELF    7ec76000-7ed16000    Deferred        gdi32<elf>
  \-PE    7ec90000-7ed16000    \               gdi32
ELF    7ed16000-7ee62000    Deferred        user32<elf>
  \-PE    7ed30000-7ee62000    \               user32
ELF    7ef8c000-7ef98000    Deferred        libnss_files.so.2
ELF    7ef98000-7efa3000    Deferred        libnss_nis.so.2
ELF    7efa3000-7efbc000    Deferred        libnsl.so.1
ELF    7efbc000-7efe2000    Deferred        libm.so.6
ELF    b7413000-b7417000    Deferred        libdl.so.2
ELF    b7417000-b757a000    Deferred        libc.so.6
ELF    b757b000-b7594000    Deferred        libpthread.so.0
ELF    b7597000-b75a0000    Deferred        libnss_compat.so.2
ELF    b75b2000-b76e9000    Deferred        libwine.so.1
ELF    b76eb000-b7709000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Maxis\The Sims 8 in 1\The Sims\Sims.exe
    0000001a   15
    00000019   15
    00000009    0 <==
0000000c 
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000016 
    00000017    0
Backtrace:
=>1 0xffffffff (0x0032fa14)
  2 0x005c8367 in sims (+0x1c8367) (0x0032fabc)
  3 0x004fb8c7 in sims (+0xfb8c7) (0x0032fc3c)
  4 0x004ef5eb in sims (+0xef5eb) (0x0032fdf8)
  5 0x00602f5b in sims (+0x202f5b) (0x0032fe14)
  6 0x005d5cee in sims (+0x1d5cee) (0x00676a6c)
  7 0x00602ee4 in sims (+0x202ee4) (0x00602e48)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
nim@Nebula:~/.wine/drive_c/Program Files/Maxis/The Sims 8 in 1/The Sims$ 

```
thanks guys.

Echo Nimbus.

---

### Post by EvilTaj on 2011-04-04
I'm having the same issue; if anyone could help it would be greatly appreciated.  I've got mono and am very bored!

---


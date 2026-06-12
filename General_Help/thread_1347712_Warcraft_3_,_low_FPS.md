---
title: "Warcraft 3 , low FPS"
date: 2009-12-06
forum: General Help
---

### Post by domagoj91 on 2009-12-06
I am trying to run warcraft 3 TFT with wine, till now i couldn't solve my problems with FPS. First I disabled all my desktop effects but there was no change in computer behaviour. Second, when I am runing Warcraft 3 system speed is not affected only warcraft has low fps, so I am thinking that this is some kind of software issue. My graphic card drivers are the latest ( for my Mobility Radeon 7500 card).

> altair@altair-laptop:~$ wine "c:/Program Files/Warcraft III/War3.exe"
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f374,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f640,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f670,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub



> altair@altair-laptop:~$ wine "c:/Program Files/Warcraft III/War3.exe" -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f374,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f640,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f670,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub


---


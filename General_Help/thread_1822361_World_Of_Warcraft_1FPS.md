---
title: "World Of Warcraft 1FPS"
date: 2011-08-10
forum: General Help
---

### Post by EpicFailGuy on 2011-08-10
First, Sorry for Poor english but i coulnt find enough help in my language,

and i'm new ubuntu user..

i copied wow disk to disk (not downloaded again)

after, i installed Play on linux (with wine 1.2.2)

than; 
i did that: 
Open config.wtf using a text editor and add or change the following line: 
SET gxApi "opengl"
SET ffxDeath "0" SET ffxGlow "0"
SET M2UseShaders "0"
---
regedit tweaks for OpenGL
----
after;
i downloaded wine 1.3.18 
----
i downloaded "Crossover games" trial.
it couldnt worked on that..
-----


the logs:
~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
wine: cannot find L"C:\\windows\\system32\\plugplay.exe"
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:grin:wmIsCompositionEnabled 0x33d04c
fixme:iphlpapi:NotifyAddrChange (Handle 0xa5de8d8, overlapped 0xa5de8e0): stub
wine: configuration in '/home/samet/.wine' has been updated.
err:winediag:X11DRV_WineGL_InitOpenglInfo  The Mesa OpenGL driver is  using software rendering, most likely your  OpenGL drivers haven't been  installed correctly
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
archive Data/Cache/SoundCache-1.MPQ opened
archive Data/Cache/SoundCache-2.MPQ opened
archive Data/Cache/SoundCache-3.MPQ opened
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enGB/SoundCache-enGB.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enGB/patch-enGB-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enGB/patch-enGB-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enGB/patch-enGB-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enGB/patch-enGB-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13329.MPQ opened
archive Data/wow-update-13596.MPQ opened
archive Data/Cache/patch-base-13596.MPQ opened
archive Data/Cache/enGB/patch-enGB-13596.MPQ opened
archive Data/Cache/SoundCache-patch-13596.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13596.MPQ opened
archive Data/wow-update-13623.MPQ opened
archive Data/Cache/patch-base-13623.MPQ opened
archive Data/Cache/enGB/patch-enGB-13623.MPQ opened
archive Data/Cache/SoundCache-patch-13623.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13623.MPQ opened
archive Data/wow-update-base-13914.MPQ opened
archive Data/enGB/wow-update-enGB-13914.MPQ opened
archive Data/Cache/patch-base-13914.MPQ opened
archive Data/Cache/enGB/patch-enGB-13914.MPQ opened
archive Data/Cache/SoundCache-patch-13914.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-13914.MPQ opened
archive Data/wow-update-base-14007.MPQ opened
archive Data/enGB/wow-update-enGB-14007.MPQ opened
archive Data/Cache/patch-base-14007.MPQ opened
archive Data/Cache/enGB/patch-enGB-14007.MPQ opened
archive Data/Cache/SoundCache-patch-14007.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14007.MPQ opened
archive Data/wow-update-base-14333.MPQ opened
archive Data/enGB/wow-update-enGB-14333.MPQ opened
archive Data/Cache/patch-base-14333.MPQ opened
archive Data/Cache/enGB/patch-enGB-14333.MPQ opened
archive Data/Cache/SoundCache-patch-14333.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14333.MPQ opened
archive Data/wow-update-base-14480.MPQ opened
archive Data/enGB/wow-update-enGB-14480.MPQ opened
archive Data/Cache/patch-base-14480.MPQ opened
archive Data/Cache/enGB/patch-enGB-14480.MPQ opened
archive Data/Cache/SoundCache-patch-14480.MPQ opened
archive Data/Cache/enGB/SoundCache-patch-enGB-14480.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\sound.MPQ opened
archive Data\world.MPQ opened
archive Data\art.MPQ opened
fixme:ntdll:find_reg_tz_info  Can't find matching timezone information  in the registry for bias -120,  std (d/m/y): 30/10/2011, dlt (d/m/y):  28/03/2011
fixme:win:EnumDisplayDevicesW ((null),0,0x32eccc,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32G32_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16G16_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
fixme:d3d:check_filter Error during filtering test for format 822d, returning no filtering
fixme:d3d:check_filter Error during filtering test for format 822f, returning no filtering
fixme:win:EnumDisplayDevicesW ((null),0,0x32e998,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32G32_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16G16_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
fixme:d3d:check_filter Error during filtering test for format 822d, returning no filtering
fixme:d3d:check_filter Error during filtering test for format 822f, returning no filtering
fixme:win:EnumDisplayDevicesW ((null),0,0x32f338,0x00000000), stub!
fixme:d3d9:grin:3DPERF_SetOptions (0x1) : stub
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x32f0e8,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32G32_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16G16_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
fixme:d3d:check_filter Error during filtering test for format 822d, returning no filtering
fixme:d3d:check_filter Error during filtering test for format 822f, returning no filtering
fixme:win:EnumDisplayDevicesW ((null),0,0x32edb4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x172a48,0x17b21:cool:: stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x172a48,0x17b21:cool:: stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f86c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f338,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R32G32_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16_FLOAT with  rendertarget flag is not supported as  FBO color attachment, and no  fallback specified.
err:d3d:check_fbo_compat   >>>>>>>>>>>>>>>>>   GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat  Format WINED3DFMT_R16G16_FLOAT with  rendertarget flag is not supported  as FBO color attachment, and no  fallback specified.
fixme:d3d:check_filter Error during filtering test for format 822d, returning no filtering
fixme:d3d:check_filter Error during filtering test for format 822f, returning no filtering
fixme:win:EnumDisplayDevicesW ((null),0,0x32f004,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000

---


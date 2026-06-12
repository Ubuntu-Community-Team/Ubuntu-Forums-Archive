---
title: "BadWindow when trying to launch StarCraft 2"
date: 2012-01-25
forum: General Help
---

### Post by heysean on 2012-01-25
Hi everybody!

I've been trying to get StarCraft 2 running for quite some time now, and keep getting this every time I run the executable:

```
sean@ubuntu:/media/9A08DB9408DB6E2F/StarCraft II$ wine StarCraft\ II.exe 
err:winediag:wined3d_dll_init The GLSL shader backend has been disabled. You get to keep all the pieces if it breaks.
fixme:process:GetLogicalProcessorInformation ((nil),0x32dca0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0xe3c2e0,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 3000
fixme:process:GetLogicalProcessorInformation ((nil),0x103c5a0): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x103c58c): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 2000
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation ((nil),0x113e998): stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation ((nil),0x113e998): stub
sean@ubuntu:/media/9A08DB9408DB6E2F/StarCraft II$ fixme:shell:SetCurrentProcessExplicitAppUserModelID L"BlizzardEntertainment.StarCraftII.StarCraftII": stub
err:winediag:wined3d_dll_init The GLSL shader backend has been disabled. You get to keep all the pieces if it breaks.
fixme:process:SetProcessDEPPolicy (1): stub
fixme:process:GetLogicalProcessorInformation (0x33fa3c,0x33fd3c): stub
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x143330, 0x450f0d4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x450ed40,0x450ed44): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x450e9f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x450e904,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x450eee4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x450e7bc,0x00000000), stub!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  10 (X_UnmapWindow)
  Resource id in failed request:  0x4a00001
  Serial number of failed request:  180
  Current serial number in output stream:  183
^C
sean@ubuntu:/media/9A08DB9408DB6E2F/StarCraft II$ wine regedit
sean@ubuntu:/media/9A08DB9408DB6E2F/StarCraft II$ wine StarCraft\ II.exe 
fixme:process:GetLogicalProcessorInformation ((nil),0x32dca0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0xe3c2e0,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 3000
fixme:process:GetLogicalProcessorInformation ((nil),0x103c5a0): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x103c58c): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 2000
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation ((nil),0x113e998): stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation ((nil),0x113e998): stub
sean@ubuntu:/media/9A08DB9408DB6E2F/StarCraft II$ fixme:shell:SetCurrentProcessExplicitAppUserModelID L"BlizzardEntertainment.StarCraftII.StarCraftII": stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:process:GetLogicalProcessorInformation (0x33fa3c,0x33fd3c): stub
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x143330, 0x450f0d4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x450ed40,0x450ed44): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x450e9f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x450e904,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x450eee4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x450e7bc,0x00000000), stub!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  10 (X_UnmapWindow)
  Resource id in failed request:  0x4a00001
  Serial number of failed request:  180
  Current serial number in output stream:  183

```

I've been searching for BadWindow errors that people have gotten, and the only fixes I've seen were from installing the latest Nvidia drivers, which I have done already. When I run the command, the screen flickers for a second like the window was created and then destroyed very quickly. Not really sure what to do. Using a GeForce 550 TI.

Edit:
Oh, I also have it shown running it twice, the first time is with the following Direct3D registry key in, and the second one without. I had seen that it fixed some stuff over on the WineHQ page, so I decided to give it a shot. Not sure if I should leave it in or not.



[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"Multisampling"="disabled"
"OffScreenRenderingMode"="pbuffer"
"UseGLSL"="disabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="1024"

---


---
title: "Fireworks CS3\CS4 on Ubuntu 9.10 under wine"
date: 2010-01-19
forum: General Help
---

### Post by gfd_ck on 2010-01-19
Hi. 

I immediately apologize for his English. 

Faced with launching Fireworks CS3CS4 on Ubuntu 9.10 under wine. 

The problem is that when you run an already installed Fireworks appear a window where I must agree with the terms of the license. The text of the license is not displayed and not one of the three buttons (accept, reject, ...) in this box does not work. Thus in wine says that Fireworks has a gold status. 
Attempts to establish Fireworks also fails, and then I found information that the installation really is a problem and need to run pre-installed Fireworks. 

All information on this subject, which I found, describes the launch Fireworks in older versions of Ubuntu (in Ubuntu 8.10 I ran Fireworks 8 without problems). And I never met a description of the problem, which I have. 

Maybe someone installed Fireworks CS3CS4 on Ubuntu 9.10, and he had a similar problem or someone knows, so this may be due and possible solutions. 

Here is what the terminal:

```

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
fixme:heap:HeapSetInformation 0x110000 0 0x32fc80 4
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\media\\Soft\\Windows\\Work\\Graphyc\\FireworksCS3\\Microsoft.VC80.MFCLOC\\Microsoft.VC80.MFCLOC.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC"
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x170f44 0x170f50 0x170be8 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x170f44 0x170f50 0x170be8 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x170b8c 0x170b98 0x172ef0 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x170bec 0x170bf8 0x170c40 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:shdocvw:PersistStreamInit_InitNew (0x174fd0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32abb8:3; TargetFrameName 0x32aba8:
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:bind_to_object BindToObject failed: 80004005
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x174fd0)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32abdc:3; TargetFrameName 0x32abcc:
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e19f9b8, overlapped 0x7e19f99c): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x6d8ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x17506c)->((null) 1 0x32a9cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 25 2 0x32a9e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 26 2 0x32a9e0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x17506c)->(0x32aa24)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32aae0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32ab70)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 29 2 0x32b28c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x17506c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32b1bc)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:get_script_host Ignoring JScript
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32b1bc)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:nsChannel_GetContentLength default action not implemented
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:get_script_host Ignoring JScript
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32b1bc)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:nsChannel_GetContentLength default action not implemented
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:get_script_host Ignoring JScript
fixme:mshtml:get_script_host Ignoring JScript
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32b1bc)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32b1bc)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:shdocvw:ClientSite_GetContainer (0x17506c)->(0x32b204)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x17506c)->(0x6003eb71)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 25 2 0x32b110 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 26 2 0x32b110 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32b1cc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32b1cc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 26 2 0x32b26c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 29 2 0x32b27c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x17506c)->(0x7bca561a)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 28 2 0x32b1cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17506c)->((null) 21 2 (nil) (nil))

```

Thank you.

---


---
title: "running 123di in wine"
date: 2010-05-23
forum: General Help
---

### Post by oomisilekootsi on 2010-05-23
Hi everybody!

I've been trying to get the photography learning software, 123di, to run on linux using wine and am already at my wit's end. I have tried many versions of wine in puppylinux, mepis, and ubuntu but the best I could get is a screen saying "page not found" and a "Gilead" logo... Finally I've settled on wine 1.0.0 on ubuntu 8.10 after trying out the latest version from winehq. 

I have limited internet connectivity right now so I cannot afford to download the debug-cab-files.  Thanks.


```
myname@abc:~/MyDownloads$ wine 123di_62_demo.exe
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
num bytes of app code: 1097728, 0.0KBnum bytes of data: 8200780, 8008.6KBfixme:shdocvw:PersistStreamInit_InitNew (0x139818)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7da98a08, overlapped 0x7da989ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x123ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1398b4)->((null) 1 0x32d970 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->((null) 25 2 0x32d984 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->((null) 26 2 0x32d984 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1398b4)->(0x32d9c0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32da84 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x138908)->(L"" L"" 0 0x32dabc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->((null) 29 2 0x32fbf4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1398b4)
fixme:shdocvw:ClientSite_GetContainer (0x1398b4)->(0x32fba8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1398b4)->(0xb7ea66d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->((null) 25 2 0x32fadc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->((null) 26 2 0x32fadc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1398b4)->((null) 28 2 0x32fb94 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x139818)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14ef10)->((nil))
fixme:shdocvw:OleObject_Close (0x139818)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
```

---


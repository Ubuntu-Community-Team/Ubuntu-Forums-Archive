---
title: "Terminal's Diagnose (Crashing)"
date: 2011-04-16
forum: General Help
---

### Post by Julian Luna on 2011-04-16
Hello comunity I wish I can get some support to help me understand what's going on and how to fix this crash. This is the terminal's lines

julian@julian-A780GM-A:~$ wine /home/julian/.wine/dosdevices/c:/AirRivals/AirRivals.exe
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
julian@julian-A780GM-A:~$ fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0xf3e8d8, overlapped 0xf3e8bc): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33d4a8,0x00000000), stub!
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x180940)->((null) 1 0x33e0c4 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1b7e48)->()
fixme:shdocvw:ClientSite_GetContainer (0x180940)->(0x33e094)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1b7e48)->(0x33d38c)
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x180940)
fixme:shdocvw:ClientSite_GetContainer (0x180940)->(0x33eb88)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1884d0)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1889a0)->()
fixme:mshtml:nsChannel_SetResponseHeader (0x1b7e48)->("content-type" "text/html; charset=utf-8" 1)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x19a698)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x181600)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x181b98)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1883b8)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x188530)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x188a00)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x188e98)->(0x33e534 0x33e50c 0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x188dc0)->(0x33dc70)
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 01-Jan-2038 00:00:00 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 01-Jan-2038 00:00:00 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 01-Jan-2038 00:00:00 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 01-Jan-2038 00:00:00 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 16-Apr-2010 17:22:26 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 16-Apr-2010 17:22:26 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 01-Jan-2038 00:00:00 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 01-Jan-2038 00:00:00 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 01-Jan-2038 00:00:00 GMT")
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x181bf8)->(0x33dc70)
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1889a0)->(0x33db74)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x19aa60)->(0x33dc70)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1884d0)->(0x33db74)
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x181c50)->(0x33d660 0x33d638 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1883b8)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1c4880)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1c59c0)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x1bd668)->()
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x19aa50)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1c4468)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1bd568)->(0x33e534 0x33e50c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1bd8e8)->(0x33e534 0x33e50c 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1c59c0)->(0x33db74)
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1bd668)->(0x33db74)
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x181bf0)->(0x33cd9c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1883b8)->(0x33cca0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1c4880)->(0x33db74)
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
wine: Call from 0x7bc4afc0 to unimplemented function msvcrt.dll._snwprintf_s, aborting
wine: Unimplemented function msvcrt.dll._snwprintf_s called at address 0x7bc4afc0 (thread 0021), starting debugger...
julian@julian-A780GM-A:~$

Then the application freezes, and the following message is displayed:

"[I]The program Launcher.atm has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem or a deficiency in Wine. You might want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If the problem is not present under windows and has not been reported yet, you can report it at [http://bugs.winehq.org](http://bugs.winehq.org)[/I]"

Hope I can get to run it properly, thanks

---


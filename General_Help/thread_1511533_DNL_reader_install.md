---
title: "DNL reader install"
date: 2010-06-16
forum: General Help
---

### Post by raffi_1970 on 2010-06-16
Hi,

I'm trying to install [DNL Reader]("http://dnl-reader.en.softonic.com/") , which is a Windows file. I have had no luck in getting it to install.

I'm running Karmic Koala.

Also, I'm rather new to Ubuntu. And not sure how capable I am with using Wine either (I haven't been able to add any appications to run on Wine. I can go to the configure Wine window, add the program and then what?

Does DNL Reader exist for linux or some simple workaround for reading password protected e-books with .dnl extensions?

Thanks!
Raffi

---

### Post by raffi_1970 on 2010-06-17
Update:

I tried installing it in terminal with the command:

wine /location/filename.exe and I got

fixme:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:shdocvw:PersistStorage_InitNew (0x131640)->(0x8ee82c)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 17-Jun-2011 03:53:12 GMT; path=/; domain=softonic.com")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Fri, 17-Jun-2011 03:53:12 GMT; path=/; domain=softonic.com")
fixme:system:SetProcessDPIAware stub!
fixme:dwmapiwmIsCompositionEnabled 0x32e334
fixme:iphlpapi:NotifyAddrChange (Handle 0x249e8d8, overlapped 0x249e8e0): stub
0[141020]: IMM32: InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1316e->((null) 1 0x32ea74 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x26a97b->()
fixme:shdocvw:ClientSite_GetContainer (0x1316e->(0x32ea3c)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestHeader (0x26a97b->(0x32d590 0x26aae2c)
fixme:mshtml:nsChannel_GetRequestMethod (0x26a97b\->(0x32d750)
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsChannel_GetReferrer (0x26a97b->(0x32dc70)
fixme:mshtml:nsChannel_IsNoStoreResponse (0x26a97b->(0x32db5c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x26a97b->(0x32db5
fixme:mshtml:nsChannel_GetReferrer (0x26a97b->(0x32dcb0)
fixme:mshtml:nsChannel_Open (0x26c181->(0x32aa00)
fixme:mshtml:nsChannel_SetRequestHeader (0x26c4d4->(0x32d930 0x32d940 0)
fixme:mshtml:nsChannel_SetReferrer (0x26c4d4->(0x26abd3
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvwocHostUIHandler_GetDropTarget (0x1316e
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x26c0f5->(0x32eb1c 0x32eb08 0)
fixme:shdocvw:ClientSite_GetContainer (0x1316e\->(0x32f07c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1316e->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x26c4d4->(0x32e61
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1316e->(L"Done")
fixme:mshtml:nsChannel_IsNoStoreResponse (0x26a97b->(0x32ed2c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x26a97b->(0x32ed2\
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvwropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:mshtml:CustomDoc_SetUIHandler (0x13b72->(0x8f59c

and also Wine ran a installation and download status window which doesn't stop...

(note, the text above is edited because some of the text displays here at smilies, and the forums only allow the display of 8 smilies...

---

### Post by raffi_1970 on 2010-06-22
Ok, somehow I got the DNL reader to install and I was able to open and read the book in DNL Reader. 

The hyperlinks, however, in the book don't open. Any ideas about how to make that happen?

Thanks!

---


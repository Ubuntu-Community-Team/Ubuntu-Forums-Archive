---
title: "Wine can't access internet!"
date: 2011-04-28
forum: General Help
---

### Post by joelstitch on 2011-04-28
I notice for a while that every time I try to install a program that download files from the internet as part of the setup Wine (wine-1.2.2) doesn't installs it. I tried opening Internet Explorer in Wine and it's also not going online. I am trying to install Google Chrome trough Wine (I know there's an Ubuntu version but I need one in Wine as well) and I am getting this error:

> Installation failed. Ensure that your computer is connected to the Internet and that your firewall allows GoogleUpdate.exe to connect and then try again. Error code = 0x80070057.And this is what I get on the terminal when I open the ChromeSetup.exe:

```
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 7 0x33f1d4 0x33f1c8
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:advapi:LsaOpenPolicy ((null),0x84e3ac,0x00000001,0x84e3c8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"http://tools.google.com/service/update2", 0x84e360, 0x84e378
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"https://tools.google.com/service/update2", 0x84e360, 0x84e378
fixme:mstask:MSTASK_ITaskScheduler_Activate Partial stub always returning COR_E_FILENOTFOUND
fixme:mstask:MSTASK_ITaskScheduler_Activate Partial stub always returning COR_E_FILENOTFOUND
fixme:mstask:MSTASK_ITask_SetFlags (0x137528, 0x00002000): stub
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:advapi:LsaOpenPolicy ((null),0x84e32c,0x00000001,0x84e348) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"http://tools.google.com/service/update2", 0x84e2e0, 0x84e2f8
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"https://tools.google.com/service/update2", 0x84e2e0, 0x84e2f8
fixme:mstask:MSTASK_ITaskScheduler_Activate Partial stub always returning COR_E_FILENOTFOUND
fixme:mstask:MSTASK_ITaskScheduler_Delete 0x1372f8, L"GoogleUpdateTaskUser": stub
fixme:mstask:MSTASK_ITaskScheduler_Activate Partial stub always returning COR_E_FILENOTFOUND
fixme:mstask:MSTASK_ITaskScheduler_Delete 0x199c50, L"GoogleUpdateTaskUserS-1-5-4": stub
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:advapi:LsaOpenPolicy ((null),0x84e3bc,0x00000001,0x84e3d8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
pag@pag-laptop:~/Desktop$ fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:advapi:LsaOpenPolicy ((null),0x33f0c4,0x00000001,0x33f0e0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 7 0x33f27c 0x33f270
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 7 0x33f1d4 0x33f1c8
fixme:advapi:LsaOpenPolicy ((null),0x33ef74,0x00000001,0x33ef90) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0x33ef6c,0x00000001,0x33ef88) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0x33ef64,0x00000001,0x33ef80) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"http://tools.google.com/service/update2", 0x84e370, 0x84e388
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"https://tools.google.com/service/update2", 0x84e370, 0x84e388
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:advapi:LsaOpenPolicy ((null),0x84e614,0x00000001,0x84e630) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"https://tools.google.com/service/update2", 0x84e638, 0x84e650
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"https://tools.google.com/service/update2", 0x84e638, 0x84e650
fixme:advapi:RegisterEventSourceW ((null),L"Google Update"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x00000014,0x13f8b8,0x0001,0x00000000,0x84e8c8,0x13f568): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:advapi:LsaOpenPolicy ((null),0x84e58c,0x00000001,0x84e5a8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:msxml:domdoc_createNode nodes with namespaces currently not supported.
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"http://tools.google.com/service/update2", 0x84e540, 0x84e558
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetProxyForUrl 0x1, L"https://tools.google.com/service/update2", 0x84e540, 0x84e558
fixme:advapi:LsaOpenPolicy ((null),0x33eee4,0x00000001,0x33ef00) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:process:SetProcessShutdownParameters (00000280, 00000001): partial stub.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:mstask:MSTASK_ITaskScheduler_Activate Partial stub always returning COR_E_FILENOTFOUND
fixme:mstask:MSTASK_ITaskScheduler_Delete 0x142608, L"GoogleUpdateTaskUserS-1-5-4Core": stub
fixme:mstask:MSTASK_ITaskScheduler_Activate Partial stub always returning COR_E_FILENOTFOUND
fixme:mstask:MSTASK_ITaskScheduler_Delete 0x142608, L"GoogleUpdateTaskUserS-1-5-4UA": stub
fixme:mstask:MSTASK_ITaskScheduler_Enum 0x142608, 0x33f140: stub
fixme:mstask:MSTASK_ITaskScheduler_Enum 0x142608, 0x33f140: stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
```And when I open Internet Explorer I get this error:

> Cannot find 'http://go.microsoft.com/fwlink/?LinkId=74005. Make sure the path or Internet address is correct.

---

### Post by joelstitch on 2011-05-01
Still no luck :(

---

### Post by joelstitch on 2011-05-03
So another program that Im trying to use is Tether. When I open it with wine on the Terminal I get this:

> fixme:ntdll:NtLockFile I/O completion on lock not implemented yet

---

### Post by clhsharky on 2011-05-03
joelstitch


Have you searched to see if you apps are supported by Wine.

WineHQ are the developers of wine not Ubuntu, thats where I look for solutions.

WineHQ
[http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.winehq.org%2F&rct=j&q=wine%20hq&ei=ZS3ATdsLyonRAfK57JwF&usg=AFQjCNG_GieVLJmWMq2dtLWRMyBttJA2Xw&sig2=8YVnOaeOHFMrZzawPMRngg&cad=rja](http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.winehq.org%2F&rct=j&q=wine%20hq&ei=ZS3ATdsLyonRAfK57JwF&usg=AFQjCNG_GieVLJmWMq2dtLWRMyBttJA2Xw&sig2=8YVnOaeOHFMrZzawPMRngg&cad=rja)

App DataBase
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

Also look in Wine sub-forum for Ubuntu users.
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)



Sharky

---

### Post by joelstitch on 2011-05-03
With Tether there's nothing on it. I was able to install it with no problems, the problem is that wine apps cant access the Internet.

---

### Post by joelstitch on 2011-05-03
I just installed Firefox trough wine and is working fine. So I guess it could be that Tether is not supported...

How would I go about fixing the error:

> fixme:ntdll:NtLockFile I/O completion on lock not implemented yet 			 		??

---


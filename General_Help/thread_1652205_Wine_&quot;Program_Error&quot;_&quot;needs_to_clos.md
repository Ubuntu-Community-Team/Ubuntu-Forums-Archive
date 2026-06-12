---
title: "Wine: &quot;Program Error&quot; &quot;needs to close&quot; but stays open"
date: 2010-12-24
forum: General Help
---

### Post by physic.dude on 2010-12-24
I am successfully able to run Photoshop CS5 through Wine but every time I start up Photoshop I get Wine's error that says that the program has an error and needs to close. however, Photoshop doesn't close and seems to run just fine after I close the 'program error message.' In fact I cropped the attached picture in that same Photoshop session. 

Anyway, is there a way to disable the message from showing up, or is it trying to tell me something. In advance, thanks.

---

### Post by jwbrase on 2010-12-24
> **physic.dude said:**
> I am successfully able to run Photoshop CS5 through Wine but every time I start up Photoshop I get Wine's error that says that the program has an error and needs to close. however, Photoshop doesn't close and seems to run just fine after I close the 'program error message.' In fact I cropped the attached picture in that same Photoshop session. 

Anyway, is there a way to disable the message from showing up, or is it trying to tell me something. In advance, thanks.

You could see what appdb.winehq.org says about it. Wine doesn't run every Windows program perfectly, so it's likely that it really is running into some problem.

---

### Post by physic.dude on 2010-12-24
I cant find anything relevant to my problem, I just tested many features of Photoshop and they all worked with flying colors (pun intended), from text to HDR toning. Is there a way I can disable the Message permanently?

---

### Post by physic.dude on 2010-12-24
If it helps, here is the last line that is returned before I close the 'Program Error' message when Photoshop is run through terminal.

```
wine: Unhandled page fault on write access to 0x00000014 at address 0x57c6348 (thread 002e), starting debugger...
```

---

### Post by physic.dude on 2010-12-25
bump

---

### Post by sjwaldron on 2011-04-10
Sorry to bring up this old thread, but I'm having the same issue.  Did you ever figure out how to fix it?

How things went down:
I installed the CS5 trial download (the only trial available is the Extended version) on a Vista virtual machine.  I take that and copy it over to my WINE install on Ubuntu 10.10 and it works well.  I input my serial number and the program down-converts to CS5 Standard.  Every time I start the program up I get that WINE error, but after that it functions fine.

```

err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
wine: Unhandled page fault on write access to 0x00000014 at address 0x59e6348 (thread 0087), starting debugger...
Unhandled exception: page fault on write access to 0x00000014 in 32-bit code (0x059e6348).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:059e6348 ESP:068fe898 EBP:068fe8f8 EFLAGS:00010202(  R- --  I   - - - )
 EAX:0000d0b2 EBX:f64faff4 ECX:84e061c4 EDX:00000003
 ESI:00000000 EDI:00200000
Stack dump:
0x068fe898:  00000003 00000000 ffffffff 00000000
0x068fe8a8:  0bbd0120 f64f2136 00000003 00000000
0x068fe8b8:  00200000 068fe95c 00000008 10000000
0x068fe8c8:  00000001 f64f7f34 068fe95c f64f7efa
0x068fe8d8:  068fe95c 00411400 068fe95c 7fffffff
0x068fe8e8:  f64efddd f64faff4 00000000 00000000
Backtrace:
=>0 0x059e6348 in amtservices (+0xa6348) (0x068fe8f8)
  1 0xf64f0d09 in winhttp (+0x10d08) (0x068fe9a8)
  2 0xf64f19ae in winhttp (+0x119ad) (0x068fe9d8)
  3 0xf64eca20 in winhttp (+0xca1f) (0x068fe9f8)
  4 0x7bc7bcf7 in ntdll (+0x6bcf6) (0x068fea68)
  5 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x068fea78)
  6 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x068feb48)
  7 0x7bc79ce5 in ntdll (+0x69ce4) (0x068ff398)
  8 0xf75f1cb2 start_thread+0xd1() in libpthread.so.0 (0x068ff498)
0x059e6348: movw	%ax,0x14(%esi)
Modules:
Module	Address			Debug info	Name (227 modules)
..........removed section here that was long.............
Backtrace:
=>0 0x059e6348 in amtservices (+0xa6348) (0x068fe8f8)
  1 0xf64f0d09 in winhttp (+0x10d08) (0x068fe9a8)
  2 0xf64f19ae in winhttp (+0x119ad) (0x068fe9d8)
  3 0xf64eca20 in winhttp (+0xca1f) (0x068fe9f8)
  4 0x7bc7bcf7 in ntdll (+0x6bcf6) (0x068fea68)
  5 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x068fea78)
  6 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x068feb48)
  7 0x7bc79ce5 in ntdll (+0x69ce4) (0x068ff398)
  8 0xf75f1cb2 start_thread+0xd1() in libpthread.so.0 (0x068ff498)
fixme:win:LockWindowUpdate (0x209d6), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fda54,0x00000001,0x222fda70) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fda54,0x00000001,0x222fda70) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} not registered
err:ole:CoGetClassObject no class object {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} could be created for context 0x1
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fe52c,0x00000001,0x222fe548) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fe52c,0x00000001,0x222fe548) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} not registered
err:ole:CoGetClassObject no class object {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} could be created for context 0x1
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\scott\\Temp\\swtag.log" 1 -2147483644 0xbb8bb6c 0xbb8bb78 0xbb8bc40 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0xbb8bb6c 0xbb8bb78 0xbb8bc40 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\scott\\Temp\\swtag.log" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)

```

---

### Post by physic.dude on 2011-04-13
> **sjwaldron said:**
> Sorry to bring up this old thread, but I'm having the same issue.  Did you ever figure out how to fix it?

How things went down:
I installed the CS5 trial download (the only trial available is the Extended version) on a Vista virtual machine.  I take that and copy it over to my WINE install on Ubuntu 10.10 and it works well.  I input my serial number and the program down-converts to CS5 Standard.  Every time I start the program up I get that WINE error, but after that it functions fine.

```

err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
wine: Unhandled page fault on write access to 0x00000014 at address 0x59e6348 (thread 0087), starting debugger...
Unhandled exception: page fault on write access to 0x00000014 in 32-bit code (0x059e6348).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:059e6348 ESP:068fe898 EBP:068fe8f8 EFLAGS:00010202(  R- --  I   - - - )
 EAX:0000d0b2 EBX:f64faff4 ECX:84e061c4 EDX:00000003
 ESI:00000000 EDI:00200000
Stack dump:
0x068fe898:  00000003 00000000 ffffffff 00000000
0x068fe8a8:  0bbd0120 f64f2136 00000003 00000000
0x068fe8b8:  00200000 068fe95c 00000008 10000000
0x068fe8c8:  00000001 f64f7f34 068fe95c f64f7efa
0x068fe8d8:  068fe95c 00411400 068fe95c 7fffffff
0x068fe8e8:  f64efddd f64faff4 00000000 00000000
Backtrace:
=>0 0x059e6348 in amtservices (+0xa6348) (0x068fe8f8)
  1 0xf64f0d09 in winhttp (+0x10d08) (0x068fe9a8)
  2 0xf64f19ae in winhttp (+0x119ad) (0x068fe9d8)
  3 0xf64eca20 in winhttp (+0xca1f) (0x068fe9f8)
  4 0x7bc7bcf7 in ntdll (+0x6bcf6) (0x068fea68)
  5 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x068fea78)
  6 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x068feb48)
  7 0x7bc79ce5 in ntdll (+0x69ce4) (0x068ff398)
  8 0xf75f1cb2 start_thread+0xd1() in libpthread.so.0 (0x068ff498)
0x059e6348: movw    %ax,0x14(%esi)
Modules:
Module    Address            Debug info    Name (227 modules)
..........removed section here that was long.............
Backtrace:
=>0 0x059e6348 in amtservices (+0xa6348) (0x068fe8f8)
  1 0xf64f0d09 in winhttp (+0x10d08) (0x068fe9a8)
  2 0xf64f19ae in winhttp (+0x119ad) (0x068fe9d8)
  3 0xf64eca20 in winhttp (+0xca1f) (0x068fe9f8)
  4 0x7bc7bcf7 in ntdll (+0x6bcf6) (0x068fea68)
  5 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x068fea78)
  6 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x068feb48)
  7 0x7bc79ce5 in ntdll (+0x69ce4) (0x068ff398)
  8 0xf75f1cb2 start_thread+0xd1() in libpthread.so.0 (0x068ff498)
fixme:win:LockWindowUpdate (0x209d6), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fda54,0x00000001,0x222fda70) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fda54,0x00000001,0x222fda70) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} not registered
err:ole:CoGetClassObject no class object {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} could be created for context 0x1
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fe52c,0x00000001,0x222fe548) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x222fe52c,0x00000001,0x222fe548) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} not registered
err:ole:CoGetClassObject no class object {0f87369f-a4e5-4cfc-bd3e-73e6154572dd} could be created for context 0x1
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\scott\\Temp\\swtag.log" 1 -2147483644 0xbb8bb6c 0xbb8bb78 0xbb8bc40 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0xbb8bb6c 0xbb8bb78 0xbb8bc40 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\scott\\Temp\\swtag.log" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0xbbd0d84 0xbbd0d90 0xbb8ba00 (nil)

```


No, I never bothered to find a solution, I just use Photoshop with windows in a virtual box now.

---


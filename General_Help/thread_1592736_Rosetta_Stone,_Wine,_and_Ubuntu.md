---
title: "Rosetta Stone, Wine, and Ubuntu"
date: 2010-10-10
forum: General Help
---

### Post by GeneralRitz on 2010-10-10
I am running Ubuntu 10.04 and WINE 1.2.

WineHQ APPDB states that Rosetta Stone is not installable.

I have installed it, so the information there is not correct/complete.

When I installed, it ran perfectly.  I created an ISO of the install disc and the first lesson.  I then loop mounted each of them in turn for them to run and assigned each of them a windows directory, configuring them as CD-ROM.  This worked perfectly the first day.  Now it no longer works with the ISO or with the original disc.

I have run the program in terminal and received the following output:

> err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Macrovision Shared\\FLEXnet Publisher\\\\fnp_registrations.xml" 1 4 (nil) (nil) 0x97f6350 (nil)
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x196ce8, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xa6be974)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c10
fixme:wbemprox:wbem_locator_ConnectServer 0x196cc8, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xa3be9a4)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data/FLEXnet" 1 1 0x4aeea8 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data/FLEXnet" 1 4 (nil) (nil) 0x4b2c28 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data/FLEXnet\\rosetta_003da900_tsf.data" 1 1 0x4a8800 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data/FLEXnet\\rosetta_003da900_event.log" 1 1 0x4a8800 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\All Users\\Application Data/FLEXnet" 1 4 (nil) (nil) 0x4b2c90 (nil)
wine: cannot find L"C:\\windows\\system32\\taskkill.exe"


C:\Program Files\Rosetta Stone\Rosetta Stone V3\support\bin\win\\RosettaStoneLtdServices.exe [v082920071939] 

AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
AUDIO ERROR
...using WAVE_MAPPER
AUDIO ERROR
AUDIO ERROR
wine client error:30: pipe: Too many open files
err:winediag:FILE_CreateFile Too many open files, ulimit -n probably needs to be increased
err:wave:wodOpen Error open: Input/output error
err:wave:wodOpen Error open: Input/output error
err:wave:wodOpen Error open: Input/output error
fixme:crypt:SystemFunction036 couldn't open /dev/urandom
err:mmtime:TIME_MMTimeStop Timer still active?!

I have seen similar outputs on the forums, but nothing that included that AUDIO ERROR.  This seems to be an issue of time.  If I don't do anything, the program will crash giving me error 5118.  If I run through lesson select and mic testing quickly then I can get all the way to the lesson before it crashes with the same error.  Any suggestions?

---

### Post by Neonfly on 2010-10-13
I also have this AUDIO ERROR problem. In my case it doesn't crash and I also don't receive any error-numbers but I also have no sound. Which sound server do you use (ALSA, Pulseaudio, OSS)?

Because of the crash. Did you try to start up the program from the working directory?

---

### Post by GeneralRitz on 2010-10-13
I am using ALSA.  And yes, I did start it in the working directory.

---


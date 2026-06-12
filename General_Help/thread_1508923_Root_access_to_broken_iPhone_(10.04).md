---
title: "Root access to broken iPhone (10.04)"
date: 2010-06-13
forum: General Help
---

### Post by nathan28 on 2010-06-13
So my wife dropped her iPhone a few days ago. The glass broke and the screen is borked. AFAIK otherwise the thing is okay--it rang (until she got a replacement), I can browse it in windblows and ubuntu, etc.

But the contacts are locked outside of the sandboxed part of the file system, and we never jailbroke the phone. Since the screen has two new features--all white and all black--I don't think it's possible to jailbreak it. Every windblows jailbreak looks like I need to at least see the screen.

As far as I can tell from the internet, if I don't jailbreak the phone--and right now, I don't think that's possible--I can't get past the AFC crap.

> name@computername:/media$ ifuse /media/iPhone/ --root
Failed to start AFC service 'com.apple.afc2' on the device.
This service enables access to the root filesystem of your device.
Your device needs to be jailbroken and have this service installed.
Note that PwnageTool installs it while blackra1n does not.


Is there a workaround to get to the f-cking root directory on this Apple monstrosity? Would I be able to get root access via an OS X terminal?

I have xpwn binaries untarred, but really don't know what to do from there or if xpwn can help me.

> name@computername:~/testingdir/xpwn/XPwn-0.5.7-Linux$ ls
bundles   dmg              hdutil   ipsw         ramdisk.dmg  xpwn
dfu-util  FirmwareBundles  hfsplus  LICENSE.txt  README.txt   xpwntool



On edit, this looks hopeless w/out a hardware repair. Well, I have an excuse to buy a dremel now. PlexiPhone 3G FTW.

---

### Post by jacoody on 2010-06-17
I don't think you need to see the screen to jailbreak the iPhone.  I jailbroke mine using redsn0w in Windows and a custom ipsw file for 3.1.2.  The iPhone I have is a 3G on firmware 3.1.2, although I jailbroke it at 3.1.0.  If you upgraded it to 3.1.2 or 3.1.3 pre-jailbreak you may have issues as I don't recall exactly how blackra1n starts up.

Basically you open redsn0w, point it to the custom ipsw file and follow the directions on your computer monitor.  You have to hold down the power button for so many seconds, continue with it and hold down the home button for so many seconds, then the computer does the rest.  What you won't be able to do without a screen is probably install openssh from Cydia which will allow you to ssh into the phone.  You can probably get around that by installing ifuse and mounting it in linux though as it will give you root access to your phone directory.

If you are on the right version (plug it into iTunes to see and DON'T update it) and need to download the ipsw file you will need the torrent called iPhone1,2_3.1.2_7D11_Custom_Restore_NO_ACTIVATION.ipsw .  Make sure you get the NO ACTIVATION file since you are on AT&Ts network (assumption since you haven't jailbroken it yet in order to unlock it).

Hope this helps

---

### Post by CuteLinux on 2010-06-20
To get root Access on iDevice you need a jailbroken iPhone and a running AFC Service.

> 
name@computername:/media$ ifuse /media/iPhone/ --root
Failed to start  AFC service 'com.apple.afc2' on the device.
This service enables  access to the root filesystem of your device.
Your device needs to be  jailbroken and have this service installed.
Note that PwnageTool  installs it while blackra1n does not.
To solve this Problem you need to install AFC through Cydia:

The Output After installing AFC Service: 

> 
cutelinux@MacOS:/mnt$ ifuse --root /mnt/iPh0ne/
cutelinux@MacOS:~$ cd /mnt/iPh0ne/
cutelinux@MacOS:~$iPhone> ls
Applications  boot   dev        etc  Library  private  System  User  var
bin           cores  Developer  lib  mnt      sbin     tmp     usr
 Done  ;)

CuteLinux

---


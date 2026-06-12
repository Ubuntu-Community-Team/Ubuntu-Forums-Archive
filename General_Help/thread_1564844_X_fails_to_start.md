---
title: "X fails to start"
date: 2010-08-31
forum: General Help
---

### Post by Subito Piano on 2010-08-31
Hi all - this one really has me going....

I'm using Ubuntu Studio 10.04 (64-bit) loaded onto sda3, formatted to ext4.   It's a Toshiba laptop, AMD Turion and ATI radeon, which appears to be troublesome for some.  All was fine for months; I am not sure that I did anything unusual, i MIGHT have upgraded, idk, but i cannot get the X server to work (no gui, just commandline). At the prompt i type "startx" and receive the following:[INDENT]The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                        Ignoring extra symbols
Errors from xkbcomp are not fatal to the x server
(EE) AlpsPS/2 ALPS GLidePoint Unable to query/initialize Synaptics hardare.
(EE) PreInit failed for input device "AlpsPS/2 ALPS GlidePoint"

waiting for X server to shuw down Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Enable CRTC 1 success
Unblank CRTC 0 success
error setting MTRR (base = 0xf0000000, size = 0x00000000, type = 1) Inappropriate ioctl for device (25)
  ddxSigGiveUp: closing log
Disable CRTC 1 success
Enable CRTC 0 success
[/INDENT]The synaptics error is due to a faulty touchpad but that never was a problem before; nevertheless i removed the reference to it in my xorg.conf file.  Strange, the xorg.conf file was missing --  ?!?!?  so i booted up a copy of Ubuntu Live 8.04 i had on hand and copied the resulting xorg.conf file from there to /etc/X11 (in sda3). Removing those lines removed that error message but didn't help me get gdm.

I fixed the <RALT> error according to [this post]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/433926"), again it removed those particular error lines but still no X.  I also tried to remove /lib/tls/i686/cmov/libc.so.6 as per [this post]("https://bugs.launchpad.net/ubuntu/lucid/+source/eglibc/+bug/542357") (using my Knoppix disk -- sorry, i'm weak on commandline) -- but then Knoppix would act up and not shut down properly, thus the file stayed intact.  I have my doubts that would fix it, anyway. 

Finally, i tried to overwrite my mtrr files manually as suggested [here]("http://ubuntuforums.org/showthread.php?t=115104"), but when i issued the command[INDENT]echo "disable=0" >| /proc/mtrr
[/INDENT]the laptop would spew out lines of code and just stop cold.  ](*,)  At any rate, the memory IS reporting correctly; i have 2 gigs.

Yowsers!  This is a royal pain!  I'm using Puppy 4.2 to run this thing for the moment so i can't even access my files (Puppy didn't start reading ext4 til version 4.3) -- kind of a bad situation since i just started in as principal and my files are so inaccessible.....silly me, i got so excited when i tried out a Ubuntu Studio install that i never reinstalled with a separate home partition!!!  #-o

I'd obviously NOT rather copy all my files and reinstall and recustomize....any ideas???

---


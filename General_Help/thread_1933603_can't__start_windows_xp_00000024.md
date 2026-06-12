---
title: "can't  start windows xp 00000024"
date: 2012-02-29
forum: General Help
---

### Post by David728 on 2012-02-29
I can't start my Dell windows xp laptop with sp3 from 2004 with. I am getting the stop 0x000000024 and 0x00190203. When I ran diagnostics, I got the DST short test, error detected, test result failed, error code 1000-0146, MSG unit 2 DST, contain previous error. 

Someone suggested I use Linus or Ubuntu to boot into the computer and backup and copy the files in the computer before running the recovery console. The windows xp cd only has the sp1. Where can I download the xp cd with sp3?

Can someone explain how to do it or suggest a link to a tutorial that show how to fix the problem.

Should I use another computer to download Linus or Ubuntu onto a usb stick and the recovery console software for windows xp with sp3? After copying the files from the bad computer into a usb stick, should I install linux or ubuntu into the bad computer? Thank you.

---

### Post by QIII on 2012-02-29
Short of bold-faced piracy, you can't just download an XP SP3 disk.  You would have to re-install from your licensed media and hope that Micosoft still supports upgrading to a newer service pack.

As for your files ...

Beg, borrow or download a copy of the Ubuntu LiveCD on another computer.  That is free.  Burn it to a disk -- as an image.  Set your BIOS to boot from CD and start a Live session.  From there, you can navigate to your Windows disk and find the files you care to back up.  You will need to have some attached medium large enough to hold all the files.  A beefy USB stick or even an external drive.  Copy your files to secure them.  Reinstall Windows and hope Microsoft Update gives you the option to update to SP3.

---

### Post by matt_symes on 2012-02-29
Hi

DST failed ? Sounds like your hard drive has had it. I take it your drive does not have SMART ? If not, it may be an older drive.

You may have problems getting your files from that drive. Do you have a backup of your drive ?

Kind regards

---

### Post by QIII on 2012-02-29
With that error code he may be able to use System File Checker and scannow 

```
sfc /scannow
```

(... I think that's it.)

Haven't owned a Dell myself, but we use them at work.

---

### Post by matt_symes on 2012-02-29
Hi

The hard drive has had a Drive Self Test failure. 

QII is correct. It's worth trying both sfc /scandisk (system file check) and a scan disk.

Can i recommend something before that though ? Back up your drive using ddrecue or clonezilla or some such. 

Kind regards

---


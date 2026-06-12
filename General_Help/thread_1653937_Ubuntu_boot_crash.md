---
title: "Ubuntu boot crash"
date: 2010-12-27
forum: General Help
---

### Post by Frobozz23 on 2010-12-27
Hi Ubuntu gurus,

First a quick background on my Ubuntu expertise, or lack thereof.  I'm a professional software engineer, and I've used linux/unix for 15+ years.  But I'm very new to Ubuntu.  My brother installed Ubuntu on my mom's Lenovo G555 laptop as a dual-boot with Windows 7 Professional.  (It's the install that has Ubuntu sharing the same partition as Windows 7)  My mom has been using Ubuntu for about 3 months now, and likes it.

Today, I was helping her debug a printing problem with OpenOffice.  While working on this, I saw an update prompt for a variety of Ubuntu applications, and likely the OS itself.  I allowed it to update everything.  I then booted into Windows7, which we had not done in quite a while, because I wanted to test printing the same document on Windows to see if the problem was specific to the Ubuntu print drivers, or to OpenOffice.  While I was in Windows7, I rebooted the system, and it installed 25 system updates without warning (I have since turned off automatic updates.)  Now, when I try to boot into Ubuntu, it crashes immediately (within one second) and reboots to the boot selection prompt.  The only message I see on the screen, for a fraction of a second, is:

Try hd(0,0): NTFS5: No wubildr

Unfortunately, I don't know what version of Ubuntu was installed, but I do know the laptop was purchased in September, and the Ubuntu install was downloaded at that time.  I have the install disc around here somewhere.

For what it's worth, I do see the file C:/ubuntu/winboot/wubildr when I boot in Windows 7.  And the Windows7 OS is working fine.

Any advice on how to diagnose this problem, and what could be wrong?

Thanks,
Frobozz

---

### Post by wojox on 2010-12-27
I don't use wubi but you can checkout [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"). That should head you in the right direction.

---

### Post by Frobozz23 on 2010-12-27
Thanks wojox.  I've made some progress.

First, I'm seeing other users with the same symptoms.

I found my boot disk.  The original install was Ubuntu 10.04.1.  I don't think this install was upgraded to 10.10.  (How do I check while running from the LiveCD?)

The [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") describes a boot failure that sounds similar to what I'm experiencing.  It says:

"If it is a 10.04 install, the fix is to boot an Ubuntu LiveCD/USB, loop  mount the wubi root.disk and manually edit the grub.cfg file."

How do I "loop mount the wbui root.disk?"

I also found this disheartening information:

[http://askubuntu.com/questions/18125/wubi-installation-broken-by-update-now-unable-to-mount](http://askubuntu.com/questions/18125/wubi-installation-broken-by-update-now-unable-to-mount)

TIA,
Frobozz

---

### Post by drs305 on 2010-12-27
> **Frobozz23 said:**
> 
"If it is a 10.04 install, the fix is to boot an Ubuntu LiveCD/USB, loop  mount the wubi root.disk and manually edit the grub.cfg file."

How do I "loop mount the wbui root.disk?"


The instructions on 'loop' mounting are contained within the first post of the megathread. Find the section with the command:
```

sudo mount -o loop / ......

```

That is the section he is referring to.

---

### Post by Frobozz23 on 2010-12-28
The problem is fixed.  It was a bad grub.cfg file caused by the latest update, as mentioned in the Wubi megathread.  Thanks to the Ubuntu community for help solving this.

---

### Post by Rubi1200 on 2010-12-28
On behalf of the Ubuntu community, you are more than welcome :)

Please mark this Solved using the Thread Tools near the top of the page.

---

### Post by Wordhammer on 2010-12-28
Hi, I've been searching the forums for a solution to my current problem and this is closest to what I am facing.
I'm using wubi; Windoze vi$ta boots.
Selecting Ubuntu in the boot menu reboots: The pause button will not work, and I don't know what it is telling me, I assume that the error message is the same as frobozz23's.

His solution:
```
 It was a bad grub.cfg file caused by the latest update
```

My problem is that there is nothing in my GRUB folder, it is empty. There is a file called wubildr.cfg, but the GRUB directory is empty - totally.

I'm currently stuck in doze, I don't like the vi$ta environment. I have a lili key booted up but I would rather work on MY home copy of [x][k]ubuntu. After getting it all set up with all three environments and all the drivers working, I would like to get back to it.

I was wondering how to fix the bad grub.cfg file if it is not there?

---

### Post by Rubi1200 on 2010-12-28
Wordhammer,
it would be best if you booted the computer with either a LiveCD or LiveUSB, choosing to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here please.

---

### Post by Wordhammer on 2010-12-28
Thank you for your quick reply Rubi1200,

This message would have been done sooner, but I had to learn (in the problem solving nerdy fashion) that d0z3 vi$ta will not support persistence.
```
save to key
reboot
not on key
reboot
boot vmachine
download script
reboot vmachine
NO PERSISTANCE
look up LiLi - yup, m$ still sux
Download to /ubuntu
reboot
load key
move to key
run - Success!
```

There is a cool shell command that right click root runs that script.
I'm impressed.

---

### Post by Rubi1200 on 2010-12-28
Have you tried the solutions in the Wubi Megathread?

I would give either problem #2, solution #1 or #2 a try and see if it gets you back into Ubuntu.

Let us know how it goes.

---

### Post by Wordhammer on 2010-12-28
Problem #2 - Solution #2 worked like a charm. Thank you rubi1200.

---

### Post by Rubi1200 on 2010-12-29
> **Wordhammer said:**
> Problem #2 - Solution #2 worked like a charm. Thank you rubi1200.
No problem, you are more than welcome :-)

---


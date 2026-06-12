---
title: "Ubuntu 10.04 Freezes sometimes when I boot up!"
date: 2010-04-30
forum: General Help
---

### Post by TheNerdAL on 2010-04-30
I have been posting some threads about this but they don't help much. 

So I boot up my computer and sometimes it freezes with a white underscore on a black screen and my Caps Lock and Scroll Lock blink. 

Sometimes it doesn't freeze but just the underscore starts blinking. What could be the problem?

Thanks.

---

### Post by TheNerdAL on 2010-05-01
*bump*

---

### Post by TheNerdAL on 2010-05-02
This is why I went back to Ubuntu 9.10, can anyone fix this? :(

---

### Post by TheNerdAL on 2010-05-06
Will this help? 

> **philinux said:**
> 
...Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` and add this option FRAMEBUFFER=y, save the file.
Then
```
sudo update-initramfs -u

```Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

If the problem is a slow boot, and you have no floppy drive, disable the floppy in the bios. This has been reported as a fix to this. [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712)

If the problem is plymouth not displaying, and a black screen from grub to gdm, this could be due to graphics drivers needing to be loaded quicker. This is bugged.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787)...



---

### Post by Nizarus on 2010-05-07
I have the same problem on my dell E521 with an ATI graphical card. I noted that the freeze happened when switching to polymouth.

---

### Post by Xianath on 2010-05-10
Can't help with a solution I'm afraid but the slowly blinking LEDs indicate a kernel panic. You may try _[raising elephants]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device")_ to at least reboot cleanly. Other than that, sounds like an issue with hardware, most likely video as other posters suggested.

---

### Post by alejandro.mc on 2010-05-18
My pc freezes for about 9 seconds when the desktop is loaded, nothing works during those 9 seconds.. after them all the things you pressed during that time get activated..

Is it the same problem?

Any solutions yet?

Thanks!

Alejandro

SOLVED FOR ME: Disabled the Floppy from BIOS (I have no floppy drive and apparently that created a conflict..strange..)

---

### Post by the hoplite on 2010-06-29
Yeah, this sure is a big problem, I installed 10.04 in THREE different pcs (laptops Acer and Samsung and a fixed PC with amd64 and nvidia graphics) and they ALL got the same problem. Randomly, one time out of ten-fifteen it freezes at the end of the boot process, just before the desktop should appear. 
It's a bit of a problem. Any ideas?

---

### Post by kingoftown on 2010-06-29
i really need help anyone ](*,)

---

### Post by ytzml on 2010-07-25
Well, same issue as in this thread:

[http://ubuntuforums.org/showthread.php?t=1474444](http://ubuntuforums.org/showthread.php?t=1474444)

Also without solution so far.

---

### Post by the hoplite on 2010-07-25
Hadn't had that issue for quite some time now, I think a kernel update solved the problem (on all the three pcs).

---

### Post by linux18 on 2010-07-25
> **ytzml said:**
> Well, same issue as in this thread:

[http://ubuntuforums.org/showthread.php?t=1474444](http://ubuntuforums.org/showthread.php?t=1474444)

Also without solution so far.
SOLUTION!!!
I have had this problem once in 9.04 and several times in 10.04 however, I have found a workaround:
```
 
-choose recovery mode at grub
-drop to a root prompt
-type " telinit 3" and login
-then type " xinit "
-when xinit starts type: " metacity & " - for ubuntu OR " compiz & " - if you have it OR flux/openbox & - if you have it OR " fvwm & " - for xubuntu
-then type " gnome-panel & " -for ubuntu OR " xfce4-panel & " -for xubuntu
-lastly type " nm-applet & " -for networking

```
once you do this, the next few boots are almost guaranteed to work properly and I haven't had any problems since I used the workaround

---


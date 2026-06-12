---
title: "latest updates borked it for me"
date: 2010-08-17
forum: General Help
---

### Post by ELD on 2010-08-17
Basically i installed all updates today, rebooted and not it won't even get to the login screen.

Sometimes i get a black screen, sometimes the ubuntu logo.

Anyone else getting the same?

---

### Post by sydbat on 2010-08-17
> **ELD said:**
> Basically i installed all updates today, rebooted and not it won't even get to the login screen.

Sometimes i get a black screen, sometimes the ubuntu logo.

Anyone else getting the same?Nope.

Have you gone into the recovery area and done the "fixes" (dpkg, fix-X)?

---

### Post by ELD on 2010-08-17
> **sydbat said:**
> Nope.

Have you gone into the recovery area and done the "fixes" (dpkg, fix-X)?

How do i do these fixes? Never had this problem before heh.

---

### Post by sydbat on 2010-08-17
> **ELD said:**
> How do i do these fixes? Never had this problem before heh.Fired. :p

At the grub screen there is the current kernel boot option, followed by the current recovery kernel option. Loading the recovery kernel pulls up a menu with "fixing" options (it has been awhile since I have had to use this, so I am not 100% sure what they are called).

If grub does not show up during boot, I think you hit 'Esc' or 'Ctrl' to bring it up.

---

### Post by ELD on 2010-08-17
Rightyo will give it a go.

---

### Post by alphaamanitin on 2010-08-17
I have had a problem that gave similar results.  I will briefly describe:  Did some updates, reboot get to grub, goes normally, gets to ubuntu logo, permanent black screen.  Sound familiar?  

If so here was my solution:

For whatever reason grub stopped using UUID to find the device to boot from and started using /dev/sdc1.  I solved this by hitting 'e' in grub, editing the device location to what I was pretty sure it should be. It was '/dev/sdb1' fro me because I was booting from an external hard drive.  If you are booting from an internal HD it is probably '/dev/sda1' or '/dev/sda0.'  Anyway, after I did that I hit tab to save changes and I think it is ctrl-x to boot.  I booted fine.  Next open a terminal and run sudo update-grub and the problem was completely fixed.  

Hope it helps.

AlphaA

---

### Post by ulfj on 2010-08-17
Nope, but a couple of updates ago seemed to break my flash, can't get full screen to work, will figure it out though.

---

### Post by espressobeanie on 2010-08-17
Yes, this happened to me too. I tried to boot in recovery and it couldn't get past the scripts part stating "/sbin/initd scripts not found. I can't boot into a tty at all. The keyboard is disabled once you boot normally because the LED lights flash continuously. I didn't add any new hardware, I just updated language-en, x-server-org, and some other stuff. This blows.

---

### Post by zeropointer on 2010-08-17
I had the same problem. After an update it wouldn't boot up. Went to blank screen, no start up sounds.
Trying to find solutions, I ran across this site:
[http://www.lockergnome.com/linux/2007/09/22/ubuntu-black-screen-recovery/](http://www.lockergnome.com/linux/2007/09/22/ubuntu-black-screen-recovery/)
[http://www.lockergnome.com/linux/2007/07/19/kernel-update-breaks-ubuntu/](http://www.lockergnome.com/linux/2007/07/19/kernel-update-breaks-ubuntu/)

Which got me thinking about Kernels.

I booted up with Livecd, went to my /boot directory on my harddrive.
I noticed I had files like:[INDENT] vmlinuz-2.6.32-24-generic 
initrd.img-2.6.32-24-generic
[/INDENT]However when I edited my Grub2 (hold shift while booting or press key and then 'e')
I noticed mine read:[INDENT] vmlinuz-2.6.32-2**1**-generic 
initrd.img-2.6.32-2**1**-generic
[/INDENT]Very old Kernels.
So, I edited them to [INDENT] vmlinuz-2.6.32-2**4**-generic 
initrd.img-2.6.32-2**4**-generic
[/INDENT]The latest ones I had in my /boot directory and booted Ctrl-X
And this worked for me.

I hope this works for others.
I think for some reason, this latest update has messed up Grub2 files.

---

### Post by CoolJohnB on 2010-08-17
I haven't had the problems mentioned above, but when I boot the screen flashes a few times then everything works normally.  Also writing this I notice everything is underlined in red as though it is all misspelled!

Anyone any ideas?

---


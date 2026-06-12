---
title: "Can't repair grub after installing Windows 7"
date: 2009-11-04
forum: General Help
---

### Post by koskoz on 2009-11-04
Hi everyone, 
I installed Windows 7 today and everythings ran fine.
When I restarted I knew grub would be missing, so I booted on an ubuntu live cd to repair it, and I did as always :

grub
find /boot/grub/stage1 => error 15
root (hd0,2) (I know the numbers even if find doesn't work)
setup (hd0) => error 17

My ubuntu's partition still exists, the live cd mounts it in /media/disk and I have access to my /home.

I didn't want to reinstall ubuntu but I can't find any solution to repair my grub :/

Any idea ?

---

### Post by coffeecat on 2009-11-04
These look like legacy grub commands:

> **koskoz said:**
> 
grub
find /boot/grub/stage1 => error 15
root (hd0,2) (I know the numbers even if find doesn't work)
setup (hd0) => error 17

... but your profile to the left of your post says your are running Karmic. Did you do a fresh install of Karmic, or did you upgrade from Jaunty? If a fresh install, then you have grub2 and those commands won't work.

Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

What you need is the section titled [COLOR=Black]"**[B]Reinstalling GRUB 2 from the LiveCD".**[/B] [/COLOR]It's numbered 13 at the top of the post, but 12 in the body of the text. It's not as straightforward as with legacy grub. Good luck!

**Edit**: by the way, I don't think the new Windows install will be added to the menu automatically - I'm new to grub2 myself. If it isn't, the information you need should be in that link, or in:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

What you shouldn't do is edit the main config file, grub.cfg, directly.

---

### Post by koskoz on 2009-11-04
Ow thanks, I didn't know it was grub2.

My live CD is a 8.10 but my ubuntu's version on my hard drive is 9.10.
I guess I need a 9.10 live cd to reinstall my grub ?

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
You'll need a 9.10 CD if you did a fresh install.

---

### Post by coffeecat on 2009-11-04
> **koskoz said:**
> My live CD is a 8.10 but my ubuntu's version on my hard drive is 9.10.
I guess I need a 9.10 live cd to reinstall my grub ?

You don't have a 9.10 CD? So did you do a fresh install or an upgrade from an earlier version?

If you're not sure which version of grub you have, the best way is to look in /boot/grub. If you have menu.lst, then you have legacy grub and we need to see why those commands you posted didn't work. If you don't have menu.lst, but have grub.cfg, then you have grub2.

And if you have both...... :?

---

### Post by koskoz on 2009-11-04
I first install 8.04 then did upgrade to 8.10 then 9.04 then 9.10.
I do have a menu.lst

And I almost posted everything in the first post :/

---

### Post by coffeecat on 2009-11-04
> **koskoz said:**
> I first install 8.04 then did upgrade to 8.10 then 9.04 then 9.10.
I do have a menu.lst

Then you have legacy grub after all, and grub2 was a red-herring.

> **koskoz said:**
> And I almost posted everything in the first post :/

If sda3 is your root partition, or boot if you have a separate /boot, then those commands should have worked. To be honest I never bother with the find command. If I know the partition number, I just do the root and setup commands and it's never failed - and I've reinstalled grub many times before.

Are you absolutely sure your root partition is sda3? Why not post the terminal output of "sudo fdisk -l" from the live CD to be sure (that's lower-case L). I've read somewhere that Windows 7 sets itself up with a tiny subsidiary partition as well as the main C: partition - it's unlike XP and Vista in this respect. I wonder if it's changed the partition table such that your Linux root partition now has a different number.

And those errors 15 and 17 are odd. Curious.

---


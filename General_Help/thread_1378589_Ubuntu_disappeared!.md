---
title: "Ubuntu disappeared!"
date: 2010-01-11
forum: General Help
---

### Post by UncleChicken on 2010-01-11
OK, I did something really, really stupid. I have been using Ubuntu 9.1 for a while and after a steep learning curve, have really enjoyed running it on my machines with no BLUE SCREENS OF DEATH. However, I did get tired of not being able to run certain programs, so I decided to simply throw XP on a 6g partition that was sitting on my machine. Now, I should have known better than to assume that things would just work or that I could do it without screwing things up, but I didn't. Anyway, long story short, my 490 gig partition is just sitting on my machine and I cannot figure out how to access it again. 

 *sigh* I feel like such an idiot. And that is because I am. But is there a simple solution to fixing this problem so that I can boot back to Ubuntu? I'm more than willing to delete XP if that is the solution.

 Thank-you

---

### Post by J V on 2010-01-11
boot into a live cd, mount the boot partition (look it up in gparted) and reinstall grub (google ftw)

---

### Post by UncleChicken on 2010-01-11
OK, thanks - I will try that.

 I had sort of gotten the impression that might work from other things I had read, but none of them specifically adressed my situation

---

### Post by UncleChicken on 2010-01-11
OK, I have re-installed GRUB after a lot of seraching and troubleshooting; par for the course, now, my XP installation has disappeared. Is there a way of making a way so that I have a choice when my computer boots up?

---

### Post by nerdy_kid on 2010-01-11
i know how to do it with jaunty's grub (1?) but not with grub 2.
i just added:
```

title        Windows XP
root        (hd0,2)
makeactive
chainloader    +1

```

after "
### END DEBIAN AUTOMAGIC KERNELS LIST
"
in menu.lst.  dont know how to do it with grub 2 however :|


NOTE:
the "root" setting has to be the number of the HD (so sda would be 0, sdb would be 1, etc) followed by the partition number:  so, if i remember right, hd0,2 would correspond to sda2 once ubuntu was running.

---

### Post by UncleChicken on 2010-01-11
That was actually a helpful reply - I found the code in my boot/grub/ directory (it's called grub.cfg) now. I log on with root privileges, but when I try to edit it with this code:

# (2) Windows XP
menuentry "Windows XP" {
set root=(hd0,3)
chainloader +1
}
and save it, it tells me that I can't save because the disk is read-only! What is going on there? Any suggestions?

---

### Post by louieb on 2010-01-11
The easiest way is to run 
```
sudo update-grub
```Grub2 is great at picking up and  adding other operating systems. That should work. 

and yes grub.conf is read only (even if opened as administrator).  You can make it writable, but that is not the recommended way to modify it.

[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by UncleChicken on 2010-01-11
Well, that was simple!

 Everything works perfectly now! Thank-you so much for all your helps, guys.

---


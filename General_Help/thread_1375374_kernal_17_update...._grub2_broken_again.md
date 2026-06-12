---
title: "kernal 17 update.... grub2 broken again"
date: 2010-01-07
forum: General Help
---

### Post by r0tor on 2010-01-07
So I know I should have known better then to turn my updates back on after the 15 and 16 kernal updates crashed ubuntu and grub.... but I did anyway and once again after a new kernal gets installed i'm stuck at the grub sh prompt.

Been down the road before... tried using

linux /boot/vml.......  root=/dev/sda1 loop=/ubuntu/disks/root.disk ro

when i use the 16 or 17 kernal I get an error stating "invalid imaginary number"... 

so I use the 14 kernal and enter

initrd /boot/initrd.....
boot


and it boots like it did the last time this crashed.  I went to the terminal and entered

sudo apt-get install grub 2
sudo update-grub2

and then rebooted like I did last time expecting the problem to be fixed and at least be able to boot up the 14-generic.... WELL, IT DIDN'T FIX IT THIS TIME!!!!



so now what do I do to fix grub and what do I do about having 2 unbootable kernals??

---

### Post by r0tor on 2010-01-07
problem solved... used this [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/200](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/200)

---

### Post by byStanderone on 2010-01-07
...as to my experience, usually the restore mode function corrects/fixes problems. it is only when this process is unable to do so, that i resort to command line options. one thing i've noticed, would'nt it be better to restore grub from the live cd?

---


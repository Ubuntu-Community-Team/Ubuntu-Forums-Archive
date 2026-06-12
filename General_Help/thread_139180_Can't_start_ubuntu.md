---
title: "Can't start ubuntu"
date: 2006-03-03
forum: General Help
---

### Post by pinkisntwell on 2006-03-03
It's been a while since I can't start ubuntu. No matter which kernel I choose, even if I choose recovery mode, shortly after the ubuntu loading screen appears I get:

/bin/sh can't access tty: job control turned off


With a command prompt which is not bash I think. I've tried asking in IRC channels, nobody seems to know what this is.

---

### Post by stuporglue on 2006-03-03
You've probably landed in busbox, which is built in to the initial ram disk (initrd). 

If my guess is right, what you need to do is:

(short version)
chroot into your Ubuntu and recreate the initrd.

(long version -- commands might be slightly off...I'm at work right now)
create a directory (mkdir /tempmount)
mount your Ubuntu root partition there (mount /dev/hda1 /tempmount)
mount proc inside the Ubuntu root (mount -t proc proc /tempmount/proc)
bind-mount /dev/ inside the Ubuntu root (mount -o bind /dev/ /tempmount/dev)
chroot into Ubuntu land (chroot /tempmount /bin/bash)
recreate the initrd (dpkg-reconfigure linux-image-`uname -r`
exit chroot (exit)
reboot (reboot)
cross your fingers. :-) 

Hope that helps!

---

### Post by pinkisntwell on 2006-03-04
> (long version -- commands might be slightly off...I'm at work right now)
create a directory (mkdir /tempmount)
mount your Ubuntu root partition there (mount /dev/hda1 /tempmount)
mount proc inside the Ubuntu root (mount -t proc proc /tempmount/proc)
bind-mount /dev/ inside the Ubuntu root (mount -o bind /dev/ /tempmount/dev)
chroot into Ubuntu land (chroot /tempmount /bin/bash)
recreate the initrd (dpkg-reconfigure linux-image-`uname -r`
exit chroot (exit)
reboot (reboot)
cross your fingers. 

It works until the dpkg-reconfigure point, when I try that I get:

sudo: unable to lookup ubuntu via gethostbyname()

---

### Post by pinkisntwell on 2006-03-05
Up...

Nobody can help me?

---

### Post by pinkisntwell on 2006-03-17
Before you flame me for bringing this topic back up, I just want to say it's fixed, so if someone searches for a solution they can find it.

I had mistakenly swapped channels on my IDE cables, which meant that gurb couldn't find my ubuntu installation on hda2.

The error message was bit misleading but anyway, all good now.

---

### Post by Adanufgail on 2006-03-22
Same problem, here's what I get:
/bin/sh can't access tty: job control turned off
> mkdir /tempmount
> mount /dev/hdb2 /tempmount
mount: /proc/filesystems: no such file or directory

Any help will be greatly appreciated.

Oh, and I've rebooted a few time before getting this error, and have gone into both XP and Ubuntu, but now I have this problem.

---

### Post by pinkisntwell on 2006-03-22
Are you sure you didn't change anything as I did?

Please read the whole output, not just the last few lines. In my case there was a 

/dev/hda2 not found!

Which I didn't notice and was the key to solve the problem. Post the whole output (from the point the problem surfaces.)

---

### Post by Adanufgail on 2006-03-22
do you mean everything on screen before the tty part, or my input part?
because my input is exactly as I entered it, and I copied the messages down to the T. But if you need the part before the can't access tty, I can get it also.

---

### Post by pinkisntwell on 2006-03-23
When ubuntu is booting it prints some messages on screen sequentially. Read them one by one and you'll see where the problem begins. It will be before the tty message. Post the lines here.

---

### Post by Adanufgail on 2006-03-23
> Uncompressing Linux... OK, booting the kernel.
Loading, please wait...
mount: Mounting /dev/hdb2 on /root failed: invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
#

Hope it helps...

---

### Post by Adanufgail on 2006-03-23
bump.

---

### Post by Adanufgail on 2006-03-24
Sorry to bump again, but I could really use some help on this.

---

### Post by cocox on 2006-05-15
Here is the solution good luck

[http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808](http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808)

:mrgreen:

---

### Post by Adanufgail on 2006-05-15
Don't worry, I fixed it ages ago.

---

### Post by chronusdark on 2006-05-20
could you post how you did it im having the same problem

---

### Post by chronusdark on 2006-05-21
i fixed it  some program edited my grub and changed sda3 to hda1 on my initrd

---


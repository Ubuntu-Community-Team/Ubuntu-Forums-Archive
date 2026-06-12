---
title: "Ubuntu 10.10 on Lenovo Ideapad S12"
date: 2010-10-19
forum: General Help
---

### Post by tduccuong on 2010-10-19
Hi everyone,

I am experiencing this weirdness since ubuntu 10.04, and it has gotten worse after I installed fresh ubuntu 10.10 today. 

During and even after the installation, the system continuously just pauses showing no activity/progress until I touch the mouse, or press a key to proceed! For example, when I am installing a package, the progress bar just stops at some point until I move the mouse. It progresses a little and stops until I move the mouse again. This happens again and again for every activities that I can do with the system.

Can someone point me out what is it and how to fix it?

Thanks,
Cuong

---

### Post by tduccuong on 2010-10-25
Any one pls?

Thanks

---

### Post by mk500 on 2010-10-28
I'm having the same problem with my Lenovo S12 with clean 10.10. I find that the hard drive light goes completely out. When I hold the shift key, it lights again and is booting. When I release it goes out again.

At some point I made the below change to grub that solved the problem after boot; but I still have to hold the shift key at boot every time or it just sticks at the black screen with white curser and no disk activity. Once I see text on the screen showing its booting I can release shift.

(replace vi with your choice of editors)
sudo vi /etc/default/grub
change the following line :
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=0"
update-grub

Useful threads:
[http://ubuntuforums.org/showthread.php?t=1593549&highlight=Lenovo+S12](http://ubuntuforums.org/showthread.php?t=1593549&highlight=Lenovo+S12)
Bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643822)

I'm also experiencing the wireless problem as detailed here (not sure if related):
[http://ubuntuforums.org/showthread.php?t=1596043&highlight=Lenovo+S12](http://ubuntuforums.org/showthread.php?t=1596043&highlight=Lenovo+S12)

---

### Post by tduccuong on 2010-10-29
Thanks mk500 for ur detailed reply. I will try it out and give report of how it looks..

Update: It worked! Thanks a lot mk500 :)

---

### Post by mk500 on 2010-11-01
> **tduccuong said:**
> Thanks mk500 for ur detailed reply. I will try it out and give report of how it looks..

Update: It worked! Thanks a lot mk500 :)

Great! Do you still need to hold shift at boot though? I still do :-( Did you just make the change I mentioned; or did you make other changes referenced in those links?

---

### Post by tduccuong on 2010-12-02
Hi, I droped ubuntu and installed fedora instead. However I still face the same problem. Here is what I did in fedora, and it worked: 

selinux=0 nolaptic_timer nohz=off highres=off

I dont know if it works in ubuntu, but doesnt hurt to try rt?

good luck to you :)

---

### Post by Sylslay on 2010-12-02
Where is that goes?

"selinux=0 nolaptic_timer nohz=off highres=off"


1. boot option for grub ???
2. /etc/rc.local ???

---

### Post by tduccuong on 2010-12-03
those are kernel flags. Here are the steps:

Fedora:
- su
- nano /boot/grub/grub.conf
- add these flags after the 'quiet' flag

Ubuntu:
- sudo nano /boot/grub/menu.lst
- add these flags at the end of the default boot line e.g., 'kernel /boot/vmlinuz...'. And you may want to remove the 'selinux=0' here for ubuntu.

Hope this helps
Cuong

---

### Post by mtelesha on 2010-12-31
disabling selinux is never a good idea. Personally I like app armor but this is not good advice in terms of security. Did you notice that this fixed the issue or did you normally just get rid of selinux on boot? I know a ton of people who do this on all of their Linux installs with selinux.

I also have this same issue but since this is a fix for grub and not grub2 which is now the default boot loader for Ubuntu this isn't working for me. If I figure out the fix for grub2 I will post.

---

### Post by mtelesha on 2010-12-31
Fixed through updating grub2 but works for grub also

sudo nano /etc/default/

add to the following: quiet splash nolapic_timer to GRUB_CMDLINE_LINUX_DEFAULT=
example:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer"

then update grub or grub2 with
sudo update-grub or sudo update-grub2 depending on what grub you are using.

Fixed my issue with booting up.

-Marc

---


---
title: "how to work with &quot;grub rescue&gt;&quot;"
date: 2012-04-15
forum: General Help
---

### Post by loolooyyyy on 2012-04-15
i want to boot from 'a cheap not so good usb flash disk - on a crappy cheap pc with buggy not to be updated bios'  to install ubuntu
but well, grub wont recognize anything and jumps to grub rescue>

"grub rescue> ls" says:

(hd0) (hd0,msdos1) (hd1) (hd1,msdos6) (hd1,msdos5) (hd1,msdos1)

judging from number of partitions, usb flash should be hd0

so:
grub rescue> root=hd0,1
grub rescue> prefix=(hd0,1)/boot/grub

ok, now what? how do i tell grub to boot the os? no command such as 
"grub rescue> boot" ...
what are the possibe commands? (help , /? , ? are not available)

---

### Post by oldfred on 2012-04-15
Is this a full install on a flash drive or on your system? I have full installs on Microcenter house brand flash drives that work well. 

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

If you can boot flash or also want a CD or another flash and want to repair install on hard drive:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by loolooyyyy on 2012-04-15
> **oldfred said:**
> Is this a full install on a flash drive or on your system? I have full installs on Microcenter house brand flash drives that work well. 

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

If you can boot flash or also want a CD or another flash and want to repair install on hard drive:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

wow very good articles tanx
it is ubuntu server installation disk actually, i forgot  about it and found a DVD drive and used it, but since i face grub rescue regularly, i'm gonna study those carefully, thanks again

---


---
title: "symbol not found grub_env_export"
date: 2011-08-08
forum: General Help
---

### Post by HaRabAS on 2011-08-08
Recently did a clean install (instead of upgrade) of 11.04 from 10.10 and this error bugged me for the first time. I have tried many solutions ([http://ubuntuforums.org/showthread.php?t=1742655&page=2](http://ubuntuforums.org/showthread.php?t=1742655&page=2), [https://help.ubuntu.com/community/Gr...3%20-%20CHROOT]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT"))but nothing works. Been tinkering for about three hours and I think heads gonna explode.

[I]ubuntu@ubuntu:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

followed this one too to the letter:

[I]ubuntu@ubuntu:~$ sudo chroot /mnt/clean/sda1 apt-get install -y grub-pc
chroot: failed to run command `apt-get': No such file or directory[/I]

tried this one too:

[I]ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
/usr/sbin/grub-probe: error: cannot stat `aufs'.
[/I]
and this too which got me a bash something:

[I]ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt
bash: groups: command not found[/I]


i'm a bit tired and too sleepy atm so i'm gonna check this thread back again tomorrow.

---

### Post by HaRabAS on 2011-08-08
so no one wants to help eh, fine then!!

---

### Post by HaRabAS on 2011-08-09
community support is supposed to be a star in this linux world, guess i was wrong.

/sighs

just gonna reinstall this pos and hope grub installs correctly, or just switch back to 10.10 and hope for the best. this is such an embarassment.

---


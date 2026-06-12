---
title: "Sudo/Synaptic Problem sudo: must be setuid root"
date: 2010-07-09
forum: General Help
---

### Post by Cybrmerc on 2010-07-09
Alright so I recently have done a few things partition wise and now I have an issue with my sudo commands. A little backstory:

     Moved my /usr to its own partition for filespace reasons

     Created a new partition for a windows install

     Reinstalled grub as per Win install prior to Ubuntu

Ubuntu works fine except that when I try a sudo command I get sudo: must be setuid root. Synaptic doesn't open at all. Now I have read through several forums where the suggested fixes (from recovery console) did not work:

     chown root:root /usr/bin/sudo              
     (ls 'l of /usr/bin/sudo was green - sudo still no joy)

     chmod 4755 /usr/bin/sudo
     (ls -l of /usr/bin sudo was red back/white text - sudo still no joy)

     chmod u+s /usr/bin/sudo 
     (ls -l of /usr/bin/sudo was red back/white text - sudo still no joy)

     I tried /etc/sudoers fix but the file seems to be fine

Now currently my ls -l of /usr/bin/sudo and sudoedit looks like this:

          -rwsr-xr-x 2 root   root 148024 2010-07-08 16:35[COLOR=Black]/usr/bin/sudo (red back/whitetext)
      -rwsr-xr-x 2 root   root 148024 2010-07-08 16:35 sudoedit (red back/white text)

But even when I chown root:root /usr/bin/sudo and the entries go green, sudo commands still fail. I'm assuming the main problem is that my /usr directory was moved to its own partition which somehow screwed it up. Anyone got any ideas of how to fix this issue?
[/COLOR]

---

### Post by sisco311 on 2010-07-09
You have to mount the /usr partition with the suid mount option. Please post the content of the fstab file:
```
cat /etc/fstab
```

---

### Post by Cybrmerc on 2010-07-09
cybrmerc@GhostNet:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cb1926ac-ac02-4773-9bf5-95e1358bf067 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=0e196938-bdc6-427c-a0b8-bb4e3a12febe /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=07eb5a8a-5380-45d6-a2be-e72360e99d69 none            swap    sw              0       0
/dev/sda6 /usr ext4 nodev,nosuid 0 2


I added last line, is it lacking the UUID piece above it??

---

### Post by sisco311 on 2010-07-09
Edit the last line to:
```
UUID=**uuid-of-the-partition-here**    /usr    ext4    **defaults**    0    2
```
to get the UUID of the partition run:
```
sudo blkid -c /dev/null -o list /dev/sda6
```

Linux now prefers to use UUID, LABEL, or symlinks to identify media storage devices on a system. Directly using /dev/hd*# or /dev/sd*# is no longer preferred since these device assignments can change between system boots.

The nosuid mount option does not allow setuid and setgid bits to take effect.

For more info:
[http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)
[thread=283131]Understanding fstab[/thread]
[uhelp]community/UsingUUID[/uhelp]

---

### Post by Cybrmerc on 2010-07-09
Awesome - worked like a charm! Thanks, totally forgot about my fstab entries =) - synaptic is up and running and that stupid power management error is gone too :D

---


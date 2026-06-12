---
title: "Problem booting Ubuntu?"
date: 2011-03-16
forum: General Help
---

### Post by galexy19 on 2011-03-16
Hello, I'm running Ubuntu 10.10 on a desktop and I'm having problems booting. When I try to boot I get the error 
```
 DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER 
```ok, when I enter system disk to diagnose the problem, I then get the screen... .

```
 (initramf's) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/ouput error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs 
```I just recently changed my RAM thinking that was the problem, but its not. It appears thats its having trouble mounting a filesystem? Could anyone please help with the problem? 


[SIZE=1]*Emachine AMD 2.7 ghz processor, 1024 mb RAM, 500 gb Harddrive (no partitions), 9600 ati Radeon graphics card, motherboard soundcard*[/SIZE]

---

### Post by galexy19 on 2011-03-23
Lol, so it turns out the reason I couldn't boot was because the cdrom  drive I was trying to boot live cd from was having problems. I unplugged  that, and made my slave the master. The live cd booted then.

```
 fdisk /dev/sda1 (or what ever sh#%%y drive you have)  
```

push 'y' to all errors. 
Reboot, should have fixed bad sectors on drive!

---


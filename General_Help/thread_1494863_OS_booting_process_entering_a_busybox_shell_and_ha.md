---
title: "OS booting process entering a busybox shell and halts"
date: 2010-05-27
forum: General Help
---

### Post by deostroll on 2010-05-27
I think I have a problem similar to this one > [http://bit.ly/b0WJZ2](http://bit.ly/b0WJZ2)

I use ubuntu 9.10. The os was working find until one day +poof+ the busybox shell showed up out of no where...

The os shows the ubuntu logo before the log-in page shows up, but then goes blank. On hitting escape I find a message saying...

```
Gave up waiting for root device. Common problems: ...
```

Finally it says something like:
```
ALERT! /dev/disk/by-uuid/e669c383-063f-40e5-b67f-ed155ce404cd4
```..and then prompts 
```
(initramfs)
```
(man, its hard typing all that!!!)

Anything I can do to troubleshoot. 

FYI. Someone in the IRC told me I had to look for a post concerning with grub 2.0, but I noticed I am still in grub 1.5

---

### Post by chrone on 2010-06-19
> **deostroll said:**
> I think I have a problem similar to this one > [http://bit.ly/b0WJZ2](http://bit.ly/b0WJZ2)

I use ubuntu 9.10. The os was working find until one day +poof+ the busybox shell showed up out of no where...

The os shows the ubuntu logo before the log-in page shows up, but then goes blank. On hitting escape I find a message saying...

```
Gave up waiting for root device. Common problems: ...
```

Finally it says something like:
```
ALERT! /dev/disk/by-uuid/e669c383-063f-40e5-b67f-ed155ce404cd4
```..and then prompts 
```
(initramfs)
```
(man, its hard typing all that!!!)

Anything I can do to troubleshoot. 

FYI. Someone in the IRC told me I had to look for a post concerning with grub 2.0, but I noticed I am still in grub 1.5

by changing the root device UUID to your device path will solve this.

for example the root / filesystem is /dev/sda1, then remove the grub boot option (UUID=blablablabla) to /dev/sda1 and then press tab in the grub menu and enter and then press b to boot the drive.

after finally booting the system, go to terminal and then change the boot menu.lst: sudo nano /boot/grub/menu.lst

change the UUID=blablabla in grub boot option to /dev/sda1, save and exit. go: sudo update-grub

hope this will solve your problem. i just did it yesterday and it worked! :)

---


---
title: "Error: no such device During Booting !! Grub Rescue. Please urgent"
date: 2010-09-13
forum: General Help
---

### Post by mina.mohsen on 2010-09-13
Hey people please I need your help :S

I have Ubuntu 10.04, I have run the update manager and installed grub,
Then the computer freezes and nothing happened.
I restarted my computer and a black screen appears before any other boot screen:

[B]Error: no such device: 598071d2-3871-4b28-a831-0ece4415046
Grub Rescue>

I tried ls, it tells me
(hd0)

[/B]**Take in mind that I have installed ubuntu 10.04 through wubi.**
[B]I tried to run a live cd with an older ubuntu version,
and according to this topic:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


[/B]I entered
```
sudo grub
```and it opened the grub prompt

and then entered:
find /boot/grub/stage1

and the output is:
Error 15: File not found

Please dont hesitate to provide any mean of help.

---

### Post by bcbc on 2010-09-13
You need to reinstall the windows boot loader. Depending on what version of windows you are running the commands are different:
xp: fixmbr
vista/7: bootrec.exe /fixmbr

If you don't have a windows disk you can achieve the same fix by installing lilo from a liveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

You will see warnings after running the first command that you can ignore. They don't apply to the use of lilo above.

FYI here is the bug report: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by mina.mohsen on 2010-09-13
Thanks [bcbc]("http://ubuntuforums.org/member.php?u=946783") that really solved the problem :)

But another problem appeared after booting to Ubuntu,
a black screen with this message:
```
udevadm trigger is not permitted while udev is unconfigured.
```I waited few seconds and it booted opening Ubuntu first login screen with message:

```
The disk drive / is not ready yet or not present
continue to wait; or Press S to Skip mounting or M for Manual recovery
```I pressed S to skip, another message appears:

```
The disk drive /tmp is not ready yet or not present
continue to wait; or Press S to Skip mounting or M for Manual  recovery
```I didnt press anything and the first message with the black screen appears again:
```
udevadm trigger is not permitted while udev is unconfigured.
```

Here is Boot menu after choosing Ubuntu:
```
Ubuntu, Linux 2.6.32-24-generic
Ubuntu, Linux 2.6.32-24-generic (recovery mode)
Ubuntu, Linux 2.6.32-21-generic
Ubuntu, Linux 2.6.32-21-generic (recovery mode)
Microsoft Windows XP Professional (on /dev/sda1)
```

---

### Post by bcbc on 2010-09-13
Try the -21 kernel in the meantime. There have been some issues with the -24. I'll try and forward some links later with a potential fix.

---

### Post by mina.mohsen on 2010-09-13
Ok, Thanks bcbc for your help.

---

### Post by bcbc on 2010-09-13
This thread is regarding some -24 kernel issues. Note some of the fixes are not a good idea - particularly rebuilding the initrd.img for ALL kernels. You don't want to interfere with the working kernel you have.

[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

---


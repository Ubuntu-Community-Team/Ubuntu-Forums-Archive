---
title: "'Minimal BASH-Like line editing is supported' at startup"
date: 2010-08-22
forum: General Help
---

### Post by ryanyehh on 2010-08-22
So I turn on my PC this morning, and it comes up with this telling me to use 'TAB' to see a bunch of options I can use, not knowing any idea on how to use them properly I type in 'boot', it returns with 'error: no kernel' and then I type 'exit', it just reboots.

I've scanned endless posts on the forum trying to find the most useful replies and tried to use 'find /grub/stage2' and 'find boot/grub/stage2' and it says 'find is not a command' so that failed. I then tried to find out the partition my installation is in, which is hd0,1 so I tried using 'setup (hd0,1) which returned with 'setup is not a command'. I even tried 'boot (hd0,1) but it returned with the first error 'error: no kernel'.

Luckily, when I installed Ubuntu I dual-booted it with Windows so I'm still able to use the Internet but I would love Ubuntu back and I had a lot of important files on it. So does anyone know how to solve this?

By the way, the way I installed Ubuntu was through Windows using 'wibu', it's worked absolutely fine ever since this morning.
Oh and I'm using Ubuntu 10.04 (Loopy Lynx or whatever it's called ;p)

(Also, for more information this screen appears after I choose 'Ubuntu' from the Windows bootloader, it doesn't even get to the Ubuntu bootloader it just goes straight to that screen)

Thanks.

--EDIT--

Okay, I have worked out the 4 commands I need to use to fix this problem, which are;

```
root (hd0,2)
```(This is the correct partition, so this command works fine)
```
kernel /vmlinuz root=dev/hda*
```(the asterick resembles what number hda the kernel is in, but this I do   not know. A grub article says that you can use 'find /vmlinuz' and  'find  /sbin/init' to find out where the kernel is but when I try to use   'find' it says it is not a command, why is this? Also, I tried  guessing  where the kernel is by using 'kernel /vmlinuz root=dev/hda2'  but it  returned with 'kernel is not a command. WTF, why don't these  commands  work?)
```
initrd /initrd.img
``` (Simply cannot work due to their being no kernel loaded from the beforehand command, obviously)
```
boot
``` (Same as above) 

So yeah basically, the only problem I'm having is finding out where the kernel is (one of the dev/hda*) and how to load it as the commands 'find' and 'kernel' are apparently not valid commands..

Thanks.

---

### Post by Brandon Williams on 2010-08-22
[Here](https://help.ubuntu.com/community/Grub2#Command Line and Rescue Mode) is a good source of documentation about rescue mode.

You should be able to figure out which drive is the root using the command ls. Also, not that when you specify the root drive, it should be "/dev/sda*", not "dev/sda*" as in your examples.

---

### Post by ryanyehh on 2010-08-22
Good link, has helped me realise that these are now the correct codes for wibu installation:

```
set root=(loop0)
``````
linux vmlinuz root=/dev/sd** loop=/ubuntu/disks/root.disk ro
``````
initrd /initrd.img
``````
boot 
```BUT.
Still I have not found out a way to find which directory my kernel is actually in, '/dev/sd**', I still don't know what mine is and don't know how to find it out.

Also, when I took a guess it tells me 'vmlinuz' is not a correct file name.. any ideas?

(And yeah I know it's '/dev/sda' it was a typo)

--EDIT--

After trying to fix this problem so much I have finally learnt pretty much all the commands, but a couple of problems still arise. When I 'ls' /dev there isn't any '/sd**' of any kind in there. Also, if I just let it work from just the '/dev' folder it seems like it's working due to all the information appearing on the screen but then all of a sudden comes up with the error '/ubuntu/disks does not exist'. 

Whaaat is going on? Please help. /:

---

### Post by Brandon Williams on 2010-08-23
Hopefully someone more familiar with wubi installs will be able to help on this, but in the meantime ...

What is the output of this grub command?:
```
ls (loop0)/
```

If it gives you a listing, does the listing include both a /dev and a /ubuntu directory? And if it does, what is the output from these commands?:
```
ls (loop0)/dev/
ls (loop0)/ubuntu/
```
Do those commands appear to show the expected paths/files?

---


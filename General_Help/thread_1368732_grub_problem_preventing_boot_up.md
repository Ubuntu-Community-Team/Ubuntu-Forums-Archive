---
title: "grub problem preventing boot up"
date: 2009-12-31
forum: General Help
---

### Post by ahadiel262 on 2009-12-31
I am new to Ubuntu and unexperienced in terms of its commands. Currently I am dual-booting Ubuntu and Windows Vista. 

I had Ubuntu up and running perfectly and was playing with the cool shaky windows and 3d cube
and tried to install some grub splashes to make the entry screen look cool.

Unfortunately, now when I select Ubuntu from the initial list I get this screen:

GNU GRUB version 1.97beta4

[Minimal BASH-like line editing is not supported. For the first word, TAB lists possible
command completions. Anywhere else TAB lists possible device/file completions.]

Now, I did try to look for solutions to this problem before, and a theme seemed to be
with partitioning which I am clueless about. But, this seemed to be important:

sh:grub> ls
(loop0) (hd0) (hd0,5) (hd0,3) (hd0,2) (hd0,1)

Now, I don't have a LiveCD I just downloaded the version made for dual-booting with Windows
Vista so if there is a fix which avoids me needing that disc that would be preferable.

And if there's time, maybe an explanation, so if it happens again I could figure it out for myself.

---

### Post by drs305 on 2009-12-31
First, ahadiel262, welecome to Ubuntu and the Ubuntu forums.

We'd like to know if this is a normal Ubuntu install or if it's a "wubi" install inside Windows. 

This may be a bit too much for your first time on Ubuntu, but there is a Grub 2 document that discusses how to boot from the Grub 2 command line. [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2") There is a section on Command Line & Rescue mode that discusses how to boot from the Grub 2 prompt if you want to try to take it on.

Since you are getting to a Grub prompt, it means that Grub is at least partially working and it can see your partitions.

Do you know which partition your Ubuntu install is on? From that command prompt in Grub, you can explore your disks using this command format:
```

ls (hd0,5)/

```
You can do that with any of the partitions Grub 2 found. You can see if your Ubuntu boot files are there with this command. Try hd0,5 first, but if nothing is there, try other combinations:
```

ls (hd0,5)/boot
ls (hd0,5)/boot/grub

```

In /boot, you should have a file called vmlinuz...something (like vmlinuz-2.6.31-16-generic) and initrd.img...something (
initrd.img-2.6.31-16-generic).
In /boot/grub, you should see a file called grub.cfg. 

Do you see those files?

---

### Post by ahadiel262 on 2009-12-31
Hey drs305, thanks for helping me out.

I retraced my steps and yes I did do a wubi install.

I do not know which partition it is on, but i did 
ls (hd0,x)/boot for all of them and (hd0,3) was the only one
which displayed any files. For all the other ones I got
error: file not found except (hd0) which said unknown filesystem.

In /boot I do have those files,

and in 

/boot/grub I do have grub.cfg

ls (hd0,3)/boot/grub did not have any files however.

ls (loop0)/boot/grub has:
device.map unicode.pf2 grub.cfg grubenv splash.xpm.gz splashimages/

---

### Post by drs305 on 2009-12-31
See if you can boot to the Desktop with these commands. We will try the easy way first:
```

set root=(hd0,3)
linux /vmlinuz root=/dev/sda3 ro
initrd /initrd.img
boot

```

If that doesn't work, we can try it with a few more commands.

---

### Post by ahadiel262 on 2009-12-31
The set root=(hd0,3) command worked,

but when I tried

linux /vmlinuz root=/dev/sda3 ro

I got error: file not found.

I then tried it with every partition and none of them had the file.

---

### Post by drs305 on 2009-12-31
> **ahadiel262 said:**
> The set root=(hd0,3) command worked,

but when I tried

linux /vmlinuz root=/dev/sda3 ro

I got error: file not found.

I then tried it with every partition and none of them had the file.

I can't stay online any longer. You seem to have a good handle on the file operations. If nobody else replies soon, I would try the more comprehensive steps in the doc I linked to in the first post. You may have to set the prefix - run all the steps in the Rescue Mode section, and if that doesn't work you can also try the "Boot to a Specific Kernel Manually" section.

Here is the starting point for both:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

I'll check back tomorrow (later today) to see if you made any progress. Best of luck.

---

### Post by ahadiel262 on 2009-12-31
Alright, it isn't working yet but I got really close. I attempted to do the boot to a 
Specific Kernel Manually steps from the link you gave me.

Since it was not working with the usual partitions, and since loop0 is where
the /boot revealed all the files, I tried it using loop0 as the partition.

I got all the right outputs, but at the end I got

ALERT! /dev/loop0 does not exist. Dropping to a shell!

so for (hd0,1) the equivalent is /dev/sda2 correct?

so for loop0 I need to find the equivalent /dev/X I believe.

---

### Post by ahadiel262 on 2009-12-31
Oh man... 

I think I found the answer:

[http://www.ihisham.com/2009/12/how-to-fix-grub-bug-after-updating.html](http://www.ihisham.com/2009/12/how-to-fix-grub-bug-after-updating.html)

---

### Post by ahadiel262 on 2009-12-31
IT WORKED!

SDA3 was the key. Now there is something about my NVIDIA graphics card
and how it didn't configure correctly. 

I may just get rid of wubi and make my own live CD and install it side by side.

Thanks for all your help!

---

### Post by drs305 on 2009-12-31
Glad you got it working. I am going to add a note to the community doc about the additional information needed in the linux line when booting wubi from the rescue mode. I've known about it for a while but you have confirmed it works. Thanks for the feedback.

---


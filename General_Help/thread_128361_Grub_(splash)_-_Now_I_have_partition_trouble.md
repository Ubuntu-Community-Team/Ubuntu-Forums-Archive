---
title: "Grub (splash) - Now I have partition trouble"
date: 2006-02-11
forum: General Help
---

### Post by SWAT on 2006-02-11
Let me start by explaining what I WAS trying to do. I just wanted to spiffy up my grub bootloader by adding a nice picture to it. Somehow it wasn't working and I edited the /boot/grub/menu.lst some more (trying to find out why it didn't work). Eventually this resulted in not being able to boot into my Ubuntu install anymore. :-# So now I'm looking for a fix.

*So what the hell did I do?*
I edited the following line in my /boot/grub/menu.lst file 
```
# kopt=root=/dev/mapper/Ubuntu-root ro
```(If I remember correctly this should be the line)

And I replaced it with
```
# kopt=root/dev/hda1 ro
```(or something like that)


*What do I get when I try to start my Ubuntu install?*
```
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: mounting /dev on /root/dev failed: no such file or directory 
target filesystem doesn't have /sbin/init
```

I use 2 partitions. My hda1 is my /boot and my hda5 is my 'normal' partition. I would love some help with this issue :confused:

---

### Post by SWAT on 2006-02-11
OK, I've figured out it has something to do with my /dev/Ubuntu (apparently my root partition is located at /dev/Ubuntu/root  which I find very strange). The question that remains is how to 'reset' GRUB or 'reconfigure' GRUB so I can get back to work... :-k

---

### Post by Irony on 2006-02-11
To restore grub see; [http://ubuntuforums.org/showthread.php?p=723858&posted=1#post723858](http://ubuntuforums.org/showthread.php?p=723858&posted=1#post723858)

Also it helps if you back up your menu list before you alter it;

[PHP]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup[/PHP]

so if things go pear shaped and you end in shell then at the prompt type;

[PHP]sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst[/PHP]

---

### Post by SWAT on 2006-02-11
Irony, hehehe, normally I back things up. Somehow I forgot this time :-# 

But I found my error (and so it was fixed). My code-line should have been
```
# kopt=root=/dev/Ubuntu/ ro
```This thanks to LVM :-k

---


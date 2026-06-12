---
title: "reboot failure"
date: 2010-04-09
forum: General Help
---

### Post by ewuntu on 2010-04-09
I am new to Linux and its ways and need your help.
 
Installed Ubuntu 9.10 on an external drive, several times as it turns out, since Feb. 2010.
It works fine, for a week or two, until I start to add,update and upgrade the progs. then I run into:
 
GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported for
the first word, TAB lists possible command completions.
anywhere else TAB lists possible device/file completions.]
 
sh:grub>
 
This usually happens after add/update or upgrade and I am instructed to "save and
restart for the progs. to take effect".
Most of the time I am using the CLI but it has happened with the Synaptic Mgr.
 
Is there a special "save and restart" procedure or am I missing something else?
Any and all help welcome. Thanks in advance.

---

### Post by themusicalduck on 2010-04-09
Did you install Ubuntu using WUBI? i.e. installed from within windows rather than on a separate partition? If you did, then try this -

```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot
```

If you manage to boot, then once in open a terminal (Applications > Accessories > Terminal) and run ```
sudo update-grub
```

Then assuming that command works, you should be able to reboot and it will work fine.

On this line: ```
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 
```
Since you installed it on an external drive, I'm gonna guess that it is "sdb1" however if that doesn't work, try sdb2, sdb3. If they don't, then try sda1, sda2, sda3.

If none of those work, then let me know. Although assuming you only have one internal hard drive and one external, one of those should work.

Lastly, if you're planning on using this installation for a long time, I'd much more recommend installing it to a proper partition. This problem seems to happen to most people and a dedicated install is more reliable.

It's fine for testing out Ubuntu for a while though.

---

### Post by oldfred on 2010-04-10
If you have wubi there is a bug in the 9.10 version. Fix instructions:

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by oldfred on 2010-04-12
Did you install the fix for C:\wubildr?

Slightly simplified instruction to manually boot, if install is on sda1:

Type this at "grub sh>" prompt:

set path=/ubuntu/disks/root.disk
linux /vmlinuz root=/dev/sda1 loop=$path ro
initrd /initrd.img
boot

vmlinuz and initrd.img are links to the most current kernel in /boot, so  you do not have to type all the details.

---


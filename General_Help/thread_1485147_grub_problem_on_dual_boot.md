---
title: "grub problem on dual boot"
date: 2010-05-16
forum: General Help
---

### Post by amite on 2010-05-16
i have installed ubuntu 9.10 inside windows vista.now when i start my system i get option to select windows or ubuntu. windows can start successfully but ubuntu start up fails and give grub shell prompt as :
> 
                        GNU GRUB version 1.97~beta4
[ Minimal BASH-like line editing is supported. For the first word, TAB
   lists possible command completions. Anywhere else TAB lists possible 
   device/file completions. ]

sh:grub>

Help me!!!!!!!

---

### Post by oldfred on 2010-05-16
If you are running wubi with version 9.10:

Fix for grub2 problem with wubi with 9.10
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by amite on 2010-05-16
although i am not familiar with grub very much but tried instruction on  [http://www.linuxjournal.com/article/4622?page=0,1](http://www.linuxjournal.com/article/4622?page=0,1)
> grub> root (hd0,1)
grub> kernel /vmlinuz root=/dev/sda2 ro vga=791
grub> boot

on my system results are:

sh:grub> root (hd0,1) 
[COLOR=DimGray](hd0,1): Filesystem is ntfs.[/COLOR]

sh:grub> kernel /vmlinuz root=/dev/sda1 
[COLOR=Navy]**error: unknown command 'kernel'**[/COLOR]

---

### Post by amite on 2010-05-16
@[oldfred]("http://ubuntuforums.org/member.php?u=852711"):
Thanks,it's working........

but i have remain one question why the commands in previous post doesn't working,and specially why i got the error message with 'kernel'.

---

### Post by oldfred on 2010-05-16
the sh:grub is not the same as a grub or now with grub2 grub rescue. So you were not at a normal grub command line. The instructions were very old and now we have grub2 which is different.

wubi adds some differences since it is inside a windows NTFS partition and not in its own linux based partition.

---


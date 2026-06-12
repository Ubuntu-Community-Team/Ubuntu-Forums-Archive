---
title: "Vmware question"
date: 2006-04-09
forum: General Help
---

### Post by leftyman on 2006-04-09
Hello:


I have 2 hdd´s both of them using ext3. I want to reserve 10GB for a windows xp installation within vmware.


Can my windows applications access files in the ext3 hdds?

thank you

---

### Post by towsonu2003 on 2006-04-09
[QUOTE=leftyman]
I have 2 hdd´s both of them using ext3. I want to reserve 10GB for a windows xp installation within vmware.


Can my windows applications access files in the ext3 hdds?

thank you[/QUOTE]
vmware gives you emulation so you'll be running windows (using a file located in linux partition) from within linux. you can't get access to your ext partitions that way. samba may help, but I'm clueless on that. 

if dual booting, check [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) out.

---

### Post by kevieboy on 2006-04-09
If you goto the applications menu > Add Applications > System Tools > More Programs there should be a program called QT Parted.  It should allow you to edit the partitions.

---

### Post by towsonu2003 on 2006-04-09
[QUOTE=kevieboy]If you goto the applications menu > Add Applications > System Tools > More Programs there should be a program called QT Parted.  It should allow you to edit the partitions.[/QUOTE]
Although you could, you don't need to use partitions with vmware. A .vmdk file used as an hard disk with vmware emulation. a vmdk file is much "cheaper" than a partition in how much space it takes. My 20G downloaded (see below) vmdk file now takes up only 1.6G or so. 

check this page out for more info on that file: [http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php](http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php) It also lets you download pre-made files (500MB, 5G, 10G, 20G) all as 5k files or so... You than tweak a certain .vmx file to make vmware aware of these files. 
unlike vmware player (free), I think vmware workstation has a tool to create thi stuff for you.

---

### Post by leftyman on 2006-04-09
There is some misunderstaning here,

What I really want to do is install Windows XP, Office XP and a music notation program (not supported bby wine) in a growing .vmdk file.


My question is:

Is there w way I can access my hdd contents (for example my /home directory) from the windows applications?

In other words I want to exchange files between the host and the guest
operating systems.

thank you

---

### Post by towsonu2003 on 2006-04-09
[QUOTE=leftyman]
[b]I want to exchange files between the host and the guest
operating systems.[/b]
[/QUOTE]
these may help a little:
[http://www.ubuntuforums.org/showthread.php?t=84275&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=samba+howto)
[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+howto)
[http://lists.gnu.org/archive/html/qemu-devel/2004-09/msg00150.html](http://lists.gnu.org/archive/html/qemu-devel/2004-09/msg00150.html)
[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto)

you're basically looking for a howto that covers samba file sharing and vmware...

---


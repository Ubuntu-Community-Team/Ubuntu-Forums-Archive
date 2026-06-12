---
title: "Booting"
date: 2011-03-12
forum: General Help
---

### Post by Semi_Nerd on 2011-03-12
This morning I was messing around with the bash.bashrc file, trying to customize my terminal. My dad I went to lunch, and when we got back, Ubuntu wouldn't boot. It said something about Logitech USB controllers not calibrating for the relative axes or something like that... Win7 worked fine. After much troubleshooting, I decided to start from scratch. I deleted the partitions with Ubuntu, and left the ones with Win7. When I tried to reinstall Ubuntu, I couldn't select a partition. I pushed the reset button, and after POST, I got the message:

error: no such partition
grub rescue>

I can get into Win7 if I put in Hirens boot CD and then select "boot from hard drive." I wouldn't mind this so much if I was the only one using the computer. Does anyone know what happened and how I can fix it?

---

### Post by Hedgehog1 on 2011-03-12
Semi_Nerd,

When you want to remove Ubuntu from a dual boot system, there are two basic steps:

1) Run FIXMBR for windows to boot directly (no grub)
2) Then remove the Ubuntu partitions.

You will need your Windows7 repair CD - and you can generate one from Windows 7 if you cannot find yours.

To make a Windows emergency repair disk:
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]


Booting from the windows 7 emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-12
To remove Ubuntu:
[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space (OPTIONAL IF YOU ARE REINSTALLING UBUNTU)
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]

Now you can reinstall Ubuntu safely.

***The Hedge***

:KS

---

### Post by Semi_Nerd on 2011-03-13
Thanks Hedge!

---


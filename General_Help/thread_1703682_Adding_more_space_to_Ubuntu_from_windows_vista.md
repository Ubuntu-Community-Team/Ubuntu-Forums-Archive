---
title: "Adding more space to Ubuntu from windows vista"
date: 2011-03-09
forum: General Help
---

### Post by mubtasim123 on 2011-03-09
Hi, I am using ubuntu inside windows vista but when I first installed I used very low memory with it. I seen and read some tutorials about how to expand it through GParted but seems it's not working or not allowing me to expand.
[IMG]http://2.bp.blogspot.com/--xcUqDdkFYM/TXfsl-KVKPI/AAAAAAAAAIo/EE6wNN31lUs/s320/Screenshot--dev-sda%2B-%2BGParted.png[/IMG]
//
[IMG]https://lh3.googleusercontent.com/-i8GmgEoyGXQ/TXfsyZOq-ZI/AAAAAAAAAIw/W__5gkHpZis/s320/Screenshot--dev-sda+-+GParted-1.png[/IMG]
//
[IMG]https://lh5.googleusercontent.com/-qcT6DwIpUas/TXfs3fJU9dI/AAAAAAAAAI0/GEq75vcVP0A/s320/Screenshot-Untitled+Window.png[/IMG]
//
so can anyone help me with this situation how to add more space to Ubuntu. ;)

---

### Post by tordeu on 2011-03-09
Did you run gparted from within the installed Ubuntu? If so, please try using the gparted live cd: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by deskman on 2011-04-09
hi! u asked me on youtube. so i guess u didnt install it with Wubi. so if that is correct, than u have to use an ubuntu live cd, but i strongly recommend the 10.04 version because when i tried to perform something like u described with the 10.10 version it just wouldnt work. so use 10.04 live cd. boot into it, open a terminal and type: sudo gparted. that will start the partitioner in which u can just click on a linux partition and click on edit, and then resize it to whatever size u can, and in the end click on apply.
second scenario, as u said, u may want to delete windows completely , so in this case instead of resizing your linux partition, in gparted, u just click on windows ntfs partition and choose delete, it will show u the new free space that u got, after that click on the linux partition and choose "edit" and expand it to a maximum allowable size, click on apply to perform the changes.
reboot and boot into your linux, if u did the "second scenario" and deleted windows, dont forget to run "sudo update-grub" to remove windows from grub menu configuration.

i hope i helped u. if u have any questions, send me a message on my youtube channel or post here.

---

### Post by mike555 on 2011-04-09
Looks like you installed a Wubi install , gparted won't help that ........  I suggest you do a partition install.

---

### Post by vanadium on 2011-04-09
Just keep your data on your Windows partitions. Then you do not need more than 6-7 GB for the Ubuntu installation.

Replace the Documents, Music, etc. folders in your Ubuntu by symbolic links to these data on your Windows partitions. After that, you will access your data on the Win partitions as conveniently as before.

A symbolic link can be created by dragging a folder or file while you keep the Ctrl+Shift keys pressed, then releasing the mouse button.

---

### Post by mubtasim123 on 2011-04-09
Thanks guys it was really helpful :D

---


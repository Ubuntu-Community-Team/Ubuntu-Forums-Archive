---
title: "Grsync and permissions"
date: 2012-06-24
forum: General Help
---

### Post by DeMus on 2012-06-24
Hi, I use Kubuntu 12.04 and at the moment I have a problem with the back-up program Grsync.
I used to have an external hard-disk connected to one of my computers, the one which is using Grsync. That way I could make back-ups from this, and also the other computers, including on Windows 7 computer.
Now, I have connected the external disk to the USB connection on my router, giving it an IP-address (the routers address) so every computer can reach the disk all the time. I don't need to take it up- and downstairs to connect it to a computer.
At the moment I can address the disk,  make folders on it, copy files to it. What I can't do it use Grsync to back-up my data files. I get an permission denies error on the files. Strange thing is, Grsync does make the folders on the external disk, like Documents, Downloads, etc. Files are not copied.
Who can help me to set these things straight? I know it must be something about permissions, but how and why is beyond me.
Please help. Thank you.

---

### Post by habana on 2012-06-24
As I am sure you know, grsync is a GUI for rsync. Check out the rsync man page for all the available options. If you hover your mouse over the tickboxes in grsync, you will see which option they refer to. I found the -x option prevented my files being copied. The options I ended up with were -rntvL

I hope that helps

---

### Post by papibe on 2012-06-25
Hi DeMus.

G/Rsync works over:
[LIST]
[*]Local directories.
[*]Remote shares that are explicitly mounted.
[*]Remote filesystems over ssh.
[*]Remote filesystems through an rsync daemon.
[/LIST]
How are you accessing the external hard disk?

Regards.

---

### Post by DeMus on 2012-06-25
> **papibe said:**
> Hi DeMus.

G/Rsync works over:
[LIST]
[*]Local directories.
[*]Remote shares that are explicitly mounted.
[*]Remote filesystems over ssh.
[*]Remote filesystems through an rsync daemon.
[/LIST]
How are you accessing the external hard disk?

Regards.

I mounted the disk in fstab, I used this line for it:
```
//192.168.1.1/Back-Up         /home/jan/Back-Up    cifs    rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```
From within my filemanager (Dolphin) I can do everything, no problem whatsoever.
It's just when I use Grsync that I get the permission deny errors.
Thank you for your help.

---

### Post by DeMus on 2012-06-25
> **habana said:**
> As I am sure you know, grsync is a GUI for rsync. Check out the rsync man page for all the available options. If you hover your mouse over the tickboxes in grsync, you will see which option they refer to. I found the -x option prevented my files being copied. The options I ended up with were -rntvL

I hope that helps

Hi Habana, yes I know how to use Grsync, have been using it for years, but with a locally connected drive. I's just that niw, with the disk connected to the router I get these permission deny errors.

---

### Post by DeMus on 2012-06-25
At the moment I have no idea what happened, but I can make contact to my external drive again using Grsync. Maybe I just had to restart the computer for whatever reason.

---


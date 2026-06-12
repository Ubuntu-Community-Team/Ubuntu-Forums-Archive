---
title: "Can I  make a bootable USB thumb drive with a Windows ISO file? I'm using Ubuntu now."
date: 2011-10-15
forum: General Help
---

### Post by Gogglez on 2011-10-15
I have tried using UNetbootin but it didn't work. I've read that it does work so maybe I just did it wrong. I used UNetbootin to put a LINUX ISO file on a thumb drive. Now I need the reverse. I'm using Linux and want to install Windows. Does anyone know how?

---

### Post by Blaqksheep on 2011-10-15
Heh, this is the one thing in the world I can recall how to do easier via DOS than shell.

Here's one way you can try it.  Mount the ISO, then open your terminal.

```
cp /directory of mounted ISO/ /mounted flash drive/
```


I had to put the Windows 8 Dev build on a flash drive so I used a similar command in DOS.

Good luck!  If it doesn't work or you get confused let me know.


[EDIT]DOH!  If you're going that route, unless it tells you that you don't have access or if this way doesn't work, just mount both and drag/drop.  Sorry about trying to complicate it.

---

### Post by Gogglez on 2011-10-15
> **Blaqksheep said:**
> Heh, this is the one thing in the world I can recall how to do easier via DOS than shell.

Here's one way you can try it.  Mount the ISO, then open your terminal.

```
cp /directory of mounted ISO/ /mounted flash drive/
```
I had to put the Windows 8 Dev build on a flash drive so I used a similar command in DOS.

Good luck!  If it doesn't work or you get confused let me know.


[EDIT]DOH!  If you're going that route, unless it tells you that you don't have access or if this way doesn't work, just mount both and drag/drop.  Sorry about trying to complicate it.
ok, so i unmounted the usb drive. then i typed the command  "sudo mount /dev/sdb1 /mnt/usb-drive" in order to mount it. i've mounted it there before. then i used the software gmount-iso to mount the iso file to a folder. the contents are in the folder and it also created a icon with a disk on my desktop. i guess i ignore that disk icon on my desktop because i think it's extra since i told gmount-iso to mount it in the folder.

now what would the command be according to the code you want me to type in? the directory of the mounted usb i think can be told by the command i provided above. and the folder where the iso is mounted, is on my desktop, in a folder called "the mounted iso"

thanks

---


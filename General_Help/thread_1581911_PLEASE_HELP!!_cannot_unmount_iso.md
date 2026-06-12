---
title: "PLEASE HELP!! cannot unmount iso"
date: 2010-09-25
forum: General Help
---

### Post by FrolicsomeGaiety on 2010-09-25
[SIZE=2]So,  the CD drive on my laptop doesn't work. I'm trying to install a 5 disk  (iso) game (Baldur's Gate II). I've tried Gmount iso and the command  line to mount CD1's iso (successfully), Wine prompts the install.exe  just fine, but when then the install wizard prompts me for CD2 it is  impossible for me to unmount it- in either Gmount or command line. When I  click "unmount" in Gmount it simply ignores my click... CD1's info  stays stubbornly in my virtual drive (media/cd) until I exit the install  wizard- then, it mounts and unmounts fine. But that doesn't exactly  help me install the game.

Attempting to unmount via right-click gives the error message "umount:  /media/cd is not in the fstab (and you are not root)".  "sudo mount -t  iso9660 -o loop /home/frolicsomegaiety/ISO/BG2_CD1.iso /media/cd" is the  command that successfully mounted, but again, "umount media/cd" gives  the same error in the terminal as the error message above: /media/cd is  not in the fstab.[/SIZE] [SIZE=2]

Please help... been digging around for hours.[/SIZE]

---

### Post by Rocket2DMn on 2010-09-25
Did you try using sudo with umount?  You can also try with the -f option to attempt to force the unmount.  Alternatively, I've had success with the -l option (lazy unmount) in the past with different media types.
e.g.
```
sudo umount -l /media/cd
```
or using "/home/frolicsomegaiety/ISO/BG2_CD1.iso" in place of "/media/cd"

---

### Post by WorMzy on 2010-09-25
Like Rocket said, you need to use sudo along with the umount command for it to work.

---

### Post by FrolicsomeGaiety on 2010-09-25
I've used sudo/#, it still says that the device is busy. I would love to just force unmount the iso, but -f still dosen't work: still busy? I don't care that it's busy, I just want to unmount the thing.

---

### Post by FrolicsomeGaiety on 2010-09-25
Replacing media/cd, also, does nothing.. it merely says that the iso in question is not mounted. when it clearly is.

---

### Post by Rocket2DMn on 2010-09-25
The lazy unmount I mentioned before is very useful when it keeps saying the device is busy.  It doesn't always work, but it's worth a shot.

Is there a drive mapping in the Wine configuration utility for /media/cd?  Having this might help with integration between the native mounting and dealing with Wine.

---

### Post by WorMzy on 2010-09-25
If it's refusing to unmount then a quick restart will teach it it's place.

I'm surprised that -f didn't work though.

---

### Post by CharlesA on 2010-09-25
You can always run this:

```
sudo lsof /media/cd
```

TO see what is using it.

---

### Post by FrolicsomeGaiety on 2010-09-25
went back and tried sudo umount -l, and it inexplicably worked when I used Gmount first.. now using terminal and Gmount in harmony together, it seems to work.. thanks so much, guys.

---

### Post by Andrew_P on 2011-10-25
I just experienced the same problem in Ubuntu 10.04.1.  Since the system was complaining that I wasn't root, I started up an instance of Nautilus as root:

```
sudo nautilus
```

The offending ISO image was visible in the root Nautilus.  I right-clicked on it, selected "unmount", and it was gone in both the root and user views of Nautilus, *without having to reboot the system*.  It shouldn't require this sort of trickery, but it's an easy work-around.

---

### Post by WorMzy on 2011-10-25
[SIZE="1"]I don't even rememeber ever posting in this thread..[/SIZE]

> **Andrew_P said:**
> I just experienced the same problem in Ubuntu 10.04.1.  Since the system was complaining that I wasn't root, I started up an instance of Nautilus as root:

```
sudo nautilus
```

The offending ISO image was visible in the root Nautilus.  I right-clicked on it, selected "unmount", and it was gone in both the root and user views of Nautilus, *without having to reboot the system*.  It shouldn't require this sort of trickery, but it's an easy work-around.

Don't use sudo for graphical applications. Use gksu or gksudo. Running a graphical application with sudo can bork the permissions on your home folder and prevent you from using the graphical interface.

But thanks for sharing your solution.

---


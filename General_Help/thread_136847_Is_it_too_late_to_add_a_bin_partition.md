---
title: "Is it too late to add a /bin partition?"
date: 2006-02-26
forum: General Help
---

### Post by LadyDoor on 2006-02-26
So if you've already got a dist intalled and your hard drive all partitioned up for use on it, is it too late to, y'know, take the stuff you normally put in a /bin partition and, y'know, put it into one without losing all the programs installed?

Thanks,
Door

---

### Post by Xian on 2006-02-26
No, you're fine. Just move the contents of that directory over to the newly created partition, and add the mount point to your /etc/fstab. Of course, make a backup before any changes.

---

### Post by Zeroangel on 2006-02-26
Since the original author's question is answered...

My HDD doesn't have enough space to hold all of the files that would normally go into my /home/ folder. So added a second HDD and mounted it at /mnt/mdkhome, where most of my media files are stored. I have all of those subfolders (pictures, music, downloads) symlinked to my /home/dave/ folder, but I would like to integrate them better instead of having to symlink every folder I create.

If I were to do this:

1) copy files (including dotfiles and dotfolders) from /home/dave to /mnt/mdkhome
2) alter the fstab entry of hdb so that the mountpoint is /home/dave

Would I now be able to create folders in /home/dave but have them physically stored on hdb?

And, if I unplugged hdb and tried to start the OS, would I still be able to access my /home/dave folder?

---

### Post by dcstar on 2006-02-27
[QUOTE=Zeroangel]
......
If I were to do this:

1) copy files (including dotfiles and dotfolders) from /home/dave to /mnt/mdkhome
2) alter the fstab entry of hdb so that the mountpoint is /home/dave

Would I now be able to create folders in /home/dave but have them physically stored on hdb?

And, if I unplugged hdb and tried to start the OS, would I still be able to access my /home/dave folder?[/QUOTE]
Yes.

---

### Post by Zeroangel on 2006-02-27
it works :KS

---


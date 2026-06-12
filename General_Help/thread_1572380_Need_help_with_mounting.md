---
title: "Need help with mounting"
date: 2010-09-11
forum: General Help
---

### Post by polardude1983 on 2010-09-11
OK so i have installed a program called gdocsfs. which creates a filesystem for your google docs. So that you can use it as whatever you want. Anyways i got it installed but its saying i need to mount it. and I'm still a newb at linux and mounting

here is what it says 

GDocsFS filesystems is mounted with the regular mount command, or even to be listed in /etc/fstab

gdocsfsmount /path/to/gdocsfs/home /path/of/mount/point [options]
in /etc/fstab, add:
/path/to/gdocsfs/home /path/of/mount/point gdocsfs noauto[,options]

website: [http://www.ohloh.net/p/gdocsfs]("http://www.ohloh.net/p/gdocsfs")

I would like to be able to be access very easily. any help would be appreciated with mounting. Like a just write it out if ya could

---

### Post by polardude1983 on 2010-09-11
Up

---

### Post by Capt_Scribble on 2010-09-11
The /path/of/mount/point can be anywhere you want it. Most people mount stuff in the /mnt folder. So first create the folder it will be mounted in:

```
sudo mkdir /mnt/gdocs
```...or whatever you want to call it. If you want it mounted in your personal home folder then it would be something like

mkdir /home/username/gdocs

(or just do it the graphical way). Then you can mount it to that new folder you created.

---

### Post by polardude1983 on 2010-09-12
I had it working for a little bit but now i got this

[IMG]http://i.imgur.com/GZiem.png[/IMG]

[IMG]http://i.imgur.com/tRnzr.png[/IMG]

---

### Post by Capt_Scribble on 2010-09-12
I think the entry in fstab already makes it auto mount on login; so you don't need to mount it manually again. Why are you trying to unmount it?

---

### Post by Capt_Scribble on 2010-09-12
Have you tried this tool? I think it's compiled for Lucid if that's what you're using.

[http://www.unixmen.com/linux-tutorials/1073-gdocs-mount-gtk-access-and-edit-google-docs-from-nautilus-the-easy-way](http://www.unixmen.com/linux-tutorials/1073-gdocs-mount-gtk-access-and-edit-google-docs-from-nautilus-the-easy-way)

---

### Post by Lateralis on 2010-09-12
The *noauto* at the end of the gdocsfs line means the file system is not automagically mounted at boot.  As for why you can't unmount... I'm not sure.  Try changing the line to:

```

/home/christoph/gfiles/gdocsfs/ /home/christoph/gdocs/ gdocsfs user,noauto 0 0

```

---

### Post by polardude1983 on 2010-09-12
Ok so i get this here 

[IMG]http://i.imgur.com/pwJbH.png[/IMG]

---


---
title: "Auto-mount iso files on startup"
date: 2010-06-30
forum: General Help
---

### Post by A7med on 2010-06-30
Can anybody tell me how to make a script to do that or even a program that auto mounts my iso files . I did my fair amount of search and I found those to work 
```
sudo mount -t iso9660 -o loop "/somewhere.iso1" "/media/iso"
sudo mount -t iso9660 -o loop "/somewhere.iso2" "/media/iso2"

```
But I have to type them each time I login and I tried Gmount iso and other tools but They have the same problem that everything is cleared when I reboot .

Also I did some search and I found out I have to make a script and paste it in etc/init.d and other steps but I can't do that because It's a read only folder . Can anybody help because I am a total linux noob ?

---

### Post by pedro_orange on 2010-06-30
Have you tried adding the filesystems to the /etc/fstab file?

---

### Post by A7med on 2010-06-30
No , Also that file is read only . should I edit it from Terminal ? And How to edit it properly ?

---

### Post by pedro_orange on 2010-06-30
If you're not sure how to edit the file, use the application pysdm

```
sudo apt-get install pysdm
```

It's GUI /etc/fstab editor. Should make things easier for you.

---

### Post by A7med on 2010-06-30
I don't see how can this help to automount iso files !?

---

### Post by A7med on 2010-06-30
Any Help ?

---

### Post by Morbius1 on 2010-06-30
Try this:

Open a Terminal and type:
```
/usr/lib/gvfs/gvfsd-archive file=/path-to-iso
```2 things should happen:

(1) An mount icon to the ISO should appear on your desktop
(2) An actual mount point is created at /home/username/.gvfs/iso-name

If this is what you want you can then add it to your startup applications:
Preferences > Startup Applications

[COLOR=Blue]EDIT: I keep making the same mistake in this forum. I just noticed that you using xububntu. I have no idea if this works with anything other than Gnome. Sorry.[/COLOR]

---


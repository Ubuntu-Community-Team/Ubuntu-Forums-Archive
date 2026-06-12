---
title: "Oops - unmountable drive, please help!"
date: 2009-08-21
forum: General Help
---

### Post by mbuehl on 2009-08-21
So I was trying to set my mount options so that I would have permissions on this NTFS drive I've got set as /dev/hdb ... to do so, I mounted the drive, right clicked it off my desktop, and added a line of (incorrect) code to the mount options field.

Now, when I attempt to mount it via the Places drop-down, it gives me an error saying invalid mount options. Other than mounting it from console to /media, is there a way I can remove that line of text? I can't seem to get back in to the properties of it without first mounting it.

Thanks in advance!

---

### Post by aldimond on 2009-08-21
I don't have Gnome here so I'm just stabbing in the dark, but traditionally that kind of info is stored in /etc/fstab.  You'll need to edit the file with root permissions, and be very careful not to touch any entries for anything else.  Then again, Gnome might store this info somewhere else, and there might be a better way to get at it, so unless nobody else replies to this don't go poking around your /etc/fstab.

---

### Post by okmat on 2009-08-21
you should edit your fstab file

```
sudo gedit /etc/fstab
```

remove the line you originaly added and add a line like this:

```
/dev/sda1 /media/vista ntfs-3g auto 0 0
```

in this case /media/vista is the directory the hard drive will be mounted to (it has to exist), and sda1 is the name of the drive to mount, you can see a listing of all your hard drives by tying

```
sudo fdisk -l
```

Check my guide on mounting drives [here]("http://www.redmezzanine.com/?p=357&lang=en")

---


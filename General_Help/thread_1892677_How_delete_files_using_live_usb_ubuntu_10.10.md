---
title: "How delete files using live usb ubuntu 10.10"
date: 2011-12-08
forum: General Help
---

### Post by GlennW on 2011-12-08
My nephew dropped off the laptop he uses for school saying that it doesn't get past the login screen. True enough. It also says that the Gnome Power Management can't load (or something like that) and refuses to go any further. 

The laptop is an older HP with a relatively small hd, in this case only 20GB. Needless to say, for kids these days that's just not enough. I suspected that the drive was completely full. I ran the live usb (laptop runs ubuntu 10.10) and used df -h to determine that the drive is truly full.

My question is how can I remove enough files via the live usb so that it will boot up? After that there will be some serious house cleaning!

Thanks.

---

### Post by duke.tim on 2011-12-08
```
rm -r
``` to remove folders
```
rm /file/location
``` to remove files

or use nautilus and point and click away!

I'd start by cleaning up some temporary folders like

home/username/.cache/
home/username/.mozilla/firefox/firefoxprofilename/cache
/tmp

Just delete the files not the folders.

And then if you need more space video's, pictures, and music.

---

### Post by newbie-user on 2011-12-08
Use the live usb and transfer all the documents, music, and videos to an external drive, then sudo rm -rf the contents of those folders on the laptop.

---

### Post by Lars Noodén on 2011-12-08
The files in [font=Courier New]/var/cache/apt/archives[/font] and [font=Courier New]/var/cache/apt/archives/partial[/font] take up a lot of space and can be safely removed.

---

### Post by GlennW on 2011-12-08
Thanks for the info. Hopefully once I pull some of the cruft off boot up will resume as per normal.

---


---
title: "obtaining permissions on a different HD"
date: 2010-04-04
forum: General Help
---

### Post by excbuntu on 2010-04-04
my sister's easy peasy ubuntu netbook crapped out. i took out the hard drive and hooked it up to my desktop. on my desktop, i booted into ubuntu via usb and browsed for files to salvage. certain folders say i don't "have the permissions necessary to view the contents."

how can i obtain these permissions? it's been a while since i've dealt with linux. thanks in advance.

---

### Post by NightwishFan on 2010-04-04
Open the files using a root nautilus. [COLOR="DarkRed"]Be careful, you are able to delete your own system files by accident while doing this. Only browse the drive in question and not your own root drive[/COLOR]

Press alt+f2 and type:
```
gksudo nautilus
```

---

### Post by excbuntu on 2010-04-04
thank you so much. also, i'm using the find command to find all .JPG files in the system.

"find / -name \*.JPG"

how can i change this command to output the results into a file?

---

### Post by NightwishFan on 2010-04-04
Pipe it, which is easy. Your above command however will not work unless you are actually using the system in question. You need to change the directory to the mounted device alone, and not use "/". This will find every jpg in the entire system, not just user ones. Replace "/media/device" with the mounted device.
```
cd /media/device/
```

Then your own find command, and append the pipe I added. Note that Linux is case sensitive, so searching for .JpG is different than .jpg. Replace my location with the one you want, but the default of this command is to place the results on the desktop.
```
find .jpg > ~/Desktop/SearchResults.txt
```

Any questions first?

---

### Post by excbuntu on 2010-04-04
i'm using a usb linux boot. all mounted disks end up in /media/. therefore the "find /" command searches the entire system, including mounted devices.

your piping command was successful. again, thank you so much!!

specifically, i used "find / -iname \*.JPG >> outputfile"

the iname makes a difference by specifying that the jpg is not case sensitive, and that it's included anywhere in the name.

---

### Post by NightwishFan on 2010-04-04
> **excbuntu said:**
> the iname makes a difference by specifying that the jpg is not case sensitive, and that it's included anywhere in the name.

I never knew that. Thanks. :lolflag:

I did figure as much considering how you made a point of it looking like that but I decided to add a warning just in case. Glad it worked.

---


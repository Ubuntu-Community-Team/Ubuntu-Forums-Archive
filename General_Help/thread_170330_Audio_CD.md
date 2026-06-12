---
title: "Audio CD"
date: 2006-05-04
forum: General Help
---

### Post by mviroli on 2006-05-04
Hi,

I have two probably related problems:
1) When I insert a CD my UBUNTU does not automatically mount it. I have to do it myself with command "mount /mnt/cdrom".
2) When I insert an audio CD mounting does not work (is it right?), and moreover, programs that should be able to read it like totem or juicer does not.

Any idea?
Thanx.

---

### Post by harishg on 2006-05-04
what kind of an audio cd is it.I never had any problems with mounting cd roms and playing the files.

---

### Post by mviroli on 2006-05-05
It does this with any audio cd.
The problem is my item 1) above, I guess.
Why I have to explicitly mount CDs, and my UBUNTU doesn't do this automatically?
Why the CD icon does not appears in my desktop as soon as I insert a CD??

---

### Post by public_void on 2006-05-05
Check System -> Preferences -> Removable Drives and Media under "Storage" that "Mount removable media when inserted" is checked.

---

### Post by mviroli on 2006-05-05
It is checked!!!

---

### Post by az on 2006-05-05
[QUOTE=mviroli]. I have to do it myself with command "mount /mnt/cdrom".
[/QUOTE]


Insert any cd and go to Computer in nautilus and right-click on the cdrom icon.  Tell it to mount.  Does that work?  Try both data and audio cds.

---

### Post by 3rdalbum on 2006-05-05
In reply to Question 2, have you tried using Grip to attempt playback of the audio CD? I've found it works where other programs won't.

EDIT: You can double-click the CDROM drive icon in the above poster's instructions; it'll attempt to mount the CD.

Just had a thought: Is your CD-ROM drive in the fstab file?

---

### Post by mviroli on 2006-05-05
[QUOTE=azz]Insert any cd and go to Computer in nautilus and right-click on the cdrom icon.  Tell it to mount.  Does that work?  Try both data and audio cds.[/QUOTE]

With both an audio CD and data CD it reports an error, that is:
"Error: given UDI is not a mountable volume"

I can mount a data CD by command:
"mount /media/cdrom"
with the following line in fstab:
"/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0"

---

### Post by mviroli on 2006-05-05
[QUOTE=3rdalbum]In reply to Question 2, have you tried using Grip to attempt playback of the audio CD? I've found it works where other programs won't.
[/QUOTE]

I tried with the "CD player" and it worked...
Actually, it reads the tracks but when I playback I here no sound.. Is this a related problem??
(Things are getting complicated..)

---


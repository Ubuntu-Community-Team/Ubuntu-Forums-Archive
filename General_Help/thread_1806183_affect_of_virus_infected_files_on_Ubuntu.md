---
title: "affect of virus infected files on Ubuntu ?"
date: 2011-07-17
forum: General Help
---

### Post by wpshooter on 2011-07-17
I have some jpeg (picture files, etc.) that were saved off of a friends old virus laden M/S windows computer.  I am switching him to Ubuntu.  The files may be infected but I have not come up with a good way to scan them yet.  They are on an old hard drive (with no O/S) and right now I don't have a M/S windows based computer to use to scan them.

If I place these files on his new Ubuntu O/S computer **_WITHOUT_** first checking them for viruses and if it turns out that they are infected with viruses, will those viruses possibly harm other data or O/S files on the Ubuntu computer ?  

Or will those files only possibly be harmful if passed back to another M/S windows O/S computer ?

Thanks.

---

### Post by Timmer1240 on 2011-07-17
Will have zero effect on Ubuntu but could harm a windows machine if passed on to windows.

---

### Post by gandaran on 2011-07-17
the windows virus infected files will just sit there where you put them, they wont run on linux unless you try running them with wine but even with wine there wont be any significant damage or any damage at all to the system.

---

### Post by rickytikki on 2011-07-17
Ubuntu will not be damaged but let me introduce you to clam tk its an anti virus for ubuntu and its real good! thats what i use to get rid of windows viruses. it should be in the ubuntu software center. or here [http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html) the tutorial

---

### Post by wpshooter on 2011-07-17
> **rickytikki said:**
> Ubuntu will not be damaged but let me introduce you to clam tk its an anti virus for ubuntu and its real good! thats what i use to get rid of windows viruses. it should be in the ubuntu software center. or here [http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html) the tutorial

Ricky:

Is this a program that has a GUI or is it run from the terminal ?

Can this be ran as JUST an on demand scan, I DON'T want a resident scanner ?

Will I be able to add the old hard drive to the Ubuntu system and scan **_JUST the files on that drive_** before I copy them over to the Ubuntu home directory and can this program be easily uninstalled from Ubuntu once I am finished scanning the old hard drive ?

Thanks.

---

### Post by bodhi.zazen on 2011-07-17
Some windows viruses reportedly run in wine.

---

### Post by Frogs Hair on 2011-07-17
A virus made to attack a Widows .exe cannot run in Linux without the help of an emulator like Wine . If this person is planning to share these photos it would be best to deal with the possibility of infected files while windows is still installed . [http://download.cnet.com/Malwarebytes-Anti-Malware/3000-8022_4-10804572.html?part=dl-10804572&subj=dl&tag=button](http://download.cnet.com/Malwarebytes-Anti-Malware/3000-8022_4-10804572.html?part=dl-10804572&subj=dl&tag=button)

---

### Post by HiImTye on 2011-07-17
there are viruses that run in wine (or so I hear) but they cannot affect system files or the files of other users (unless they are on a shared resource). this only matters if you use WINE on those files (which means they would need to be in a place you have a windows drive linked to, i.e. your home folder and you would need to explicitly load them, every time as WINE does not have an 'on startup' loading section)

that said, if you do get your home folder compromised (unlikely) all you would need to do is create a new user or use an existing one (you would still have your shared resources compromised, if they were)

there are various options for AV under linux. I would recommend clam (I often hear it is the best) but others are OK such as Avast! or Norton (but I wouldn't pay money just to scan for Windows viri - which won't affect you unless you are downloading programs to use under WINE)

note: for some reason WINE exposes the entire file system to some programs that have mac ports (for instance, photoshop) which could expose files not inside the drives you have specified for WINE (but system files require additional permissions to access so it still isn't much of a security risk)

---

### Post by rickytikki on 2011-07-17
clam can be run from terminal but comes with a gui and does not keep running in the background. you can search individual files or just mounted partitions.

---

### Post by wpshooter on 2011-07-17
> **rickytikki said:**
> clam can be run from terminal but comes with a gui and does not keep running in the background. you can search individual files or just mounted partitions.

Thanks for everyone's advice.

---

### Post by rickytikki on 2011-07-17
> **wpshooter said:**
> Ricky:

Is this a program that has a GUI or is it run from the terminal ?

Can this be ran as JUST an on demand scan, I DON'T want a resident scanner ?

Will I be able to add the old hard drive to the Ubuntu system and scan **_JUST the files on that drive_** before I copy them over to the Ubuntu home directory and can this program be easily uninstalled from Ubuntu once I am finished scanning the old hard drive ?

Thanks.

yes you can do all these things you ask. i actually use a live cd when im fixing a computer for a client install it and run it without ever touching windows or loosing important documents the client might have or want. clamtjk is a powerfull antivirus i would say its better than all those pos software like norton or avast(what a joke).

---

### Post by flemur13013 on 2011-07-17
> **bodhi.zazen said:**
> Some windows viruses reportedly run in wine.

Lots of windows programs will run on a Linux system w/o wine, including fairly complicated programs like irfanview and foobar2000 - even Adobe Audition (I just checked w/"portable" install) -  so it's safe to assume that some viruses would also.

This jerk shows how to "Hide your virus file into image jpg 2nd Tutorial":
[http://itshinepk.blogspot.com/2011/03/hide-your-virus-file-into-image-jpg-2nd.html](http://itshinepk.blogspot.com/2011/03/hide-your-virus-file-into-image-jpg-2nd.html)
It's worth reading so you know what you're dealing with.

---

### Post by DawieS on 2011-07-17
> **wpshooter said:**
> 
Is this a program that has a GUI or is it run from the terminal ?
Yes, the scanner is **clamav**, and the GUI is **clamtk**. Both have to be installed (with their dependencies).
> **wpshooter said:**
> 
Can this be ran as JUST an on demand scan, I DON'T want a resident scanner ?
Yes, although I uninstall it after use, since I keep copies in my Local Repository. It has a daemon that continuously wants to update virus definitions, and I don't use it that often (only when helping out a friend).
> **wpshooter said:**
> 
Will I be able to add the old hard drive to the Ubuntu system and scan **_JUST the files on that drive_** before I copy them over to the Ubuntu home directory and can this program be easily uninstalled from Ubuntu once I am finished scanning the old hard drive ?
Yes, you can browse to a drive, or sub-folder on that drive. Uninstall is easy with Synaptic.

---

### Post by HiImTye on 2011-07-17
> **flemur13013 said:**
> Lots of windows programs will run on a Linux system w/o wine, including fairly complicated programs like irfanview and foobar2000 - even Adobe Audition (I just checked w/"portable" install) -  so it's safe to assume that some viruses would also.

This jerk shows how to "Hide your virus file into image jpg 2nd Tutorial":
[http://itshinepk.blogspot.com/2011/03/hide-your-virus-file-into-image-jpg-2nd.html](http://itshinepk.blogspot.com/2011/03/hide-your-virus-file-into-image-jpg-2nd.html)
It's worth reading so you know what you're dealing with.

that's not an image file, that's an executable that they changed the icon for to look like a default icon for some operating system for an image file and renamed to a .com instead of a .exe

---

### Post by wpshooter on 2011-07-17
What do the RED circles in status columns for GUI version & Virus definitions mean ?

Thanks.

---

### Post by HiImTye on 2011-07-17
it's been a while since Ive used clam but I believe if you hover over them it will tell you

---

### Post by DawieS on 2011-07-17
> **wpshooter said:**
> What do the RED circles in status columns for GUI version & Virus definitions mean ?

It means you have to first update the GUI, and also the virus definitions.

---

### Post by flemur13013 on 2011-07-17
A couple of ideas:

1 - Run "strings filename" on the file(s) and see if you get anything suspicious, like "binder".  I get the EXIF data, if present, and short junk strings like "kFI@n].#" from a normal JPG file. 

2 - You could batch-convert the files with some graphics software.  This will expand the file into an image and then recompress it from the image data. It's not completely lossless for JPG files, but the difference usually isn't noticeable.  If you're extra paranoid, convert them to a lossless, uncompressed format (e.g. BMP) where the file size on disk should match the image size (if the images are the same size the files will be the same size - but you'll lose the EXIF data) and then convert those files to nice clean JPG files.

---

### Post by bodhi.zazen on 2011-07-17
> **HiImTye said:**
> there are viruses that run in wine (or so I hear) but they cannot affect system files or the files of other users (unless they are on a shared resource).

They most certainly can, if you run wine as root.

Most windows viruses do not run well mind you.

[http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)

---

### Post by HiImTye on 2011-07-17
> **bodhi.zazen said:**
> They most certainly can, if you run wine as root.

Most windows viruses do not run well mind you.

[http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)
that's true but only someone wanting to lose their entire system would actually do that

---

### Post by bodhi.zazen on 2011-07-17
> **HiImTye said:**
> that's true but only someone wanting to lose their entire system would actually do that

Or users new to Ubuntu / Linux who do not know better.

---

### Post by HiImTye on 2011-07-17
> **bodhi.zazen said:**
> Or users new to Ubuntu / Linux who do not know better.
true [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---


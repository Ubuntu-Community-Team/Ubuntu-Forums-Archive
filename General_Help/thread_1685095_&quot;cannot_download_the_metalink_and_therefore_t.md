---
title: "&quot;cannot download the metalink and therefore the iso&quot;"
date: 2011-02-10
forum: General Help
---

### Post by khoraski on 2011-02-10
I got this error while trying to use wubi.exe 

I am posting short and quickly 'cause I'm tired of things not working and not being able to find answers! 

HELP!

BTW I downloaded the Ubuntu 10.10 64bit edition and followed the steps to put it on my thumbdrive. I can boot Ubuntu with my thumbdrive. The WUBI.EXE is part of the files on the thumbdrive.

---

### Post by bcbc on 2011-02-10
there is a little issue with thumb drives. Wubi has some code that tries to prevent people installing from a DVD image - it checks whether the installation 'image' is > 900MB and rejects it. So if you created your thumb drive and you used a partition > 900MB it will fail wubi.

I've seen mention of a parameter --force command line option (but i'm not sure if that's enabled in the current release).

So you can either, copy that wubi.exe to a folder on your computer, and place the original CD image you downloaded (the .iso file) in the same folder and run it from there. (Recommended)

Or try supplying the --force command line argument to install it from the USB. (create shortcut to the wubi.exe from the USB on your desktop. Right click, Properties, and change the Target so it looks like "x:\wubi.exe" --force 
If you decide to try the last method and it works please let me know.

PS also read this: [https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)

---

### Post by AARON_73 on 2011-12-20
The (Recommended) worked like a charm on hp-110 mini netbook with XP.
Hope this works for you as well.:guitar:

---


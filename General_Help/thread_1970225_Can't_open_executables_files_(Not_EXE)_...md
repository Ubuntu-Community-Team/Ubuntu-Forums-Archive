---
title: "Can't open executables files (Not EXE) .."
date: 2012-04-30
forum: General Help
---

### Post by GameX2 on 2012-04-30
Hi there,


I did another fresh install of 12.04 LTS; easiest install ever, fantastic, seriously.  10 minutes, I've got all my 50 programs! :O

I however experienced an unusual problem: I can't seems to open executables files.  Not Windows programs (With Wine, of course), but  you know when you go to the proprieties of the file and check "Allow executing this file as a program" ?

Just for testing purposes, here a file that won't work at all; Kega Fusion for Linux:
[http://www.eidolons-inn.net/tiki-download_file.php?fileId=572](http://www.eidolons-inn.net/tiki-download_file.php?fileId=572)

If I extract the archive anywhere and run "Fusion" (No extension, the diamond icon), it does nothing.  Normally, it would have told me if I would want to launch the file, or show it in Gedit (Like it did in my older install of Gedit)..

I really have no idea of what's going on! :(
And that's not a problem with Fusion alone, it happen on every executables files: an older version of Blender, Celtx, etc.  All of those worked on my older install on 12.04 LTS.


Thanks for the help!

---

### Post by papibe on 2012-04-30
Hi GameX2.

That is not an executable, but a compress directory (very much like a rar or a 7z file). Right click on it and select 'Extract Here'. That will create a new directory with the files contents.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by GameX2 on 2012-04-30
Hi,

Thanks for the reply.
The file I've included the link in my post was for an example only; this is definitely an archive, so I extract it.  My problem is that when I try to run the file "Fusion" with no extension (diamond icon), instead on launching the program like it normally does, nothing happen.  Not even an error message.

(Hey, I see you're from Dallas! ;)  Over the years, I've developped that very akwards interest about Texas.  I mean, really akwards.  Well, I guess that's normal, an ex-friend I knew moved to Texas, so.) 

Thanks for the help!

---

### Post by beboylips on 2012-04-30
Try running the executable from the terminal.

Open Terminal
cd into the directory (ex: cd ~/programs/)
./executable_name

see what output it gives.

---

### Post by GameX2 on 2012-05-01
Never mind.  Fusion work, but when I try to run Blender, I get this:
```
./blender: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory
```


```
./Fusion: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

EDIT: Got it!
Installed "ia32-libs-gtk" (sudo apt-get install), which took like 140 MB, but it now work like normal!
Odd that it wasn't installed already!
Thanks :)

---

### Post by GameX2 on 2012-05-01
I did another fresh install, and the first thing I do right after reboot, I try to start Blender:

```

cd Blender
./blender
error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory
```

Uh.  Again?
I install the updates, I reboot, try again..

Still doesn't work! :S

---

### Post by GameX2 on 2012-05-01
Can anyone help?


Thanks :)

---


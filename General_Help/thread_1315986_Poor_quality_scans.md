---
title: "Poor quality scans"
date: 2009-11-05
forum: General Help
---

### Post by motorcity909 on 2009-11-05
Hi all

I've been happily using my Mustek 1248 flatbed scanner for the past few months, thanks to the driver installation info on this [thread]("http://ubuntuforums.org/showthread.php?t=352342").

Recently, the quality of the scans has dropped.  The main thing I scan is my wife's timesheets and scans were excellent quality - like digital pictures of the document and you could differentiate between black or blue ink. 

Now the scans are just poor quality black & white.

Xsane settings are attached.  

I wish I could post some old and current examples of the scans but they've got personal info on them.

I've tried the scanner on an XP machine and the image was fine.

Is there a way to completely uninstall the scanner and then reinstall it and it's drivers?

Thanks as always.

---

### Post by Supersquirrel on 2009-11-05
thats because your using ubuntu......

---

### Post by motorcity909 on 2009-11-05
Er, okay, but as I said it's been working fine and scan quality has been excellent.

---

### Post by coffeecat on 2009-11-05
Hi there.

First - ignore Supersquirrel. If you check his recent posts he has been trolling silly comments all over the forum and has asked for his account to be deactivated - which it has. I guess he is going off in a huff.

Anyway...

I'm afraid I'm a bit ignorant of the inner workings of Xsane and scanning. It just works for me with my HP multi-function machine, for which I am thankful. But I do have a suggestion.

It's interesting that in that thread you linked, some posters were complaining of poor colour, but you were getting good results - but no more. Which suggests that some configurations have become corrupted. If you look in your home folder, click on View > show hidden files (or simply press ctrl-H), you'll see all your hidden folders and files. They are all prefixed with a '.', which is what makes them hidden.

Have a look for the folder '.sane'. That is only created when you first use xsane. Make sure xsane is closed and try renaming .sane to .sane.backup (so you can get it back if necessary). Now re-open xsane with your scanner on and plugged in. Xsane will create a new .sane folder. You will lose your personalised settings but, hopefully, you will get your good quality scans back.

Other than that, I don't know.

---

### Post by motorcity909 on 2009-11-06
Thanks coffeecat.  Unfortunately that hasn't worked but the scanner is working fine within XP which I run in Virtualbox, so at least I'm not scanner-less.

Thanks again for your reply. :p

---


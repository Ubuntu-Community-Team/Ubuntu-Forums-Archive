---
title: "Compiling Gimp 2.8"
date: 2012-07-10
forum: General Help
---

### Post by cosners on 2012-07-10
Since the repos only have Gimp 2.6 or so and later versions of it have single-window mode, I decided to try compiling a more recent version of it myself. I followed the instructions here:

[http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu)

More or less to the letter. However, after reaching the last step, it told me that it didn't find the TIFF library. I went on the website and found:

[http://www.gimp.org/downloads/install_help.html](http://www.gimp.org/downloads/install_help.html)

And successfully compiled the tiff library. However, now it's telling me that it can't find the jpeg library and I can't find

[ftp://ftp.gimp.org/pub/gimp/libs/](ftp://ftp.gimp.org/pub/gimp/libs/)

the libs directory in the FTP. The other FTP listed also doesn't work. Where do I find the jpeg library so I can compile and install it?

---

### Post by Rodney9 on 2012-07-10
[http://askubuntu.com/questions/134035/how-do-i-get-gimp-2-8](http://askubuntu.com/questions/134035/how-do-i-get-gimp-2-8)

Rodney

---

### Post by cosners on 2012-07-10
[IMG]http://s10.postimage.org/4ryxdl1af/knownissues.png[/IMG]
I wanted to avoid that, seeing as to how apparently there are known issues even in 12.04. However, it seems to be the only way.

EDIT: Well, it works but apparently it still doesn't have support for multiple filetypes. Marking this solved for now since my original question was somewhat answered.

EDIT 2: Everything is working.

---


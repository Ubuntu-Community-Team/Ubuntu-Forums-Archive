---
title: "Error in GXSTRT: Unable to connect to X server"
date: 2006-03-09
forum: General Help
---

### Post by neilm on 2006-03-09
Hello boys and girls

I'm trying to run an application on a remote machine, like so:

$ xhost +<remotemachine>
$ ssh <remotemachine>
> setenv DISPLAY <localmachine>:0.0
> <runapplication>

but I get the error:

Error in GXSTRT: Unable to connect to X server

I saw a fix for Fedora at [http://www.linuxquestions.org/questions/showthread.php?t=150831](http://www.linuxquestions.org/questions/showthread.php?t=150831), but does anyone have a solution for Breezy?

thanks

---


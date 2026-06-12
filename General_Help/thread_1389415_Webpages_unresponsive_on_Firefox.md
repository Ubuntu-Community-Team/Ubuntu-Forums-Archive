---
title: "Webpages unresponsive on Firefox"
date: 2010-01-24
forum: General Help
---

### Post by danp824 on 2010-01-24
Hello... I've got an issue with Firefox that prevents me from using some applications on webpages.

Most webpages work fine, but every now and then I run into one with some kind of complex script, or application, on the page, and I can't click the mouse anywhere.  I can move the mouse, but the application is completely unresponsive to it.  The page doesn't freeze - and I can click on things OUTSIDE the application - but the application on the page is unresponsive.

Examples include:

-The login page for my bank (very important!)
-Certain videos on Youtube won't let me play, pause, adjust the volume, move the play cursor, or click related videos - basically anything in the movie window is off limits
-Other websites like Weather.com, that have "boxes" with applications

Also, Pandora.com often stops and goes blank, and has to be reset for no reason other than the fact that I was on a page with a complex script in ANOTHER TAB on Firefox


Anyone know how to fix this?  I'd appreciate it very much!  Thanks. :D

---

### Post by hwttdz on 2010-01-24
Sounds similar to the problems often experienced when using nsplugin wrapper and 64 bit linux and firefox.  If you do "uname -a" at the command line do you see "x86_64 GNU/Linux" somewhere in there?  

If so there are two solutions, the first which will solve the clicking issue (but possibly not some of the other crashes) is to set gdk_native for flash, you can find instructions for that here: [http://astoryworthtelling.wordpress.com/2009/11/09/cant-click-in-flash-using-ubuntu-9-10-karmic-try-this/](http://astoryworthtelling.wordpress.com/2009/11/09/cant-click-in-flash-using-ubuntu-9-10-karmic-try-this/)

The second which I prefer is to use the adobe beta 64 bit flash, this will likely solve a few more problems.  Instructions for that are here: [http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/](http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/)

On an unrelated note you should pester your bank to have a non-flash login.

---


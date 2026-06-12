---
title: "Keyboard input and Flash"
date: 2009-12-21
forum: General Help
---

### Post by Fillanzea on 2009-12-21
Hi,
 
I'm having trouble with keyboard input in Flash applications. This happens in Pandora ([www.pandora.com]("http://www.pandora.com")) and in Elements The Game ([www.elementsthegame.com]("http://www.elementsthegame.com"))-- I can't input a user name and password to log in. I have tried this in Firefox 3.5 and in the Chrome beta. I can input text only by typing in gedit or another text program, then using the mouse to copy and paste. 
I am using Ubuntu 9.10 and Adobe Flash Player 10. 
 
Thanks for any help.

---

### Post by junapp on 2009-12-21
I had a similar issue which this solved:
[http://heratech.net/blog/sham/cant-click-playpause-flash-youtube-etc-ubuntu](http://heratech.net/blog/sham/cant-click-playpause-flash-youtube-etc-ubuntu)

> 
If you can't click buttons etc on flash videos in Ubuntu here is the fix from: [http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)
I have Ubuntu 9.10 64-bit and it worked for me.  Hit ALT+F2 and enter the below line 
gksudo gedit [COLOR=#339933]/[/COLOR]usr[COLOR=#339933]/[/COLOR]lib[COLOR=#339933]/[/COLOR]nspluginwrapper[COLOR=#339933]/[/COLOR]i386[COLOR=#339933]/[/COLOR]linux[COLOR=#339933]/[/COLOR]npviewer
 Add the following line BEFORE the last line of text [COLOR=#003366]**export**[/COLOR] GDK_NATIVE_WINDOWS[COLOR=#339933]=[/COLOR][COLOR=#CC0000]1[/COLOR]
 Save.
Restart any applications using flash 


---


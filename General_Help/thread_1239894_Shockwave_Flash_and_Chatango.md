---
title: "Shockwave Flash and Chatango"
date: 2009-08-14
forum: General Help
---

### Post by Suff on 2009-08-14
[http://ubuntuforums.org/attachment.php?attachmentid=122791&stc=1&thumb=1&d=1248840041](http://ubuntuforums.org/attachment.php?attachmentid=122791&stc=1&thumb=1&d=1248840041)

My flash player stopped working when I installed 32bit ubuntu over 64bit ubuntu.

Also i have two shockwave flash plugins under plugins Shockwave Flash 9.0 r999 - which works with youtube (but a bit glitchy and doesn't allow fullscreen) and Shockwave Flash 10.0 r32 - which doesn't work with anything.

I'm fairly sure i'm running 32bit on a 64bit computer. Last time it worked fine on a 64bit ubuntu OS after manually creating a plugins folder in the firefox directory.

Help would be great!

---

### Post by Suff on 2009-08-14
I got it to work by:
> 
run synaptic and search for flashplugin-nonfree package.See if it's really installed,if it isn't then install it.If you're in 64 bit,hard luck though. You'll have to search and install gnash and firefox-plugin-gnash to get the flash working.
After i had reinstalled the OS again.

---

### Post by Couto on 2009-08-14
For 64bit I just downloaded the beta Flash Player from Adobe and put it in /.mozilla/plugins

---

### Post by lovinglinux on 2009-08-14
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---


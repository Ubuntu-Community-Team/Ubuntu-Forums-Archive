---
title: "Missing xorg.org file in Ubuntu 11.10. Please Help"
date: 2011-10-25
forum: General Help
---

### Post by atentik on 2011-10-25
I was having some graphic problems after an upgrade from Ubuntu 11.04 to 11.10 and decided to fresh install of the 11.10. But I am still having some graphic issue. Now, my /etc/X11/xorg.org is empty. I tried ```
sudo startx
``` to get the xorg.org file but got [PHP]Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
[/PHP]. I am using lenovo X61 tablet which has intel as a graphic card. How do I get the xorg.org file? Does the Ubuntu 11.10 not suppose to have the xorg.org file? 

Thanks.

---

### Post by 2F4U on 2011-10-25
For some time now Xorg automatically detects its settings and therefore doesn't need a conf file any more. 

[http://manpages.ubuntu.com/manpages/natty/man5/xorg.conf.5.html](http://manpages.ubuntu.com/manpages/natty/man5/xorg.conf.5.html)

---

### Post by Mark Phelps on 2011-10-25
Did you open a terminal on the desktop and THEN attempt to run the command? Of course that won't work -- because it is already running.  If it wasn't, you wouldn't have a desktop.

---

### Post by atentik on 2011-10-25
> **Mark Phelps said:**
> Did you open a terminal on the desktop and THEN attempt to run the command? Of course that won't work -- because it is already running.  If it wasn't, you wouldn't have a desktop.

Yeah, that was what I did. Is there a way to make my intel graphic card useful for the new ubuntu 11.10? From what I heard, with intel graphic, there is no need to download any restricted drivers but this X61 table won't render anything in 3d. Any suggestions?

---

### Post by Favux on 2011-10-25
Hi atentik,

Well if your video chipset has been blacklisted by Unity so that you have to use Unity 2D then there is probably a good reason.  What is it by the way?
```
lspci | grep VGA
```
Are you working from something that tells you if you have a specific xorg.conf, which it shows, you can get Unity working on it?  If so you can simply create an empty xorg.conf file with:
```
gksudo gedit /etc/X11/xorg.conf
```
and paste the contents in it.

---

### Post by atentik on 2011-10-25
> **Favux said:**
> Hi atentik,

Well if your video chipset has been blacklisted by Unity so that you have to use Unity 2D then there is probably a good reason.  What is it by the way?
```
lspci | grep VGA
```
Are you working from something that tells you if you have a specific xorg.conf, which it shows, you can get Unity working on it?  If so you can simply create an empty xorg.conf file with:
```
gksudo gedit /etc/X11/xorg.conf
```
and paste the contents in it.


Nothing specific directed me to the xorg.org file but I know my previous ubuntu versions contained that file and whenever I have some graphic problem, I try editing it and often time the problem is solve but now there is nothing there. Shouldn't it have been automatically generated?
My ```
lspci | grep VGA
``` produces [PHP]00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
[/PHP]
Thanks.

---

### Post by Favux on 2011-10-25
No as mentioned earlier it is not automatically generated anymore because the video configuration is supposed to be automatically handled.  That said for some video you do need a xorg.conf to configure your chipset when the automatic configuration doesn't work the way you want.  And the xorg.conf is not deprecated and you still can use it.  They wanted to reduce or eliminate people fooling with the xorg.conf because so many people broke their X doing that and didn't know how to recover from the command line in the Recovery boot option.

Now that you supplied some keywords a quick google shows that people were having to do things to get the Intel GM965 to work with Compiz.  Don't know if that is the problem because I didn't see anything directly on Oneiric and Unity.  But that's what you need to look for.

---


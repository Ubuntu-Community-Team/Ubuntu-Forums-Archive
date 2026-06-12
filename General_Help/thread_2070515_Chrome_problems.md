---
title: "Chrome problems"
date: 2012-10-12
forum: General Help
---

### Post by mvmacd on 2012-10-12
I have 12.04, and a HP Pavillion DV6-1149WM with AMD A6-3400M cpu and integrated  Radeon HD 6520G graphics.

The problem I'm having happens on both the stable and beta releases of Chrome.

It's kind of hard to explain, but basically, the page won't update.  Like on Facebook, it will load the page, but if I click on a comment box and start typing, nothing updates.  It's still the same picture, but, however, if I zoom out, **THEN** it reflects the changes [the text] I've made.  Similarly if I click on a picture, it loads part of the picture, and part of it is black.  If I zoom in or out, it magically updates everything.

It is only noticeable on some sites, I think it might have something to do with javascript. 

Anyway I'm using the proprietary fglrx graphics drivers, and I even tried using Chrome with a new profile **["--user-data-dir=/tmp/empty-dir/"]**, but it did the same thing..

If anyone has any idea what's going on here I'd sure appreciate it.  Thanks!

---

### Post by S_p_or_t_o on 2012-10-13
/me follows thread

I have the same issue.

youtube is even worse than facebook for me.

update: after further googling, i found it's a flash issue

[Adobe websites gives hints to the issue]("http://get.adobe.com/flashplayer/?no_redirect")
[What to do about it]("http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html")

the trouble is that my flash player is up to date within the repositories
```
Flash (2 files) - Version: 11.4.31.110
Shockwave Flash 11.4 r31
Name:	Shockwave Flash
Description:	Shockwave Flash 11.4 r31
Version:	11.4.31.110
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

```

"NOTE: Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux."

so i wait until chrome fixes pepperflash :(

i found quickly switching tab fixes the pages too lol

update #2: i read somewhere disabling pepper flash fixes the issue, and it seems to work. 
[what i followed to fix it]("http://techlogon.com/2011/08/11/shockwave-flash-crashes-in-google-chrome/")

---

### Post by mvmacd on 2012-10-13
Thanks a million!   Worked for me too.  [At least for now, hopefully it will continue to work correctly from now on.]

Now, what does that mean?  Adobe is abandoning linux?  What in the world?  Why would they do that.  First Android.. Sigh, Adobe has problems.  :mad:

---

### Post by Stefan Björk on 2012-10-16
Yes, thank you. This solved the problem for me as well. This bug has been haunting me for a while, and it seems to get worse for every update of Chrome/PepperFlash. Maybe we should do Google a favour and report it as a bug? :-)

---


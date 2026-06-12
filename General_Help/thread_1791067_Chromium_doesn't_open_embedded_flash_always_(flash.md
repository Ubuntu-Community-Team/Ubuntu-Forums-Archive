---
title: "Chromium doesn't open embedded flash always (flash objects appears black by %50)"
date: 2011-06-26
forum: General Help
---

### Post by Seregwethrin on 2011-06-26
Hi,

By a fifty fifty chance chromium doesn't open embedded flash elements. Audio works but the embedded flash element shows just black.

Refreshing the page fix this again by %50 chance.

But there's no problem with Firefox because I think it uses the Adobe Flash Player (the one in the repo) but Chromium uses the an built-in flash player.

Is there a way to fix this problem? Or a way to disable Chromium's built-in flash player and use the Adobe's flash player?

Thanks

---

### Post by Enigmapond on 2011-06-26
You might try installing the FF add-on "Flash-Aid" which was developed by one of our members, lovinglinux. I had flash problems with Chromium and after running the script in FF it fixed all my issues system-wide.

[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

Hope this helps...it did for me.

Cheers!

---

### Post by Seregwethrin on 2011-06-26
It didn't fixed. Actually I can't get Chromium to recognize libflashplayer.so

It recognizes it's own plugin npwrapper.libflashplayer.so. I even tried to rename libflashplayer.so to npwrapper.libflashplayer.so at the same path and Chromium didn't recognize it too. 

npwrapper.libflashplayer.so details are:
```

Flash - Version: 10.3.181
Shockwave Flash 10.3 r181
Name:	Shockwave Flash
Version:	10.3 r181
Location:	/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
MIME types:	
MIME type	                        Description	       File extensions
application/x-shockwave-flash	Shockwave Flash     .swf
application/futuresplash	        FutureSplash Player  .spl

```

And its video still stucks sometimes.

---

### Post by gandaran on 2011-06-26
> **Seregwethrin said:**
> It didn't fixed. Actually I can't get Chromium to recognize libflashplayer.so

It recognizes it's own plugin npwrapper.libflashplayer.so. I even tried to rename libflashplayer.so to npwrapper.libflashplayer.so at the same path and Chromium didn't recognize it too. 

npwrapper.libflashplayer.so details are:
```

Flash - Version: 10.3.181
Shockwave Flash 10.3 r181
Name:	Shockwave Flash
Version:	10.3 r181
Location:	/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
MIME types:	
MIME type	                        Description	       File extensions
application/x-shockwave-flash	Shockwave Flash     .swf
application/futuresplash	        FutureSplash Player  .spl

```

And its video still stucks sometimes.
chromium doesn't have any built in flash (only google chrome does have it built-in) chromium uses the same system installed flash like firefox and should pick it up fine, I think the problem maybe due to you trying to fix something that you shouldn't or you are running 64-bits ubuntu with the system installed 32-bits flash.

---

### Post by Seregwethrin on 2011-06-26
Yep I found it. It always used 32-bit flash. But it has bugs with Chromium x64.

Now I installed 64-bit flash and it looks fine for now.

---

### Post by gandaran on 2011-06-26
> **Seregwethrin said:**
> Yep I found it. It always used 32-bit flash. But it has bugs with Chromium x64.

Now I installed 64-bit flash and it looks fine for now.
nice, if you got it fixed then to help others mark the thread solved.

---

### Post by Seregwethrin on 2011-06-26
Done.

Also, I installed flashplayer-64 like explained here: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---


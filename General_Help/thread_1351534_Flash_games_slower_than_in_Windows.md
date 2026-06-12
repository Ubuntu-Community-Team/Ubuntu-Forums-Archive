---
title: "Flash games slower than in Windows?"
date: 2009-12-10
forum: General Help
---

### Post by EricDB on 2009-12-10
I dual-boot Ubuntu 9.10 (Karmic) and Win 7, both 64-bit.  There's a flash game I like to play ([http://elementsthegame.com/elementnew.swf](http://elementsthegame.com/elementnew.swf)) that runs perfectly in Win 7, but is slow and choppy under Karmic.  

In about:plugins it shows 

```
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r42

MIME Type 	                Description 	        Suffixes Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	 Yes
application/futuresplash 	FutureSplash Player 	spl 	 Yes
```

Is it normal to have significantly worse flash performance under Linux than under Windows?  Or do I have something set up wrong?

Thanks!

---

### Post by Ylon on 2009-12-10
It looks (mostly) smooth on my old Thinkpad (centrino 1.6Ghz) on Mibility Radeon 7500.


Flash 10 is based to work with direct hardware rendering support; so it may be a "video board" related issue?

How many frames/sec do you get with glxgears?

[alt]+[f2] > xterm glxgears

remember, is not a benchmark: just a testing for basic function of your video boards.

---

### Post by EricDB on 2009-12-10
13970 frames in 5.0 seconds
14002 frames in 5.0 seconds
14120 frames in 5.0 seconds
14362 frames in 5.0 seconds
14464 frames in 5.0 seconds
14196 frames in 5.0 seconds
13942 frames in 5.0 seconds
14184 frames in 5.0 seconds
14192 frames in 5.0 seconds
14329 frames in 5.0 seconds

---

### Post by Ylon on 2009-12-10
Ok, your board is charming fast.


So, looks like that Adobe had the fix for you:

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)


You will get a tar.gz to install (remove the old flash first), are you fine with them?

---

### Post by beetleman64 on 2009-12-10
I'm not big on flash games, but I do find that the likes of BBC iPlayer and YouTube run slower than on the same computer running Windows. I'm guessing that we can probably place the blame at Adobe's door, as I have an ancient Laptop running OpenSolaris which runs YouTube, etc. better than Ubuntu!

---

### Post by akakingess on 2009-12-10
Sorry to interrupt the thread, but I have run xterm glxgears and all I get is a window with some gears spinning, but it doesn't stop or show any info within the terminal when I close it. Could someone enlighten me as to how I find out what my output is at FPS? Thanks, as I am just trying to learn.

---

### Post by Vaphell on 2009-12-10
it's supposed to output message every 5 seconds into terminal window it's run from

**glxgears** in terminal is enough on my 9.04 box

---

### Post by akakingess on 2009-12-10
Thank you Vaphell, I will try that now and let y'all know how it goes...

Follow Up:  Thank you, that did the trick, although I had to bring the terminal into focus for it to give the updates, and that may have been the problem from the get-go, just ignorance on my part, but hey, live and learn, right? Thanks again, I now feel really comfortable with my graphics card as I was getting 15500+ Frames per 5 seconds..

---

### Post by EricDB on 2009-12-10
> **Ylon said:**
> Ok, your board is charming fast.


So, looks like that Adobe had the fix for you:

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)


You will get a tar.gz to install (remove the old flash first), are you fine with them?

You know, I thought I had installed that already.  But I went through it again, and sure enough I have a new filename under "about:plugins" and much improved performance.

Thank you so much for the fast and accurate help.

---

### Post by Ylon on 2009-12-11
> **akakingess said:**
> Thank you Vaphell, I will try that now and let y'all know how it goes...

Follow Up:  Thank you, that did the trick, although I had to bring the terminal into focus for it to give the updates, and that may have been the problem from the get-go, just ignorance on my part, but hey, live and learn, right? Thanks again, I now feel really comfortable with my graphics card as I was getting 15500+ Frames per 5 seconds..

That's not a real benchmark: is like have an university teacher to perform test made at nursery school.

If you want a real benchmark for your ubuntu, open terminal and:

**sudo apt-get install phoronix-test-suite**

Once installed ask for which tests are aviable
**phoronix-test-suite list-tests**
(you should agree to a warn/welcome message)

Choice your prefer test to perform, IE if you want to take the unreal turnament 2004 demo test


**phoronix-test-suite [color=red]install[/color] ut2004-demo**
this will download the demo (275MiB) from Epic Games's website and:
**phoronix-test-suite [color=red]run[/color] ut2004-demo**
will perform a real benchmark


(if you're in hurry, can test more little downloads)

> **EricDB said:**
> You know, I thought I had installed that already.  But I went through it again, and sure enough I have a new filename under "about:plugins" and much improved performance.

Thank you so much for the fast and accurate help.
Glad to help, you know... is not always a OS related issue when software/hardware (manufacturer's driver) when something don't work fine. So Ubuntu community wouldn't be always able to solve your problem. This time Adobe did solved your issue, with their work on "Linux 1% market share"... but the matter is that you count as Windows user, and Adobe grant you the chance to choice Linux... and no to be forced to use Windows only: this is a form of respect for both Linux and Windows (allow them choice, even if they didn't want to).

This mean that your problem with Linux wouldn't always resolved... but when you see your issue resolved it's (mostly) because the company that assemble your product see *you* proprietary of your product, not Microsoft.

---


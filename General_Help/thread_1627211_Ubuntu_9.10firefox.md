---
title: "Ubuntu 9.10/firefox"
date: 2010-11-21
forum: General Help
---

### Post by luismcrd on 2010-11-21
Hi,
I'm using ubnutu 9.10 and updaded firefox for v 3.6.12 and now the videos on youtube dont play. Althought on goolgle chrome 7.0.5 and opera 10.63 play. 
There is a way to put videos play on Firefox?

---

### Post by mikewhatever on 2010-11-21
You may have upgraded Firefox in such a way that it started using a new profile, and if the flash plugin remained in the old profile folder, flash in Firefox wouldn't work.
The following commands will show if you have more then one Firefox profile, and whether libflashplugin.so is in one of them:

ls ~/.mozilla/

locate libflashplugin.so

Run them from a Terminal window and post the output.

---

### Post by luismcrd on 2010-11-22
the result:

> luis@luis-desktop:~$ ls ~/.mozilla/
extensions  firefox
luis@luis-desktop:~$ locate libflashplugin.so
luis@luis-desktop:~$ 



??????????

---

### Post by VastOne on 2010-11-22
Same situation...

I am running 3 different versions of FF and all fail with Flash but Chromium works

I have the latest 64 bit Flash plugin that has been flawless until a couple of days ago

FF normal

FF 3.6.13.pre

and FF 4

all will not run flash content.  No errors, just a lame message that the content is not available and to try again later.

I use Flash-Aid to make sure the correct flash is installed

This is a FF issue, IMHO and not a flash issue

---

### Post by mikewhatever on 2010-11-23
Ok, luismcrd, I got the commands a bit wrong (needed a memory refresh), sorry about that. The correct and checked commands are down below:

ls ~/.mozilla/firefox

locate libflashplayer.so

VastOne, run the 'locate libflashplayer.so' command and post the output. I suspect it has something to do with the location of libflashplayer.so file.

---

### Post by luismcrd on 2010-11-23
no problem, here:
> luis@luis-desktop:~$ ls ~/.mozilla/firefox
dka0vczc.default  profiles.ini
luis@luis-desktop:~$ locate libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
luis@luis-desktop:~$ 


---

### Post by VastOne on 2010-11-23
> **mikewhatever said:**
> Ok, luismcrd, I got the commands a bit wrong (needed a memory refresh), sorry about that. The correct and checked commands are down below:

ls ~/.mozilla/firefox

locate libflashplayer.so

VastOne, run the 'locate libflashplayer.so' command and post the output. I suspect it has something to do with the location of libflashplayer.so file.

Not on my end, the location of the so file is correct and has been for months.  Flash and the plugin work for everything flash except for videos as in YouTube, MSN, ABC, anything that plays. But normal flash such as at my bank or at the Adobe Website and even the Avatar trailer played fine.

---

### Post by mikewhatever on 2010-11-23
Odd indeed. Everything looks correct as far as I can see.

---

### Post by luismcrd on 2010-11-24
yes is very odd, althought it's not a problem, because I like chrome and, in my opinion, is superior comparing with all browsers.
thanks any way.

regards

---

### Post by VastOne on 2010-11-25
My issue turned out being a No Script problem.  As I went through and disabled plugins, when No Script was disabled the problem went away.  

I scoured through the settings thinking that I had inadvertently turned something on or off but that was not the case.  I noticed at the NS web site that there was a 2.07 release and I was at 2.0.5.1 which is weird because I keep updated on plugins on every start of FF.  Apparently this feature does not update the plugin version levels but only the app.  

Once I installed 2.07 everything works as it should and I am protected.

---


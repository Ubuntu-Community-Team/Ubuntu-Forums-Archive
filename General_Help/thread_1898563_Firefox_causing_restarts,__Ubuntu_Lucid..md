---
title: "Firefox causing restarts,  Ubuntu Lucid."
date: 2011-12-21
forum: General Help
---

### Post by haaho on 2011-12-21
Hello,
I tried to open this page [http://unrestrictedstock.com/tag/christmas/](http://unrestrictedstock.com/tag/christmas/)
with Firefox 3.6.24 several times, and every time my CPU does 100% and  my computer  restarts.
No problems at all with Opera and Chromium.
I am using Ati Radeon 9550 with the free driver, Lucid 64 bit.

What may be the reason fo this restarts?

---

### Post by lovinglinux on 2011-12-21
The page has many images attached to the posts, but instead of using thumbnails, the site is actually using the full size images with reduced dimensions. I checked the first image and it has 4 Mb.

I tried here on both Firefox and Chrome and it does cause high CPU usage on both, not to mention excessive RAM usage. However, I am using Firefox 10. Your version of Firefox is a lot slower, so it is probably the cause of the crashes. It simply cannot handle such amount of processing. 

You can get the latest version of Firefox from a ppa. See [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247). However, I just forget about that site or write to the owner and ask to stop with the nonsense and put some thumbnails there.

---

### Post by claracc on 2011-12-22
> [http://unrestrictedstock.com/tag/christmas/](http://unrestrictedstock.com/tag/christmas/)

I have open the link with my firefox 3.6.24 (lucid lynx) in a hp compaq 6720s laptop intel core duo cpu 1,6 GHz and 2 GB RAM.

It opens slowly, consumes about 60 % CPU and certainly the images are loaded very slow, taking about 2 minutes to load. There isn't any restart of the browser. It seems the web page renders very bad and the images overload it.

---

### Post by haaho on 2011-12-22
Yes, I know the images and thumbnails are large.
But shouldn't Firefox crash itself instead of crushing and restartirt the whole system?
With Opera and Chrome the CPU usage is not that high, with Firefox even the MPD stops playing.
I am trying to figure, is there a hardware problem with my system, or it is just a software one.

P.S. I am using Sempron 2800+ an 2 GB Ram.

---

### Post by claracc on 2011-12-22
> I am trying to figure, is there a hardware problem with my system, or it is just a software one.

I think the problem is in the web page, that can affect in more or less length to some kind of hardware and software.

---

### Post by lovinglinux on 2011-12-22
> **haaho said:**
> But shouldn't Firefox crash itself instead of crushing and restartirt the whole system?

Yes, it shouldn't.

> **haaho said:**
> I am trying to figure, is there a hardware problem with my system, or it is just a software one.

I think it is a very particular situation that triggers a system failure. Most likely is a combination of less then optimal hardware, old software and high processing demand. Your system must have some issue that is usually not triggered until you have a condition of high processing and memory usage like this. For instance, it could be bad memory.

However, since other browsers don't crash, you could solve the problem by upgrading to Firefox 9.

> **haaho said:**
> With Opera and Chrome the CPU usage is not that high, with Firefox even the MPD stops playing.

P.S. I am using Sempron 2800+ an 2 GB Ram.

You can't compare Opera and Chrome with that version of Firefox, because they both use their own repositories and are kept updated with the latest major versions. That means they are more advanced versions of those browsers, while Firefox 3.6 is old and slow. If you test Firefox 9, I am pretty sure it won't crash.

---

### Post by haaho on 2011-12-22
I found the problem. And it is called KMS.

First I tried new Firefox 9 - the same, system RESTARTS.
Second, live USB image of Xubuntu 10.04 (with Firefox 3.6) - NO RESTART!
Live USB image Ubuntu (to exclude HDD problem) - RESTART. 
Finally turn KMS off and reboot - No Problemo! :D

---

### Post by lovinglinux on 2011-12-22
> **haaho said:**
> I found the problem. And it is called KMS.

First I tried new Firefox 9 - the same, system RESTARTS.
Second, live USB image of Xubuntu 10.04 (with Firefox 3.6) - NO RESTART!
Live USB image Ubuntu (to exclude HDD problem) - RESTART. 
Finally turn KMS off and reboot - No Problemo! :D

Great. Interesting that it also crashed with FF 9.

---

### Post by haaho on 2011-12-22
Yes, Firefox (both 3 and 9) became grey several times during loading the page; with KMS On,  the system just crushed, around the time FF to become grey for the fist time.

---

### Post by haaho on 2011-12-26
Now there is another problem!
With KMS turned off, Xorg start using, progressively, more and more RAM???

---


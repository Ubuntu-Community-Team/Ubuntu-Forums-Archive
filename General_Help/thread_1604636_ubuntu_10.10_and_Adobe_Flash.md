---
title: "ubuntu 10.10 and Adobe Flash"
date: 2010-10-24
forum: General Help
---

### Post by loukingjr on 2010-10-24
one of the recent updates to 10.10 seems to be causing Adobe Flash to crash in fullscreen. It wasn't doing that when I first installed 10.10 and I have other non-ubuntu guests that aren't crashing. I also posted this over in Multimedia.

---

### Post by zarathustra@ on 2010-10-24
hi,

although i use 10.04, i found flash-aid addon for firefox very useful to avoid collisions between plugins and make flash work flawlessly.
just look up Flash-Aid, and install it to your Firefox.

let me know if it works,

cheers.

---

### Post by loukingjr on 2010-10-24
> **zarathustra@ said:**
> hi,

although i use 10.04, i found flash-aid addon for firefox very useful to avoid collisions between plugins and make flash work flawlessly.
just look up Flash-Aid, and install it to your Firefox.

let me know if it works,

cheers.

well, I have no problem in 10.04 actually which is what I am typing in at the moment. But I will try it in 10.10 and see if it helps.

thanks

---

### Post by loukingjr on 2010-10-24
well, that didn't help. but thank you none the less.

---

### Post by leighahh on 2010-10-24
Well I am glad to see that I am not the only having a problem with flash on 10.10. For me it loads but the dimensions of the items are way off. I have added the flashaid and am about to test it and see if it works right and will let you know.

---

### Post by lovinglinux on 2010-10-24
See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by loukingjr on 2010-10-24
> **lovinglinux said:**
> See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

as I think I mentioned. this seems to be an Ubuntu 10.10 issue. It also happens in Chrome or Chromium. not specific to FF. And full screen works in 10.04.

---

### Post by leighahh on 2010-10-24
Well it helped a little bit but after a few minutes I am getting a javascript not responding error.

---

### Post by lovinglinux on 2010-10-24
> **loukingjr said:**
> as I think I mentioned. this seems to be an Ubuntu 10.10 issue. It also happens in Chrome or Chromium. not specific to FF. And full screen works in 10.04.

See the third item on that list. Is a flash tweak that should work for any browser.

---

### Post by efflandt on 2010-10-24
If you have been keep up with updates, the Firefox and flashplugin-installer in 10.04 and 10.10 are same identical versions (Firefox recently updated to 3.6.11 in both).  So maybe it is a video driver issue.

Using flashplugin-installer in 64-bit 10.04 or 10.10 was apparently segfaulting flashplayer.so which was crashing npviewer.bin related to Firefox.  But I did not even notice when that happened until I got crash reports in 10.10 beta and looked in /var/log/messages of 10.04.  So I am using real 64-bit flash from Adobe with no issues in 10.04 or 10.10 release.

---

### Post by loukingjr on 2010-10-24
> **lovinglinux said:**
> See the third item on that list. Is a flash tweak that should work for any browser.

turning off hardware acceleration in flash fixed it.

thank you.

---

### Post by ctxanadu on 2010-12-12
Hi ..
Yea even I had a problem with the flash video getting freezed in fullscreen.
this is specific to ubuntu 10.10 version for both Firefox & Google Chrome

The fix for this  was creating a file "/etc/adobe/mms.cfg" and putting the entry
OverrideGPUValidation=true

---

### Post by rulet on 2011-02-28
That doesn't help.

---


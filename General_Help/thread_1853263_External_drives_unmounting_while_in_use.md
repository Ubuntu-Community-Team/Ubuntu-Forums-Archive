---
title: "External drives unmounting while in use"
date: 2011-10-01
forum: General Help
---

### Post by nCryp7 on 2011-10-01
Hello Linux community. I've got myself a pretty irritating problem and being as this forum has helped me in the past, I'm hoping to get some advice, as google has been no help.

I've got four external drives hooked up to my Ubuntu box, all via USB. Whenever a drive is in use (listening to music, watching movie, whatever) it will, without warning, unmount after a few minutes.

I know what you're thinking! And you're WRONG I tell you! All four drives have fan-cooled enclosures and are kept at a fine operational temperature. Overheating is definitely not the issue.  To make matters worse, sometimes when the drive unmounts it freezes the machine to the point where I can't even drop down to the terminal (via CTRL-ALT-F#), it's simply stuck. This was the case this latest time, which prevented me from getting some output from dmesg to post.

This is not only irritating, but the potential for data loss is frightening, as I probably have around 1.5 TB spread across the four (a fact that makes the attempt to reproduce the situation in order to get some dmesg output a very scary option).

Has this happened to anyone else? I've googled to my heart's delight to no avail, everyone just wants to know how to safely remove them. If I had a quarter for each thread I saw asking how to safely remove a hard drive, I'd be retired in a night.

~ To sum up ~


[LIST]
[*] All four HDDs are WD
[/LIST]

[LIST]
[*] All four are SMART healthy
[/LIST]

[LIST]
[*] All four suffer from this problem, which only occurs when the drives are in use (not even extended use)
[/LIST]

[LIST]
[*]This problem persisted through my change from Debian to Ubuntu, so it could be a Linux problem, or a Debian problem, I dunno.
[/LIST]

[LIST]
[*] I am still a Linux-Newb, so bear with me :)
[/LIST]

Thanks a lot!

---

### Post by 2F4U on 2011-10-02
Do these drives have a power supply of their own or are they supplied through the usb port? Are they connected through a usb hub or directly to the machine? If you think its Ubuntu/Debian related, it may be worth checking a different liveCD (e.g. something that is not Debian-based like Fedora, openSUSE, etc.). This would also help if you need to report a bug to the developers.

---

### Post by dcstar on 2011-10-02
> **nCryp7 said:**
> Hello Linux community. I've got myself a pretty irritating problem and being as this forum has helped me in the past, I'm hoping to get some advice, as google has been no help.

I've got four external drives hooked up to my Ubuntu box, all via USB. Whenever a drive is in use (listening to music, watching movie, whatever) it will, without warning, unmount after a few minutes.
.........

[LIST]
[*] **All four HDDs are WD**
[/LIST]
.........

WD "Green" drives by any chance?

---

### Post by nCryp7 on 2011-10-02
Thanks for the input.

@dcstar - An interesting question that never occurred to me. I don't believe they're green drives, but I'm not positive. I'll have to pull them out and look up the model. If that IS the case, do you have any ideas how I can remedy the problem? Is there any way to disable the 'green switch' so-to-speak? Through BIOS perhaps? I'll have to look into that.

I'm downloading Fedora now to see if the problem does indeed lie within Debian-based systems.

Thanks again guys.

---

### Post by nCryp7 on 2011-10-04
Just to update in case anyone with the same problem stumbles upon this. So far, from the looks of it the problem lied with Debian/Ubuntu.

I installed Fedora alongside Ubuntu and played a repeating playlist from an artist that commonly produced the problem, on a drive that commonly produced the problem. Left it on overnight, and come morning it was still playing merrily away!

Glad that the issue is resolved, sad that I now need to fully transition to Fedora from Ubuntu!

Thanks again to those that replied!

---


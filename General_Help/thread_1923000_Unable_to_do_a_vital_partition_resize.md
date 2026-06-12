---
title: "Unable to do a vital partition resize"
date: 2012-02-09
forum: General Help
---

### Post by dialectical.one on 2012-02-09
Greetings!  This may seem like a straightforward issue with GParted [0.4.5], where it's "unable to read the contents" of a partition in question. But my system is a mess, so the usual workarounds don't seem feasible. 

This NTFS partition was originally Windoze, but I never used it, so it's just storage. My aim is to reduce its size for the greater good:

My main (Ubuntu) partition is way too small, & if I don't add more space to it my system will soon become unbootable! :( Because of this, I haven't risked updating in wayy too long - my system is running 9.10 Karmic (dreadful, I know!). (I suspect this is why I've recently been unable to install anything with the Software Center.)

I have no working CD drive, hence no live GParted CD is possible (the straightforward solution). And there doesn't seem to be enough space to install tuxboot to create a live USB (on my non-existent thumb drive). 

Any ideas on how to proceed? (Please let me know if you need more - or more clear - info!)

P.S. I'm a nerd, but my field is not one that gives me fluency in anything having to do with the technical side of computers ... so my apologies for any ignorance I'm sure I'll display, & many many thanks for your help and understanding! :)

---

### Post by efflandt on 2012-02-09
Do you have access to a Windows PC anywhere that could **chkdsk /f** it to fix it and defrag it to move files down on the drive, which would make resizing quicker?  If gparted thinks there is something wrong with an ntfs partition, it refuses to touch it until Windows fixes it.

Is Linux itself still able to mount and read the partition without errors?

---

### Post by dialectical.one on 2012-02-10
The windows partition is inoperable. I hadn't been using it, so I deleted all the files necesary to run it. If you mean to use someone else's computer, how would I get it to defrag my laptop?

Yeah, no problem whatsoever mounting it & reading the files. Supposedly this is a common error with GParted (just the usual workarounds don't seem feasible).

---

### Post by sudodus on 2012-02-10
You could get a 'usb to ide and sata cable set' so that is can run as a usb drive attached to the other pc.

If the other computer is a desktop, it might be enough with some cables.

---

### Post by dialectical.one on 2012-02-20
Are there any other options?

---

### Post by dragonfly41 on 2012-02-20
> I have no working CD drive, hence no live GParted CD is possible (the straightforward solution).

When I had that same problem I bought a USB CD drive instead of the broken internal.

---

### Post by dialectical.one on 2012-02-26
On the usb CD drive: I'm broke, but it's infinitely better to invest in something I could really use (vs something I'd be lucky to get 1 use out of). 

Any recommendations on external CD drives which work readily with Ubuntu?

---


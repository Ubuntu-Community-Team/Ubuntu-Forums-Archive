---
title: "Wine &amp; Photoshop CS2"
date: 2010-01-02
forum: General Help
---

### Post by SergeantOreo on 2010-01-02
Hello Everyone,

I recently reinstalled Ubuntu 9.10, and Wine along with it. I am trying to install Photoshop CS2 **(from the Creative Suite 2 Disk)**; the following is the process and output.

[B][In Terminal]
[/B]
[LIST=1]
[*]wine /media/cdrom0/Setup.exe
[/LIST]
The errors I get are: ```
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x4530b1
```And there is also a message about about not being able to load module from //C:/Wndows/system32/adobe.exe.

The entire log can be read [here]("http://www.pasteall.org/10093")

---

### Post by SergeantOreo on 2010-01-05
Bump. :(

---

### Post by jamesisin on 2010-01-05
Adobe's installer can be a real pain.  As you can see from your error message it is looking into the system32 folder for the (presumably) installer.  You might try making an ISO from that disc and then mounting that ISO under WINE as d: (so you can fool Adobe into thinking it's a CD drive under Windows).  Just a guess though.

Or you could run Gimp and use all of your PS plugins there.

---

### Post by SergeantOreo on 2010-01-05
> **jamesisin said:**
> Adobe's installer can be a real pain.  As you can see from your error message it is looking into the system32 folder for the (presumably) installer.  You might try making an ISO from that disc and then mounting that ISO under WINE as d: (so you can fool Adobe into thinking it's a CD drive under Windows).  Just a guess though.

Or you could run Gimp and use all of your PS plugins there.

Making an ISO sounds good; the problem is that there are multiple disks, so I will have to look through each (there are 3 or so) and copy all of the *right* contents.

Also, how do I mount the ISO in Wine?

---

### Post by jamesisin on 2010-01-05
Well, this is new territory for me, but here goes.

I had problems with that Adobe installer in the past, as mentioned.  I was not able to run the installer from a server because it kept insisting that I should put the disc into [the location of the first folder].  Completely retarded.

So my vision is that you create a mount point for the image which was pointed to as d: under the WINE directories.  You can probably even mount the CD drive as d: but I don't know exactly.

The point is to have a Windows recognizable fixed location where you can (virtually) place each installation disc.

---

### Post by Minsky on 2010-01-05
Someone managed to get CS4 working in this thread:
[http://ubuntuforums.org/showthread.php?t=1284993](http://ubuntuforums.org/showthread.php?t=1284993)
Their solution might also work with CS2.

---

### Post by SergeantOreo on 2010-01-08
> **Minsky said:**
> Someone managed to get CS4 working in this thread:
[http://ubuntuforums.org/showthread.php?t=1284993](http://ubuntuforums.org/showthread.php?t=1284993)
Their solution might also work with CS2.

The link you posted isn't working for me; the forum says I do not have the permissions necessary for the page.

---

### Post by Perfect Storm on 2010-01-08
It was jailed, due to some EULA issues.

---

### Post by John Bean on 2010-01-08
CS2 doesn't need the CD, it'll install just fine from any location. I copied the CD contents to a folder and installed just Photoshop (I didn't want the rest) by running the serup program from the Photoshop directory rather than the setup "wrapper" in the roor of the CD.

Please note that Bridge will not work under wine but Photoshop CS2 itself is fine. It's the only reason I use wine at all.

There are still a few caveats (but only a few) and Googling for CS2 and wind will find them.

---

### Post by SergeantOreo on 2010-01-09
I was able to get it working by using an iso installer; thanks for your help mates! :D

---

### Post by jamesisin on 2010-01-09
Excellent news.  Did you use a method like I described or were you able to simply point Wine at the ISO?

---

### Post by SergeantOreo on 2010-01-10
> **jamesisin said:**
> Excellent news.  Did you use a method like I described or were you able to simply point Wine at the ISO?

I just opened the Photoshop setup with Wine, and it ran without any problems.

---

### Post by jamesisin on 2010-01-12
Oh, that's right.  I was thinking about Suite installation.  I forget that you can just pull up one installer (executable) and run that&#8212;no disc swapping involved.

---

### Post by dinakumar12 on 2010-02-13
hello sir,
 i too got that same error "err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x4530b1"

how to create an ISO

---

### Post by jamesisin on 2010-02-13
I believe Brasero will allow you to rip a CD or DVD as an ISO.

---


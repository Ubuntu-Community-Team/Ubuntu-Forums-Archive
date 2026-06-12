---
title: "LiveCD will not boot"
date: 2010-04-30
forum: General Help
---

### Post by poliltimmy on 2010-04-30
I have downloaded and burnt 2 separate Ubuntu 10.04 iso. One from bit torrent and the one from the official us mirror on this site. Neither will boot. I have other LiveCDs that will Xubuntu 8.10 (which I tried but did not care for), BootNG, Gparted and other all boot. So a hardware problem does not seem to be an issue.

Amd 64x2 4200+ AsusAliveSata2-GLAN/A/ASR Motherboard

---

### Post by pcura on 2010-04-30
did you check if your BOOT settings are:

CD/DVD is first, then floppy and hard drive last.....

This happened to me when I tried using Live CD on a different distro

---

### Post by endoglastic on 2010-04-30
If it's not whats mentioned above, try a new burning software. I've downloaded straight from the website and it works just fine.

---

### Post by poliltimmy on 2010-04-30
yep. Tried that. even tried leaving the cd drive as only boot option. I am lost.

---

### Post by poliltimmy on 2010-04-30
I got a disk to attempt a boot burning with Brasero on the second option. After watching the dots under the logo until I was mesmerized, it stopped with all dots lit up and the gave an Authorization error.

---

### Post by pcura on 2010-04-30
get the livecd thru another computer with windows OS at least when you burn it you know there won't be any problems.....

burn it with nero or roxio. they both work fine for burning image files. hopefully you have another computer that is Windows OS.

I've encountered some problems too with basero, just needs a little tweaking with it. but right now you need to download or burn thru windows os. 

gl on your 10.04

---

### Post by poliltimmy on 2010-04-30
The actual error is Authentication failure.  And I do not have a windows computer. Have not ran windows in over 2 years. Why would I? I have already convrted all my friends.

---

### Post by pcura on 2010-04-30
did you try the live cd of 10.04 before installing though?.

---

### Post by kill4killin on 2010-04-30
I had the same issue with my P4 test box. It's older hardware so I had to set the "noapic" option to get it to boot back in one of the alpha releases, seems to work fine now though. You might try checking the boot options and try booting with things like "apic" or "noapic"

Check here for other boot options

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/ch-bootopts.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/ch-bootopts.html)

---

### Post by poliltimmy on 2010-04-30
I had to hit F6 at that first screen, after that the disc ran normal.

---

### Post by ParadoxBlue on 2010-05-02
I'm currently running Ubuntu 9.10 from the Canonical provided LiveCD and it runs just fine. I also downloaded and burned Kubuntu 9.10 myself a couple weeks ago and it also runs ok.

The issue seems to be with the 10.04 releases. I've downloaded Ubuntu and Kubuntu 10.04 and burned them to cd and neither will boot. Both download checksums were doublechecked using md5sum and md5sum -c commands. For both of these I get the normal language option screen and the "Try *buntu without any changes to your computer, memory check, etc. menu". After hitting "enter" and quite a bit later I end up with what looks like terminal screen including a system prompt.

Before I get the system prompt I see a couple screens of text and I managed to get a few of lines of it written down although this is not verbatim or complete:
[B][I]
error on device sr0
illegal mode for this track
buffer I/O error on device sr0[/I][/B]

These cds were burned on a Windows 7 system at my local library since my own cd burner is on the fritz. They were actually burned on the exact same computer that I used to burn the Kubuntu 9.10 disc (the one that *does* work). Both the *buntu 10.04s were verified after the burn process. Upon re-inserting them into the library computer they both brought up the option to run Wubi or browse the files on the cd so it would seem that the data is ok.

Yesterday I even downloaded Ubuntu 10.04 again and burned it again at my local library making sure I used a different computer than I used on the first two tries just in case. Now I have a total of three 10.04 cds all with the same problem.

Any ideas folks? Any and all suggestions/ideas will be appreciated and if you would like any more info please don't hesitate to ask.

---

### Post by Rubi1200 on 2010-05-02
There seem to be a lot of people experiencing difficulties (I am one of them).
This may be the source of the problem:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes](http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes)

If anyone knows of a workaround, it would be much appreciated.
Good luck to all.

btw, I am sticking with Karmic until, and if, these issues are sorted out.

---


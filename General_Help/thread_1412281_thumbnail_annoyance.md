---
title: "thumbnail annoyance"
date: 2010-02-21
forum: General Help
---

### Post by jasonjob on 2010-02-21
Okay, judging by the number of results I've trawled through, Ubuntu simply cannot generate thumbnails (or be made to do so by a hack) for files located on network drives (although it CAN utilise existing thumbnails for files I've moved from my hard drive to my NAS).

I accept that this is so, and conclude that Ubuntu is, quite simply, broken, and not adequate for my modest needs.

But what I want to know is WHY is this so????  Why should an OS that prides itself on network integration (and being at the forefront of development) unable to do this one simple thing?  I mean, if even Windows can do it... :p

Thanks

---

### Post by raktarok on 2010-02-21
Hi,

Have you checked Edit > Preferences > Preview from the file manager? Assuming that you are using nautilus...

and never fear, my friend. ubuntu is capable to do everything that our old friend  windows can do, provided that you follow the right path :)

---

### Post by jasonjob on 2010-02-21
Second thing I did (first was to look up exactly where to find that setting again).  

I've been trying to get it to work on and off for the last month or so.  I can find only two answers addressing the issue:  Have you checked... (your answer :), and Sorry, Ubuntu just doesn't work like that over a network.  So if anyone can come up with something different... :>

Without wanting to sound like a windows fanboy (not even close :), a ranter, or starting a whinge, sorry, but Ubuntu just can't do everything that Windows does (just like Windows can't do everything that Ubuntu can).  Potentially yes, I'll grant that, but straight out of the box, no.  This being a prime example of something eminently straight-forward but apparently just not possible - and without any explanation.  

I gather it OUGHT to be able to do it (why else are the configuration settings made the way they are), but that doesn't change the fact that it doesn't, and judging by the sheer number of search results it isn't just me.  Anyway, as I said, if anyone can offer a reason why it doesn't work (I've given up on actually having it work), that'd be great :)  

One of the BIG differences between Windows and Linux - usually there is a reason for flaws, instead of a) commercial / proprietary lock-in or b) just coz...

---

### Post by raktarok on 2010-02-21
Hmm...I accept that there are some things that windows manages to do with considerable ease, but linux desktop distros like ubuntu are catching up fast, and its bound to change with time. 

I have never actually tried previewing network files, but I assumed that they would work. It seems that I was wrong here... anyway, have you tried using totem-video-thumbnailer, evince-thumbnailer and other similar commands on these network files to see if a thumbnail picture file is generated or not? When gnome generates thumbnails, these are the commands that get called. 

If you have done this already, then please ignore the above. And have you tried this with other desktop environments like KDE, XFCE, etc. Maybe its just a problem with gnome?

---

### Post by jasonjob on 2010-02-22
Catching VERY fast, yes - upgraded this morning and suddenly my graphics card works properly :)  Wasted a lot of time this afternoon playing with Compiz...  Windows 7 and Aero can go hang - M$ never can do anything first, or get it right, can it? :}

Tried evince-thumbnailer manually, didn't do anything.  Don't know about totem-thumbnailer, hadn't realised it existed :/

I use only Gnome, I'm not willing to mess about with other desktop enviros - too much trouble when the one I've got works (mostly... ;) just fine.

---

### Post by jasonjob on 2010-03-19
Okay, interesting twist here...

Seems that Nautilus CAN generate thumbnails for me over a network drive, but with some qualification:

My network drive is reached by Connect to Server, not mounted.  Via this connection, I get thumbnails of video files, but not other things such as comics.

When I mounted the network drive, I got all the thumbnails.

Playing around, I ran Evince from terminal, and got some GTK errors (operation not supported by backend) when browsing a connected network drive (given as an smb:// entry), but not a mounted network drive.  Comix gave the same result (no idea what they meant, because they were rather cryptic, but I can guess what "failed" means :) in the same situation.

Odd addendum - when I run Totem from terminal (I gather that totem is what generates thumbnails for my video files), I get the same backend error when browsing to an smb:// drive, and yet the thumbnails work...

So what I want to know is what difference does it make how I connect (surely a network drive is a network drive?), and, given that there is a difference, why can't the built-in thumbnailer handle a built-in connection method?

---


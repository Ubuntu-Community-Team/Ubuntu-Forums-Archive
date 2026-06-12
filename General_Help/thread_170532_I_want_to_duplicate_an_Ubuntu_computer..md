---
title: "I want to duplicate an Ubuntu computer."
date: 2006-05-04
forum: General Help
---

### Post by em3raldxiii on 2006-05-04
Quick synopsis:

Source computer:
Hardware: Celeron 466 512 mb SDram (NO BURNER)
OS:  Kubuntu Breezy 5.1
Software:  Apache2, Mysql, PHP5 for a fairly basic LAMP server
Website:  [www.anxietyofinfluence.ca](www.anxietyofinfluence.ca)

Destination computer:
Hardware:  P4 1.6GHz 512MB PC2100
OS:  Ubuntu Breezy 5.1
Software:  Pure unadjusted clean Ubuntu install

Summary:  I want an easy way to take the entire website & all of it's configuration settings and move it over to the new comptuer.  I could certainly do it all the hard way, but I set up the server quite some time ago, and I am only an intermediate Linux user, so I am 100% certain I would run into a number of pain-in-the-*** roadblocks.

Further Info:  The server is on an ADSL line at 1.5 Mbit, so it's not exactly the fastest connection.  Add to this the snail-like performance of a Celeron 466, and when PHP accesses the Mysql database ... well, ye gotta wait.  With the new P4 1.6, I expect substantially faster processing, and subsequently shorter wait times.  This may allow the server to handle a larger number of requests as well.  At some point, I intend to migrate entirely to a flash-based website, but that is in development and won't be ready for some time (at which point the site will be served remotely).

I understand that migrating from Kubuntu to Ubuntu will present a number of minor issues, but since Linux is (thankfully) not entirely GUI dependent, I figured the migration should be possible.  Is there a utility that can "back up" the server-related files and then install them to the new computer with a minimum of fuss?  Or perhaps there are some handy-dandy configuration commands for shell?  Since the source computer has no optical writing device, I will likely want to use FTP or other networking methods to transfer the files across.  However, in a pinch I could probably rip the burner out of the destination computer temporarily.

Any thoughts on this matter will be very much appreciated.  Thanks in advance :D

Mike Ireland
Web admin for [www.anxietyofinfluence.ca](www.anxietyofinfluence.ca)

PS. If you like alt-rock like Evanescence and Lacuna coil, go to [www.anxietyofinfluence.ca](www.anxietyofinfluence.ca) and have a listen.  Their 4 song demo CD is free to download :D

---

### Post by aysiu on 2006-05-04
Maybe you can use PartImage?
[http://www.partimage.org/Screenshots](http://www.partimage.org/Screenshots)

---

### Post by em3raldxiii on 2006-05-05
Thanks Ayisu.  I'll go have a close look at this program, it looks like it might work.  The only problem I can think of (and I haven't researched this over there yet) is that the drives are not the same size.

How would linux behave if I was to yank the hard drive out of the source computer and slap it into the destination computer?

---

### Post by em3raldxiii on 2006-05-05
Okay, so I decided to do some open-heart surgery (since I'm much more of a hardware guy than a software guy), and I ripped the hard drive out of the SOURCE computer and slapped 'er into the DESTINATION computer.

Everything works fine, server is fast and runs with a minimum of fuss YAY (had to reconfigure my router to the correct computer, of course, but all good).

**One problem**.  Of course, the video adapter drivers are totally different, and I can't seem to figure out how to make it work.  Apparently this is not an uncommon problem, but I have yet to find a clear "how to" with regards to fixing it.

I will post a brand-new thread on this matter.

Thanx!

Mike

---

### Post by joshbrown40 on 2006-05-05
If just swapping a hard drive works for putting Ubuntu on another computer, could you merely copy every file over to the new computer, a la, make a tarball of the / directory and send it to the new computer, unpack it, and overwrite everything?

---

### Post by em3raldxiii on 2006-05-05
I don't think so.  I am not an Uber-Linux super user or anything, but from my understanding it wouldn't properly configure the servers to run precisely the same way as they are right now.  On top of that, copying the entire filesystem in it's current incarnation would be over 6GB (lotsa big files), even tarballed it would be kinda big and not so easy to transfer from the older hardware (no burner).  I think it would also gibble up the boot system and stuff ... I dunno ... I just thought moving the HD would be the easiest way.

And so far, I think I was right; the server is running smooth as silk and faster by far than it ever was before (no wait time during server-side scripts or database writes).  Only issue so far is the video drivers, I think .... but that's in a new thread :D

---

### Post by em3raldxiii on 2006-05-05
Just a note, the following code fixed my video issues by re-detecting the hardware.  This info comes from one of the Archive Team, tseliot.  Thanks to him, my server is now 100%

Here's the code:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If anyone else has this problem, give it a shot :D

Mike

---


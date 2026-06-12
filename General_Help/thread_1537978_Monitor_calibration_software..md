---
title: "Monitor calibration software."
date: 2010-07-24
forum: General Help
---

### Post by oldsoundguy on 2010-07-24
I have a Gretag-Macbeth Eye-One monitor calibration tool that (along with the Epson printer calibration tools) I use on my Windows machine to get W.Y.S.I.W.Y.G. color photography printing.

Am curious as to IF the thing can be run under Ubuntu (using 10.04).  Know that it will have to be run in Wine or some emulator. Have spent way too much time on Google with virtually no results.

The question is, has any one done this? And how was it accomplished AND (most importantly) DOES IT WORK?

This is NOT one of those "I gotta get this working" things .. just that I WOULD like to calibrate the monitors on the Ubuntu machines I have.

---

### Post by CharlesA on 2010-07-24
Guessing it's written for Windows, so maybe try running it in WINE?

---

### Post by oldsoundguy on 2010-07-24
> **CharlesA said:**
> Guessing it's written for Windows, so maybe try running it in WINE?

Yes, it IS written for Windows (I believe I made that portion clear .. but maybe not.)

The issue is that it is a Windows install disk for the drivers, and for some reason, I can't even see the files on it in Ubuntu.  (drives show under Places> Computer .. but no content shows up in the file browser.)  THAT may be part of the issue, but the real issue is ... does it work?

(why spend a lot of time trying to get something to work that will NOT work?  Foolish to do so, hence, the original question.)

---

### Post by CharlesA on 2010-07-24
Not sure how you can get it working, if the files don't show up as being on the CD.

What sort of files are shown if you insert the cd into a Windows machine? They should be there regardless of the OS.

---

### Post by oldsoundguy on 2010-07-24
It has the standard auto run Windows skuzz.  Program can be run FROM the disk or can be installed (I installed it on the Windows box).

I may NOT have the dvd's mounted properly .. but have not had the need to use them in a while.  They do show up in the Places> Computer .. but when I click to open .. NOTHING!  (could be doing something stupid or omitting something)

HAVE installed Wine, it does not even see the drive(s)!

---

### Post by CharlesA on 2010-07-24
I'm not all that familiar with Wine, but I think you should be able to mount it and have it show up.

Maybe someone else has a bit more experience with Wine then I do.

---

### Post by oldsoundguy on 2010-07-24
thanks anyway.. as noted .. this is not an "end of the world if I can't install this" situation.  But it WOULD be nice to get it to work .. if, for no other reason than to get it to work!

---

### Post by oldsoundguy on 2010-07-26
Been a couple of days and no adds to this thread.  Would like to know just what I screwed up here as far as Wine and reading my DVD drives.

That, I think, is the real issue as I think I can take it from there once I can SEE the disk in a drive.

But, as noted, not earth shaking!

---

### Post by oldsoundguy on 2010-07-29
gonna keep bumping this every other day or so. In HOPE that someone else has the same gear and has been able to get it functioning.  Would be nice IF I could get MINE working.  Thanks BTW to all the lookers .. at least there is SOME interest.

---

### Post by ElSlunko on 2010-07-29
Have you tried finding the executable for the program via the device's website?

---

### Post by oldsoundguy on 2010-07-29
> **ElSlunko said:**
> Have you tried finding the executable for the program via the device's website?

Not available.  I have an older model and they are pushing a hot new item.  It MAY be burried in an archive on their site, but these are graphics people, not computer.  so nothing computer is simple for them!

I have the driver disk .. only it won't READ for some reason.  Put it in the drive (drive shows as mounted) and NO FILES or content can be seen .. tried several drives .. Can read other stuff off of those drives, but what I read was the ISO's that I have burned.

But right now the entire computer is down as the CPU cooler tanked.  Just got the new one in the mail a few minutes ago, so now have to put the box back together and make sure all is well before I close it up.

So this is becoming an on going on again/off again project!! LOL

A thought .. I may be able to copy the disk to the My Shared Folder on a Windows box and then haul it into the Linux box .. had not thought of that.   Will see how that shakes out.

---

### Post by oldsoundguy on 2010-08-01
BaBaBa BUMP!

---

### Post by oldsoundguy on 2010-08-04
bump the pup

---

### Post by drewsus on 2010-08-04
well have you tried copying the contents of the disc from Windows and then bringing that to Ubuntu?

And, have you read this: [http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management) and checked out the software and such there?

---

### Post by oldsoundguy on 2010-08-04
> **drewsus said:**
> well have you tried copying the contents of the disc from Windows and then bringing that to Ubuntu?

And, have you read this: [http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management) and checked out the software and such there?

Thanks for the link .. it tells me that currently (as of that wiki) my EyeOne software does not run under Linux and that there is no Linux alternative.

And found out that using it under Wine or any supposed emulation program is futile as any settings set up in the Windows environment will default back when you exit the program.  

Just another reason that pro and serious amateur photographers still can not use Linux for their work.  IF you can not get W.Y.S.I.W.Y.G co-ordination between monitor and printer, it makes you go back to Apple or Windows for those tasks.

Something that developers should consider down the road.

---

### Post by drewsus on 2010-08-04
Glad I could help, if only for you to draw some conclusions.
Now, have you considered running XP or greater in a virtual machine (re: virtualbox) so you dont have to switch between the two boots?

---

### Post by oldsoundguy on 2010-08-04
> **drewsus said:**
> Glad I could help, if only for you to draw some conclusions.
Now, have you considered running XP or greater in a virtual machine (re: virtualbox) so you dont have to switch between the two boots?

VM is the same issue on the settings .. the moment you leave it, you are back to system defaults.

No, currently I run XP on a SEPARATE machine .. all by itself.  Loaded with my photography/video/audio stuff.

I use a HDMI  KVM switch and all I have to do is hit a button that sits on my PHYSICAL desk to switch between.  That allows two computers to share one monitor, one mouse, one keyboard.
Sound is done by using Altec ACS45 setup which allows for two simultaneous inputs.

It WOULD be nice to be able to totally dump the Windows box, but as long as Linux drags it's feet in those areas that are critical to ME .. will have to do it the way I do it now.

Equate my enthusiasm for photography as to that of a gamer and you see the need. Two of the super weak points of Linux.  Linux does EVERYTHING else for me now and does ALL of my on line activities.

---

### Post by Quicksand on 2010-08-04
Have you tried [Argyll CMS]("http://www.argyllcms.com/doc/ArgyllDoc.html")?

The documentation page lists several Eye-One instruments as supported.

---

### Post by ElSlunko on 2010-08-04
Yeah lots of Linux photographers use Argyll CMS. I don't have a calibrator unfortunately, but I guess I was lucky enough to have something very similar to what my printer outputs by default.

---

### Post by oldsoundguy on 2010-08-04
> **Quicksand said:**
> Have you tried [Argyll CMS]("http://www.argyllcms.com/doc/ArgyllDoc.html")?

The documentation page lists several Eye-One instruments as supported.

Looks promising and my model is listed as supported.  Think I will give it a shot on one of my test bed computers and see IF I can muddle through installing it and check it out.

THANKS BIG TIME for the link!

---

### Post by CristianPrisacariu on 2010-12-25
Hello,

In this post:
[http://ubuntuforums.org/archive/index.php/t-407533.html](http://ubuntuforums.org/archive/index.php/t-407533.html)

it tells to use the software called Argyll
[http://www.argyllcms.com/](http://www.argyllcms.com/)

for which I found very good documentation:
[http://www.argyllcms.com/doc/ArgyllDoc.html](http://www.argyllcms.com/doc/ArgyllDoc.html)

and most important, the Guided Tour:
[http://www.argyllcms.com/doc/Scenarios.html](http://www.argyllcms.com/doc/Scenarios.html)

This software supports many devices, among which my Eye-one Display 2:
[http://www.argyllcms.com/doc/instruments.html#i1d](http://www.argyllcms.com/doc/instruments.html#i1d)

I just used it, following the instructions, and my laptop has new, warmer colors now :)

I am sure you can manage too.

best wishes,
cristian

---


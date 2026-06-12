---
title: "Shotwell &amp; duplicate detection"
date: 2012-08-12
forum: General Help
---

### Post by Bartender on 2012-08-12
I've been using Shotwell lately instead of importing photos by hand.  When I'm in the Shotwell application, it seems to be detecting previously imported photos and only getting the new ones.

However, if I get out of Shotwell and go into Pictures, the folders that Shotwell is creating are full of duplicate pictures.  Apparently each time I plugged the Canon t3i in, Shotwell made another duplicate in the appropriate Pictures folder.  Some of the folders have a dozen duplicates.

Just to be clear, when I'm in Shotwell it seems to be finding the new photos and importing only those.  But in the background it's creating copies to the Pictures folders every time the camera is plugged in and I ask it to "Import".  Am I doing something wrong?  Or is this a bug in Shotwell?

---

### Post by eric-yorba on 2012-08-13
That certainly sounds like a Shotwell bug; it's supposed to import a given photo only once, unless the user specifically makes a duplicate (ctrl-D.)

What version of Shotwell are you running?

---

### Post by Bartender on 2012-08-20
Oops, I didn't get back to this in a timely manner.  Shotwell 0.5.0, on Ubuntu 10.04.

---

### Post by eric-yorba on 2012-08-21
That's a very, very old version -- the current release is 0.12.3!

There's been significant fixes to the import code since then, which are likely to solve this.  But unfortunately you can't upgrade unless you also upgrade your OS.  (And I'm guessing you haven't done that for a reason.)

---

### Post by Bartender on 2012-08-21
Well, it's our daily-use PC (DUPC), so I tend to leave things alone.  I'm running 12.04 on a lappy and it seems OK but there are some things about Unity that get on my nerves.  
Our DUPC is running dual monitors via a low-end nVidia card.  I'd read that Unity has problems with dual monitors.  Has that been straightened out?  If so maybe it's time to move on.
I wonder if there's a ppa for Shotwell?

---

### Post by eric-yorba on 2012-08-22
There is an official PPA for Shotwell.  Since you're running Lucid, you can upgrade to 0.7.2.  It may solve some of the issues you're seeing. Link: [https://launchpad.net/~yorba/+archive/ppa](https://launchpad.net/~yorba/+archive/ppa)

Can't speak for everyone, but I've been running 12.04 with Unity on dual monitors with no problems.  You can always download the Ubuntu CD and run it in Live mode to test it out on your hardware without installing.

---

### Post by Bartender on 2012-08-22
Thanks for the dual-monitor feedback.  I think for our situation the best thing might be to swap the existing dual-boot HDD out for a spare, install 12.04, and see what happens.

---


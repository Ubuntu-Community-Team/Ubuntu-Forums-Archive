---
title: "Failed Install of Ubuntu 11.10 on new HP Pavilion"
date: 2012-03-10
forum: General Help
---

### Post by ddjolley on 2012-03-10
I am trying to install Ubuntu 11.10 on a new HP Pavilion desktop using a CD that I created from a downloaded iso.  The boot process does not complete -- it hangs.  It does not always hang at the same point. Sometimes I get past the point where I first see the cursor arrow for the GUI and it hangs at a blank black screen.  Other times, I don't get that far with the hang occurring at some arbitrary point like "Starting Bluetooth".  I used the boot CD in question to successfully boot an older HP computer.  For kicks, I tried booting Ubuntu 11.4 on the HP Pavilion because I happen to have a CD provided by the Ubuntu project for thar version.  It doesn't hang.  It consistently takes me to a shell prompt.  Any ideas?  Thanks for any input.

           ... doug

---

### Post by Mr Nemo on 2012-03-10
First thing i'd do is download another copy, preferably from a torrent, and then burn it to a disc again. I've had that happen to me a few times and a new copy fixed it. If that doesn't fix it respond back.

---

### Post by ddjolley on 2012-03-11
> download another copy, preferably from a torrent,  and then burn it to a disc again.
> I've had that happen to me a few times  and a new copy fixed it. 

But, I've already tried 2 CDs neither of which work on the new problem machine and both of which work on another "older" machine.  Additionally, one of the CDs is from the Ubuntu project.  I can try another download and burn; but, I don't think the evidence supports the notion of two faulty CDs.  I think that the evidence strongly points to the culprit being some sort of a difference between the brand new machine and the older machine (e.g., the CD drive on the new machine).

Thanks.

         ... doug

---

### Post by Mark Phelps on 2012-03-11
Some of the new Pavilions have "Hybrid Graphics" -- two GPUs, the use of which switches on demand in response to what you're doing with the PC.  Linux can't handle that well, and in some cases, results in no display.

---

### Post by ddjolley on 2012-03-11
The 2-gpu theory sounds reasonable.  Is there a work-around; or, am I just dead? 

Thanks.

     ... doug

---

### Post by Mark Phelps on 2012-03-12
If the Pavilion is a DV7, the following might work:

[http://ubuntuforums.org/showthread.php?t=1917897]("http://ubuntuforums.org/showthread.php?t=1917897")

---


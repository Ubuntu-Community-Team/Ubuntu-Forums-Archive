---
title: "Syncing Palm Centro in Ubuntu"
date: 2009-09-12
forum: General Help
---

### Post by tacantara on 2009-09-12
I've checked posts on this forum and researched this problem on Google.  Here's my dilemma for today:

I am attempting to sync my Palm Centro phone to my laptop.  I installed J-Pilot from the repository and set up the bluetooth on my machine to sync with the Centro.  All appears well, except for the sync part.  I get this error message on my phone when I attempt to sync:  ```
 Unable to initiate HotSync operation because the port is in use by another application.
```I've looked at the settings in J-Pilot.  I can't seem to pin down what the device name should be for bluetooth.  I see several USB names and such, but nothing specific for bluetooth.  I think this may be the problem.  I know that the computer recognizes the sync, as I was able to pull this up on hcitool scan:  ```
 Scanning ...
    00:1D:FE:26:E7:7C    PalmUser70
```Does anyone have any experience with syncing Palm devices, and if so, does anyone have any advice?

---

### Post by tacantara on 2009-09-12
Bump!

---

### Post by CyborgHunter on 2009-10-28
I have this same problem with my Centro and Kubuntu 9.04.

I believe the problem is on the Kubuntu side FWIIW.

I found this thread: [http://forums.palmone.com/palm/board/message?board.id=windows_hotsync&view=by_date_ascending&message.id=41720](http://forums.palmone.com/palm/board/message?board.id=windows_hotsync&view=by_date_ascending&message.id=41720)  

Read the 6th post down. It describes how to fix the problem by setting up a com port on MS-Windows.
Ya, I know we're running Linux, but the point is the problem is getting a com port set up on the PC to receive incoming signals over bluetooth. 
It may have something to do with "rfcomm". 

I'm Trying to figure out how to set-up a com port attached to bluetooth on Kubuntu. It may have something to do with "rfcomm". If I figure anything out I'll post here.

Good Luck.

---

### Post by tacantara on 2009-10-28
Thanks for the reply :)  I've decided to forgo the bluetooth connection and go with the USB.  It works like a charm now, and I'm using jPilot without any problems.  Not exactly what I was looking to do, but it still gets the job done.  I will check the link you sent though, and see if I can have the best of both worlds.

---

### Post by andrewsimpson on 2009-12-03
> **tacantara said:**
> I've checked posts on this forum and researched this problem on Google.  Here's my dilemma for today:

I am attempting to sync my Palm Centro phone to my laptop.  I installed J-Pilot from the repository and set up the bluetooth on my machine to sync with the Centro.  All appears well, except for the sync part.  I get this error message on my phone when I attempt to sync:  ```
 Unable to initiate HotSync operation because the port is in use by another application.
```I've looked at the settings in J-Pilot.  I can't seem to pin down what the device name should be for bluetooth.  I see several USB names and such, but nothing specific for bluetooth.  I think this may be the problem.

After much Googling and tearing my hair out, I got this working very easily.

Most sites tell you to set 'other' and 'net:any' in J-pilot, however this just gave the error message above.  The correct answer is to set J-pilot to 'other' and 'bt:'.

This [pilot-link howto]("http://howto.pilot-link.org/bluesync/") shows how to set the Palm end too.

Don't try and play with the rfcomm.conf file or set up ppp; none of this is required.

---

### Post by CyborgHunter on 2009-12-08
That works andrewsimpson.
I just sync'd my Centro to my Kubuntu 9.10 PC using bluetooth and your advice.

I *was* able to able to get it to sync once using net:any,
but I haven't been able to repeat it.
Now that this works, I probably won't bother trying to use net:any again.

Thanks!

---

### Post by Macaboy on 2012-06-04
I'm embarassed to say how many hours I've searched and attempted to Hotsync my ancient Palm TX with my newfound OS...Unbuntu 12.04. Two tiny letters "bt:" under J-Pilot preferences after clicking "other" and voila...success!  Thank you ALL!

---

### Post by overdrank on 2012-06-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


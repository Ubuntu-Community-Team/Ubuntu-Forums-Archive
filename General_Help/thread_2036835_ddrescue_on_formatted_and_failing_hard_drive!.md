---
title: "ddrescue on formatted and failing hard drive!"
date: 2012-08-03
forum: General Help
---

### Post by Accessory on 2012-08-03
First, I should point out I'm very new to Ubuntu and Linux. Trying my best, but a lot to learn.
 
I'm working on a drive from an Acer laptop. The owner was having problems and attempted to run the Acer restore - computer was unstable with the restore and failed to complete. Then, the owner realized they needed the data on the drive!
 
I have determined the drive is crashing - damaged sectors etc. So we are working with a crashing hard drive that has been reformatted - pretty tough.
 
I would like to make a clone of the drive then run rescue tools to retrieve the deleted data of the formatted drive. Will ddrescue allow me to recover formatted/deleted data once the clone is complete? Does it copy only current data, or will it copy sector by sector RAW data for recovery?
 
I actually started the clone, and it looks like it will take a long time to complete. Don't want to wait for something I can't use, so hopefully someone can confirm that I can recover deleted/formatted data from a ddrescue clone.
 
I'm running Ubuntu and the command I used is: 
sudo ddrescue -r3 /dev/(source drive) /dev/(destination drive) -f -R recovery.log
 
I used the -R switch because most of the damage is in the beginning of the drive. Thought I would reverse the process.
 
Thanks for your help!

---

### Post by Paqman on 2012-08-03
I've never used ddrescue itself, but in general dd copies every single bit of data, including everything in "free" space. So it's a good tool for data recovery.

---

### Post by Accessory on 2012-08-03
Thanks. Glad to hear that I'll be able to run recovery tools for deleted/formatted data once the clone is complete.
 
The drive that needs recovery is a 250GB. Running ddrescue in reverse mode. So far, overnight, it doesn't seem to be doing much.
 
Info: 
Rescued: 0B, errsize: 0B errors:0
Current Status
Rescued: 0B, errsize: 250GB, current rate: 0B/s
ipos: 225631 MB, errors: 1, average rate: 0B/s
opos: 225631MB, time from last successful read: 11.4 h
splitting failed blocks...
 
 
Is this normal? Looks like the ipos and opos is moving from 250 down, but no current rate of data and no rescued data yet. Is this because there is no data at the end of the drive? Will data start coming in once ddrescue gets to the earlier part? Or is this just wrong and I should try different settings.
 
Thank you!

---

### Post by Grenage on 2012-08-03
dd, as mentioned, copies whole chunks - it's not concerned with what's on the the sectors.  If it can't read a particular chunk, it writes blank data; so if you are reading a 4MB block, and a small amount of that is unreadable, the whole 4MB chunk is written blank.

Where dd_rescue differs, is that if a chunk cannot be cleanly read, it reduces the chunk size and tries again, then does the same again.  That way, when data cannot be copied across, you're only missing out on the pieces that couldn't be read.  That's my understanding from reading up on the tool a long time ago.

Given that output, it doesn't look like it's having much luck; it looks more like it can't really read the drive at all.

---


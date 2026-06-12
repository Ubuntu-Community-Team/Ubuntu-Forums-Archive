---
title: "cp hangs"
date: 2011-01-06
forum: General Help
---

### Post by Enigm4 on 2011-01-06
I recently installed Linux to run a few Linux based tools on a disk images I have, and I can't seem to copy the disk image over to my ext3 partition.
 
The particular distibution I'm using is BackTrack 4 r2, which is Ubuntu based. I can't seem to find specifically which version of Ubuntu is being used.
The disk image is 108GB. It is currently located on a NTFS partition on a SATA hard drive connected directly to the computer.
The ext3 partition is located on a second SATA hard drive connected to the same computer. It has 200GB total. I do not remember exactly how much free space it had but "df -h" showed a lot more than 108GB.
The computer has 4GB of RAM and I gave it 8GB of swap space.
 
At this point it has been running for more than 12 hours. This is far longer than I would expect it to take had I been copying the file under Windows. How ever I do not have much experience with Linux, so if it's supose to take this long please let me know. I am planning on letting it run until I wake up tomorrow.
 
"cp -v" hasn't been very verbose at all. The only sign I have that indicates the computer is still trying to do something is the HDD light on my chasis that has stayed lit this whole time.
 
Any insight on this situation is appreciated.

---

### Post by MaxIBoy on 2011-01-06
Yeah, expect it to take a while. The swap might actually be slowing it down, if it's on one of the same drives as the source or destination. Just one of the downsides of swap, normally it's a good thing to have except for situations like this. 

In the future, you might want to run ```
sudo swapoff -a
``` before a very big copy (say, more than 20 gigs,) then ```
sudo swapon -a
``` when it's done. However, that does mean you will probably not want to use the computer for anything else while the copy happens (if you don't have swap enabled, and you start to run out of RAM, random processes start getting killed, possibly even cp itself, which would suck.) DO NOT disable swap while your RAM usage is *currently* very high, that's like playing musical chairs with your RAM.

cp -v just lists each file it copies; since you're only copying one file it won't be of much use. 

You can see how much progress has been made by checking the size of the destination file, which will be approximately the size of how much has been copied so far (give or take a few gigs.)

---

### Post by Enigm4 on 2011-01-06
I have the gui turned off because I thought maybe it'll run faster this way. Is there a way for me to check the destination file without canceling the cp command?

If not, do you think I've waiting long enough that I should just stop cp from running?  How long would you expect 100GB to take?

---

### Post by MaxIBoy on 2011-01-06
Honestly, I have no idea on the time estimate. Seeing the size of the file would help you to judge whether you want to call it quits. (There are a few ways of speeding up the copying, but if you're already more than halfway done it's not worth it.)

Try switching to another virtual terminal so you can have another command line. You switch between them by hitting alt+F#, for example alt+F1 is the first one (the one you are probably using now.)

---

### Post by Enigm4 on 2011-01-06
Alright thanks man.  With the alt+f# thing I can at least see if the thing is progressing now.  Looks like it's just going really slow.  Good thing I didn't cancel it.  Thanks again.

---


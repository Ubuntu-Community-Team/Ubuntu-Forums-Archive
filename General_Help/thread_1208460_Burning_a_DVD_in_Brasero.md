---
title: "Burning a DVD in Brasero"
date: 2009-07-09
forum: General Help
---

### Post by Daniel1994 on 2009-07-09
I downloaded a .avi movie I would like to burn to a dvd, but when I get to the actual burning, this shows up:
[ATTACH]120477[/ATTACH]
My computer is norwegian, so I'll translate:
"Please replace the disk with a supported CD or DVD
It's not possible to write with the current set of plugins"

Which plugins do I need?

appreciate any help.

---

### Post by Cheesemill on 2009-07-09
If you're looking to burn an .avi so it can be played back on a regular DVD player the video needs to be transcoded first. I recommend using [DeVeDe]("apt:devede").

---

### Post by Daniel1994 on 2009-07-09
I am trying DeVeDe right now, it looks good. 
But it is very slow...

---

### Post by Cheesemill on 2009-07-09
That's because it has to re-encode the entire video stream from .avi to DVD format.
This can take from 30 minutes to several hours depending on the speed of your computer.

---

### Post by Daniel1994 on 2009-07-09
No..DeVeDe did not work. I still get the same problem.
I'm posting the end of the logfile:
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
    growisofs
    -use-the-force-luke=notray
    -use-the-force-luke=4gms
    -dvd-compat
    -speed=2
    -use-the-force-luke=tracksize:1060851
    -use-the-force-luke=tty
    -Z
    /dev/sr0=/home/daniel/Skrivebord/Movie/Movie.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/daniel/Skrivebord/Movie/Movie.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 2.5x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=5h/WRITE PROTECTED]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)


I still suspect some missing plugins, but I can't seem to find them in Synaptic. 
I still get the please replace the disk with a supported CD/DVD.

I don't get this...

---

### Post by Daniel1994 on 2009-07-09
Could it be my CD/DVD burner?

---

### Post by cbilljones on 2009-08-01
I just had this issue, it seems to be the disc itself; tried another brand(both cd-r) and its working fine.

---

### Post by Daniel1994 on 2009-08-03
Thanks, I'll try a different brand the next time.

---

### Post by sprilutsky on 2009-09-05
Here is how I went around this problem and found a workaround.

1. Open up a Brasero window/session, but leave it alone for a sec.
2. Open up a File Browser as a second Window/session
3. Drag and drop .avi file(s) from File Browser window into the Brasero Window
4. Click on "Burn" - you should not only see the correct DVD media, but also be able to burn avi format.

Let me know if it worked.

Thanks

---

### Post by Kezza69 on 2010-01-17
Thanks sprilutsky.

I've had the same probelm and just followed your advise. It worked just fine. Don't understand why 'drag n drop' lets you burn and using the GUI ADD button doesn't. Bizarre!!!

Thanks again..... good tip.

---


---
title: "All disks spin up every 10 hours---how do I find the culprit?"
date: 2011-07-10
forum: General Help
---

### Post by Blueshell on 2011-07-10
I'm running 10.10 with about 10 SATA disks attached.  If I spin them down with hdparm -Y, every disk that has a filesystem on it (but -not- disks that are partitioned but have no filesystem) spin up, simultaneously, about every 10 hours.  How do I find the culprit?  The machine is sitting effectively idle---I know it's not something I'm doing that's causing the spinups.

Is there some way to monitor -anything- that touches a particular block device?

My suspicion is that this might be the gnome low-disk-space warning daemon statting everything. (This -used- to be gnome-volume-manager, but I'm not sure where that code went when GVM was dropped in 10.10---how do I find that code? What package is it in?)

And if it -is- the disk-space monitor, how do I kill it dead?  Not just "don't tell me about disks", but "don't even bother looking".  I would -really- like these drives to spin down and -stay- down, possibly for days or weeks, until needed---not spin up every 10 hours until I either manually spin them down or until whatever I've set in hdparm spins them back down.

Thanks...

---

### Post by psusi on 2011-07-10
Are you using -y or -Y?  If the latter, then I am very surprised that it takes 10 hours.  The udisks daemon monitors the SMART status of the drives, and polling the SMART status causes the drive to spin up.  To avoid that, it skips the check if the drive is suspended ( -y ), but the very check to see if the drive is suspended causes it to wake up from sleep ( -Y ).  For this reason you should use -y.

---

### Post by Blueshell on 2011-07-10
Ugh.  Yes, I'm using -Y.  (a) I didn't realize udisk was doing this, and (b) I sorta assumed that anything touching the drives would -first- do hdparm -C (or the moral equivalent) -before- doing smartctl <something>.  What's the closest smartctl equivalent I can use for testing use of -y instead of -Y?  I find that even doing hdparm -y, if I then do smartctl -i, the drive goes from standby to active/idle, so if udisk is doing the same, it'll spin up the drive even from -y.  (And hdparm -Y always puts the drive in standby and not sleep, but I assumed this was just a limitation of hdparm---that hdparm -C can't tell the difference.)

Thanks...

---

### Post by Blueshell on 2011-07-10
Btw, yes, it does appear to take 10 hours, or rather be synchronized on 10-hour boundaries (no matter when I slept the drives).  I have many days of logging on this, where I had a script just dumping timestamped runs of hdparm -C over all the drives into a file every 30 minutes, and all the ones I slept stayed slept for hours at a time, then all simultaneously spun up.

What's the cleanest way of getting udisks to stop this?  do "udisks --inhibit-all-polling shell-script", where shell-script is just a program that sleeps forever?

---

### Post by Blueshell on 2011-07-10
Btw, if I determine it really is udisks-daemon that's doing this, I may file a bug report---it should call hdparm -C on the drive -first-, so as not to wake the drive up just to ask if it's sleeping.  (Otherwise, the daemon behaves like the typical hospital nurse... :)  Is there any reason it shouldn't already be doing this?

---

### Post by psusi on 2011-07-10
udisks does the equivalent of hdparm -C before checking the SMART status, but that causes the drive to spin up from deep sleep, which is why you need to use -y and not -Y.

---

### Post by Blueshell on 2011-07-11
Not on -my- system, it doesn't---that's how I tested things way back when I started sleeping the drives.  hdparm -Y /dev/sdm puts the drive to sleep.  At that point, I can issue hdparm -C /dev/sdm commands forever, and the drive state remains in standby.  It stays in standby until I issue a smartctl command or touch the drive's data itself (or until several hours go by and they all spin up simultaneously).

If udisks-daemon think it's checking, it must be checking in some different way, so that seems like a bug.

So, just to be clear, you're saying that pretty much any smartctl command should wake up the drive, so nothing must be allowed to invoke any smartctl command for any sleeping drive, -but- that hdparm -C will in general wake up a sleeping drive?  Because the latter behavior isn't happening for me, and if hdparm -C can do it, udisks should be able to do it, so it'd be nice to know if this is a real bug.

I'll try -y and see if that helps, but really, I'd rather put the drives in their minimum-power state and not just standby if I know I won't be using them for days.

If I don't want proactive SMART scanning, is there any reason not to use --inhibit-all-polling or to just kill the udisks-daemon process?  What launches it, btw?  A few minutes' investigation hasn't revealed that.

---

### Post by Blueshell on 2011-07-11
One more thing---is it in udisk's contract to check -all- drives, or all drives with mounted filesystems?  As I said in my first message, only drives with filesystems are getting spun up---I have two drives which are partitioned but on which I've never created a filesystem, and those aren't getting spun up.

---

### Post by Blueshell on 2011-07-11
One more datapoint:  By tailing kern.log, I can see that "hdparm -C" -is- side-effecting the state:  if I totally sleep the drive with -Y, and then do -C, kern.log reports an exception, wakes the drive up from sleep, and resets the SATA link.  However -the drive does not spin up-.  It's going from sleep to standby without a spinup.  I'm verifying that by listening to it---it has a very distinct spinup noise when I spin it up, and it doesn't make it.  smartctl -does- spin up the drive.

So yes, hdparm -C will unsleep a drive, but it won't spin it up.  If it's udisks that's spinning up these drives, it's not using hdparm -C to check first---whatever it's doing is unsleeping them -and- spinning them up.

I'm going to standby all drives with -y and see if they spin up in a while.  Even if that works, I'll probably try sleeping them with -Y and telling udisks to --inhibit-all-polling and see if they spin up then.

---

### Post by psusi on 2011-07-11
Have you enabled Power On in Standby?  Some drives can do this with hdparm, but my WD drives require a jumper to enable PoS.  As you noticed, whenever any command is issued, including hdparm -C, the link has to be reset and powered on to issue the command.  This usually results in the drive spinning up, but I suppose if you are using PoS, then it would, well, power on in standby.

Given that, and the 10 hour delay and the fact that it only happens on a disk with a mounted filesystem, that would indicate that it is not udisks.  What did you set the ext4 journal commit interval to?  That would be my next guess.

By the way, I have yet to see a drive that actually saves any more power in sleep than in standby.  The specifications are always identical, and my measurements of my drives confirm that.  I'm not sure why this is, because in theory, in sleep mode the drive is completely powered off, including the control logic, so it really should be using zero power.

---

### Post by Blueshell on 2011-07-11
I haven't explicitly enabled POS, so I suspect it's not on.  If you mean, "When power is applied to the drive, don't spin up"?  If so, that's not how these are configured---they're in a big hotswap chassis, and when I insert a drive, it spins up immediately.  They also all spin up immediately when I turn on the chassis, long before the BIOS has finished loading, though I don't think I've ever run a test with no CPU present, so the BIOS could e tickling them there.  (They're all Samsung HD204UI's, FWIW, though I have a couple of WD drives and a Seagate not currently plugged in that I could plug in if having different brands in there might tell us anything.)

Btw, all the drives with filesystems (and neither of the two without) spun up again overnight, even though they were slept with -y, so I now have 10 in active/idle and two in standby.

As for the ext4 commit interval, I haven't changed it.  Isn't it like 5s or 30s or something?  (I'm actually having considerable difficulty figuring out how to even ask this of ext4; dumpe2fs doesn't mention it, it's not showing up in /proc/mounts or /etc/mtab, the relevent lines from kern.log are long-gone because this machine has been up for two or three months, and web searches are drowned out by all the controversy of a couple years ago about ext3/ext4 differences in semantics.)  I could set some of the drives to read-only and see if that changes things...

Re power:  Hmm.  I could have sworn that a specifications PDF for this drive (which has apparently now moved somewhere else on Samsung's site) claimed different power, but their current HTML spec page does indeed now claim that both standby and sleep are 1W, compared to 5.1W idle.  So if I could only keep them from spinning up...

Is there some way to say, "log all PIDs that touch this block device" or something?  I could sit that on one of the unused drives and wait.  I've just (re-)remembered "echo 1 > /proc/sys/vm/block_dump", but a couple of these drives do get written to every half hour with many gigabytes of data; I'd rather set this for just one drive and not every drive in the system (which would also log those dmesg log lines themselves..).  Any way to do this, or do I have to take the machine entirely out of service?  Maybe I can use auditd or iotop or incron somehow, assuming the Ubuntu default kernel is compiled with the right options (like auditing).

---

### Post by psusi on 2011-07-11
If you didn't specify any commit interval in the mount options, then it is 5 seconds.  If you did not specify the noatime option, then reading a file will cause a write to the disk to update the timestamps.  I suggest you set these options.

You also might find blktrace useful.  Unlike the old proc block trace interface, it allows you to lock on to only one block device, and it provides much more detailed output to a binary log file that can be parsed later.

---

### Post by Blueshell on 2011-07-11
Yeah, they've got noatime:  "rw,noatime,barrier=1,data=ordered".  This is all on  2.6.35-28-generic 64-bit desktop build, not that that should matter.

But aha!  blktrace looks like just the ticket, judging from its manpage, and probably eaiser to configure than auditd, iotop, or incron for what I'm doing.  I'll give it a whirl and see what happens, and report back if I either figure it out, or don't.  Thank you!

---

### Post by Blueshell on 2011-07-13
Well, one unwelcome but quick result of using blktrace (actually, btrace -s) is that what was spinning up the drives at least some of the time is ls!  Specifically, the ls used in a big block of code in /etc/cron.daily/standard, which is checking every day to see if files have appeared in lost+found.  Since in theory this should only happen if I'm running fsck, which I know I'm doing, I certainly don't want that happening, and I -really- don't want it happening on non-spun-up disks.  I've disabled the entire block of code for now and will see if anything else spins up the disks.  I'm also going to file a bug report on this:  standard should, at the very least, use hdparm -C to check the drive state and not spin them up if they're in standby.  (Though I question the whole utility of this little cronjob, and mention that even with hdparm -C, it would make it impossible to really -sleep- a drive and not -standby- it as long as standard checks for this.)

---

### Post by runesvend on 2011-09-06
So did it work, removing the code in /etc/cron.daily/standard? I'm facing the same problem. Although way less than 10 hours seems to pass between my HDDs being woken up.

---

### Post by Blueshell on 2011-09-07
Yup, it worked.  I also think my "every 10 hours" must have been some sort of artifact of when I booted and/or looked at what was going on, despite multiple boots and multiple looks, since obviously cron.daily runs only once a day.  (And if I'd really figured out that it was once a day, that would have considerably narrowed my suspects!  cron.daily would of course have been the first place I looked.)  I simply commented out everything in that file from the comment saying "Check to see if any files are in lost+found directories" down to and -not- including "Clean up lockfile" and my disks stopped getting spontaneously spun up.

---

### Post by runesvend on 2011-09-07
Cool, thanks for finding out. I initially just removed the executable bit from the file, so it didn't run at all. But now I can see there seems to be some non-trivial code in there, like back ups and such. So I commented out the code you suggested.

By the way, did you create a bug report about this? I'd like to CC myself to that bug so I can - at some point - enable this lost+found checking.

---

### Post by Blueshell on 2011-09-21
Not yet, but I really should; thanks for the reminder (and apologies for the lateness of this response).

---


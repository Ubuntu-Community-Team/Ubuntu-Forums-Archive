---
title: "Increment file timestamp by one hour"
date: 2012-04-18
forum: General Help
---

### Post by alawson on 2012-04-18
Hi,

Does anybody know of an easy way to increment the timestamp of a bunch of files & directories by one hour?

My backups are stored on NTFS volumes, and somehow since the clocks changed the other week rsync is now confused and thinks it's needs to recopy about a terabyte.

I'm not even in a timezone where the clocks change. It's pretty annoying.

A script using touch should do it, but my shell scripting isn't really up to it.

Anybody able to figure this out quickly?

Thanks!

---

### Post by lisati on 2012-04-18
I'm confused: you're not in a time zone where your clocks change, but your clocks changed?

---

### Post by alawson on 2012-04-18
> **lisati said:**
> I'm confused: you're not in a time zone where your clocks change, but your clocks changed?

No, the clocks didn't change. But the timestamps on all the files on the NTFS volumes did - in relation to system time.

I haven't really figured it out, but I know that NTFS timestamps are stored in the current timezone, whereas other FSs store the timestamp in UTC and apply a modifier.

I'm in Queensland - we don't have DST here. A little further south in New South Wales (the same timezone) they do have have DST. This causes much confusion twice a year when the clocks change in NSW but not in QLD.

So I'm guessing it's something to do with that.

If I fix the timestamps this time, I can use rsync to make sure that my backups are good, and the next time around reformat the backup disks with a sensible FS.

Hmmm, sudden thought. The original is a Drobo NAS, which probably doesn't know about the timezone issue between QLD and NSW. So the original probably changed, not the backup.

Either way - the goal is to decommission the Drobo 'cos I need it's disks somewhere else. So fixing the timestamps solvs my immediate problem, and I can then take steps to ensure it doesn't occur again.

---

### Post by lisati on 2012-04-19
Ah, that makes better sense to me now. I have some vague recollection of encountering situations on my own gear where the system time (i.e. the clock) on one of my machines was being handled differently by Windows and Ubuntu a couple of years ago. I'll have to defer to the wisdom of other users for now.

---

### Post by conradin on 2012-04-19
to alter timestamps use the touch command.
$man touch fmi.

---


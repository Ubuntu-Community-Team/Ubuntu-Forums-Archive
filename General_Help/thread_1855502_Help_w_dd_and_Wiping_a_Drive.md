---
title: "Help w/ dd and Wiping a Drive"
date: 2011-10-06
forum: General Help
---

### Post by TheGuvernor on 2011-10-06
Ok I have two drives in my machine that I wanted to wipe. I dropped in Ubuntu live cd and brought up a terminal.

Then I typed in:

sudo dd if=/dev/zero of=/dev/sdb

After hours of a blinking cursor I finally got a command prompt. And I'm assuming that means it completed successfully although it said it wrote 277 GB even though the drive is 500 GB???

When I had finished with sdb I started the same command on sda. The problem this time is after hours I simply got a black screen. I could see the cursor but no desktop and no terminal. Any idea why this would happen?

And lastly. Is there a flag I can set for a progress bar?

EDIT: I'll also add the cursor I could see was not a normal cursor. It was a down arrow with a line under it, if that means anything.

---

### Post by Grenage on 2011-10-06
Here's a handy dd tip; from another terminal, type this:

```
pkill -USR1 dd
```

Then look at the terminal running dd - it should have output the %.

---

### Post by WasMeHere on 2011-10-06
At first glance it looks like you use the correct command line. But the output should state the real size of the disk. I have used dd hundreds of times, and I would not be satisfied with your results.

- I usually run dd from a live disk, but it should be OK to run from an installed system on sda and write on sdb sdc ...

- The drives must _*not*_ be mounted during dd operations on drives or partitions.

- Are you sure that you selected the drive you wanted to wipe, that it really is sdb? Is there any drive of 277 GB? (maybe a stupid question).

So firstly you have to identify which is the source disk and which is the target  disk. You can usually identify this using the output from e.g. ```
sudo fdisk -lu
``` The result should be disk device identifiers. Once you've established which is the source drive and which is the target drive, you can then proceed to cloning/wiping the disk using the "dd" command.

- tip: I add _bs=4096_ to the dd command to improve the speed.

- no progress bar but you can use the kill command to get information of the progress e.g. every 5 minutes:```
sudo -s
dd if=/dev/zero of=/dev/sdb bs=4096 & pid=$!
while kill -USR1 $pid; do sleep 300; done

```

---

### Post by WasMeHere on 2011-10-06
... and the second one, when you got a black screen: did you wipe the disk with the active operating system? If you wanted to wipe it, OK, otherwise you need a good backup. Anyway, I suggest that you boot from a live disk and try again.

Good luck
Olle

---

### Post by TheGuvernor on 2011-10-06
Hi

I did sudo fdisk -l but did not add the u. It gave me the names of sda and sdb. I wanted to make sure they weren't hda/b.

Forgive my ignorance but what is the u flag for?

After that i booted into bios and set my cd/dvd drive as the first boot device, popped in ubuntu, clicked "try ubuntu", hit CTRL+ALT+T to bring up a terminal and typed the command as stated above.

I'm assuming the internal drives weren't mounted and I was working from the live disk and ram. Should I have given a absolute path to the zero or random script on the disk? could it be that it pulled the /dev/zero from the hard disk and wrote zeros to the free space?

And BTW, thanks to you both for the killer tips. They are going in my Linux Journal.

EDIT: forgot to answer your other question. The drive is def a 500 gig'r

---

### Post by TheGuvernor on 2011-10-06
> **Olle Wiklund said:**
> ... and the second one, when you got a black screen: did you wipe the disk with the active operating system? If you wanted to wipe it, OK, otherwise you need a good backup. Anyway, I suggest that you boot from a live disk and try again.

Good luck
Olle

Did it from the disk. Used the exact method described above.

---

### Post by speedwlk on 2011-10-06
You can try using dcfldd instead of dd. Using the statusinterval option, you can track the progress.

---

### Post by qiet72 on 2011-10-06
Hi,

I do the following as root when I want to wipe a disk:

pv -s `fdisk -l /dev/sdb 2>/dev/null | grep "Disk /"|cut -d' ' -f5` /dev/zero >/dev/sdb

The progress bar looks like this:

1,55GB 0:00:19 [  24MB/s] [=======>                   ] 81% ETA 0:00:04

br,
Quinn Plattel

---

### Post by WasMeHere on 2011-10-06
> **TheGuvernor said:**
> Hi ...

Forgive my ignorance but what is the u flag for?
[COLOR="Red"]Many people prefer listing partition table size in sectors instead of cylinders.[/COLOR]

After that i booted into bios and set my cd/dvd drive as the first boot device, popped in ubuntu, clicked "try ubuntu", hit CTRL+ALT+T to bring up a terminal and typed the command as stated above.

I'm assuming the internal drives weren't mounted and I was working from the live disk and ram. [COLOR="Red"]It is OK[/COLOR]. Should I have given a absolute path to the zero or random script on the disk? could it be that it pulled the /dev/zero from the hard disk and wrote zeros to the free space? [COLOR="Red"]It is OK[/COLOR]

And BTW, thanks to you both for the killer tips. They are going in my Linux Journal.

EDIT: forgot to answer your other question. The drive is def a 500 gig'r

So there are still big questionmarks to be straightened

---

### Post by WasMeHere on 2011-10-06
Another possibility, why the wiping did not finish:

There might be errors on the disk(s). Have you tested that? *ddrescue* is a good tool that can identify errors and save whatever is readable. It can skip over bad sectors. By default *dd* stops at bad sectors, and it is ***not*** good at skipping

The manual pages ```
info ddrescue
``` are very well written. Maybe someone else can suggest a good tool to find bad sectors.

---

### Post by TheGuvernor on 2011-10-06
> **Olle Wiklund said:**
> Another possibility, why the wiping did not finish:

There might be errors on the disk(s). Have you tested that? *ddrescue* is a good tool that can identify errors and save whatever is readable. It can skip over bad sectors. By default *dd* stops at bad sectors, and it is ***not*** good at skipping

The manual pages ```
info ddrescue
``` are very well written. Maybe someone else can suggest a good tool to find bad sectors.

You're psychic! I was just wondering if maybe it hit a bad sector. I'll give this a try. Also does the live cd have S.M.A.R.T. support? If you don't know, no biggie.

---

### Post by WasMeHere on 2011-10-06
I think so, look at the menu 'System -- Settings -- Disk Utility' (actually the program is called *palimpsest* which shows SMART status).

*info ddrescue*:
> Example 2: Wipe only the good sectors, leaving the bad sectors alone.
This way, the drive will still test bad (i.e., with unreadable sectors).
This is the fastest way of wiping a failing drive, and is specially
useful when sending the drive back to the manufacturer for warranty
replacement.

     ```
ddrescue --fill=+ /dev/zero bad_drive logfile
```

---


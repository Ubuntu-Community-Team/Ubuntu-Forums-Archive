---
title: "Kubuntu installation Kernel Panic"
date: 2006-03-07
forum: General Help
---

### Post by fnasib on 2006-03-07
Hi All,

I have joined the Kubuntu Community. I am having some trouble with installing kubuntu.

Basically I will get this thread started.:

Problem:

I get to 77% of installing the packages (after the requested reboot). The system then hangs and errors with the following message:

[COLOR="Red"][4295292.478000] Kernel panic - not syncing.Waiting list traversal[/COLOR]

This happens at the stage where the system is configuring ttf-bitstream-vera.
I have had the installation at 80% but I didn't record anything at the time.

My system configuration is:

an overclocked pIII 600E to a pIII 800.
ISA sound card 16bit awe32
512mb pc133 SDRAM
AOPEN ax6b motherboard
wd 250gb drive
21" IBM p260
adaptec 2940uw scsi card
TEAC scsi cdrom
mitsui scsi burner
LG 4167B DVD burner combo drive

Now this drive was previously my external storage drive but I had som blocking errors on due to improper shutdowns when I was using it on windows. I copied all the data to a new drive and reformatted this 250gb drive.

This is the second clean install and both times I am coming across this error.
The drive seems to be fine as I have formatted it previously with XP twice and I have run chkdsk /R /F on the drive and I have found no problems.

I have also ran memtest but that got only to 37% pass where everything hung ... hmmm ... but I have been using this memory on windows for over 3years without a fuss. I am not sure if it is memory or not.

I have booted with the live DVD and it came up with one problem which was the display had lines passing through it. After seeing what the live cd had to offer, I thought I have to have this installed but to no avail I am at a point where I need help.

Can anyone please help???

Thanks in advance
Faiyaz

---

### Post by incubus on 2006-03-09
Dear Faiyaz,

Welcome aboard.
So it seems that you have a couple of problems there:
1. The kernel panic. Have you tried installing again? Does it crash at the exact same point? You can also do ALT+F4 to see more details. Could it be some problem with the CD/DVD?

2. The problem with your hard drive and the memory. You know that when a disk decides to die, there not much that we can do about it, even if scandisk says otherwise. I would still run a couple of tests to make sure this is not the case. If you see some strange misbehavior, don't trust the disk anymore.

About the memory, if you have experience you could get the stick and user a pencil eraser to clean it. Are you sure your power supply has been working well?

incubus

---

### Post by jerrykenny on 2006-03-09
I had a similar problem when a Kubuntu download I had gotten using the wget command paused halfway ( the target partition was full  -  doh )  so I made some space, and resumed the wget download . . . . any disc I cut from that download just would not install !

Also you may a bad-memory module, boot into your install disk, and at the boot prompt type

memtest

and hit enter, leave it a while, this will check your mem0modules for you . . . leave it running a good while.

---


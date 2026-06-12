---
title: "Sync/Backup Tutor Needed"
date: 2009-12-29
forum: General Help
---

### Post by TetonsGulf on 2009-12-29
So, right now I'm formatting a brand spanking new USB drive to remove the manufacturers software since it isn't so Linux friendly. I've had a USB drive in the past that I would use to store a copy of my non-system data so I had something to fall back on if my HD went bad. My last drive did what I wanted, but it has gone to the big recycle heap in the sky due to a broken connection and I want to automate the process for the shiny new drive. Which is why I'm here...

First of all, what is the difference between "Sync" and "Backup"? They must be different, but how? To me, I want to sync files so I have a backup. I'm not looking to restore a system, I'm looking for redundancy in case of a failure. If this isn't the right way to look at things, someone help me out please.

What I'd like to accomplish is:
[LIST]
[*]get away from copy/paste of gigs of data
[*]backup music/pictures/document and other folders (and subfolders), writing only the changes, and requiring some type of verification before removing files that no longer exist in the "source" folders, to the USB drive
[*]perform those actions when I plug the drive in or when I want to remove the drive (I have no preference here), but not really on a schedule since the device will not be left mounted
[*]use NTFS file system so I can access the data from a PC or Mac if the need presents itself
[*]not use an image or a snapshot for my archive, thus only copying what I as the user consider the "important" files. I have no fear of re/installing an OS and tinkering around to get it how I want it. What I am afraid of is losing years email, pictures, tax papers, targeted versions of resumes, and music.
[*]maintain a partition on the USB drive that will not be used for sync and cannot be deleted during the process as I have a few PC items I'd like to have a copy of that I don't have on my Ub drive.
[/LIST]

I've seen a ton of sites that have recommendations on this or that for how to go about parts of my needs, but I've found nothing that shows me how to do it all, and I don't know how to go about stitching it all together.

My hope is that someone here knows how to do this, or has done this very thing, and is willing to teach me how and why it works, making me happy and a smarter user in the process!

I'm not afraid of the terminal and I don't need to have a GUI solution, but I'm not going to gripe if a graphical solution does what I want it to either.

What I need, is a tutor...

---

### Post by dcstar on 2009-12-30
> **TetonsGulf said:**
> 
........
First of all, what is the difference between "Sync" and "Backup"? They must be different, but how? To me, I want to sync files so I have a backup. I'm not looking to restore a system, I'm looking for redundancy in case of a failure. If this isn't the right way to look at things, someone help me out please.

What I'd like to accomplish is:
[LIST]
[*]get away from copy/paste of gigs of data
[*]backup music/pictures/document and other folders (and subfolders), writing only the changes, and requiring some type of verification before removing files that no longer exist in the "source" folders, to the USB drive
[*]perform those actions when I plug the drive in or when I want to remove the drive (I have no preference here), but not really on a schedule since the device will not be left mounted
[*]use NTFS file system so I can access the data from a PC or Mac if the need presents itself
[*]not use an image or a snapshot for my archive, thus only copying what I as the user consider the "important" files. I have no fear of re/installing an OS and tinkering around to get it how I want it. What I am afraid of is losing years email, pictures, tax papers, targeted versions of resumes, and music.
[*]maintain a partition on the USB drive that will not be used for sync and cannot be deleted during the process as I have a few PC items I'd like to have a copy of that I don't have on my Ub drive.
[/LIST]
.........
I'm not afraid of the terminal and I don't need to have a GUI solution, but I'm not going to gripe if a graphical solution does what I want it to either.

A "Sync" makes both things the same, a "Backup" just adds (changed) files from one place to the other.

Look at the Unison package for a GUI way of keeping things in sync.

---

### Post by TetonsGulf on 2009-12-30
Unison was my first choice as well, not too robust and gets what I want done started. I have set the basics of which folders, and performed the first sync, so I'm on the right path to what I want to accomplish.

Anyone have ideas on how to string together the actions of the Unison profiles so they happen one after the other without having to launch each one with the GUI? I would think a script could be written to do it, but I haven't a clue how to go about that.

Also, I would like to believe there is a way to launch a program upon mounting a drive, and I'd like to set something up to launch this specifically when this drive is mounted. Any direction here from the group?

Thanks for the tip dcstar, I'm headed in the right direction.

---

### Post by TetonsGulf on 2009-12-31
Okay, I have the multiple folders but not every folder problem figured out, now looking for some guidance on how to initiate Unison when a particular USB drive is mounted.

Anyone have something like that going that wants to point me in the right direction?

---


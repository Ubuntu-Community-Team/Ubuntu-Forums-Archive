---
title: "Backup solutions..."
date: 2011-02-23
forum: General Help
---

### Post by Tu1J4kXk8NUhMz on 2011-02-23
This is less of a question and more of a request for sharing. I find that there are so many different solutions for backing up data, so I thought it might be cool to share those solutions. Perhaps we can inspire someone on how to do their own backup.

Alright, so please provide the following info:

**USES**: What do you use your computer for / what do you do?
**OPERATING SYSTEM(S)**: What OSes do you use? Do you Dual/Triple/etc. Boot?
**HOW**: Describe your backup solution for as many of the OSes as you like. Please let us know why you do it this way, and if you have any issues with your current process.
**(*Optional*) MEDIA**: What media do you backup to? How many do you have?



I'll go first...

**USES**: I am a freelance graphic designer and 3D digital artist.

**OPERATING SYSTEMS**: Mac OS X and Windows 7. I'll probably set up another laptop with Ubuntu Studio once I start working on my open source workflow/pipeline.

**HOW**:

I backup the entirety of my Mac OS X partition using Time Machine onto an external HDD. As far as I'm concerned, you can't do much better on a Mac than Time Machine. I backup extra important data using iBackup, both to an external and to elsewhere on my OS X partition. I do this because some of that info can become corrupt while using it (like profiles or whatnot), and it's nice to have an extra readily available. I'm considering throwing Carbon Copy Cloner into the mix, but don't know what media I'd backup to if I did this.

For Windows 7, I backup to an external HDD using Windows Backup & Restore. This is mostly due to reluctance and laziness to finding better backup software, and would love to find a better software option (preferably Open Source). I've previously used Nero Backup, but lost the CD. For a short while I used Areca-Backup, but it's a bit too technical, and doesn't quite have the functionality I'm looking for. I'm toying with doing some combination of image backup paired with a user files backup.

I think my biggest issue with either of these solutions is setting up a schedule. Time Machine only bugs you if you haven't backed up in 10 days, and iBackup doesn't even try unless the media is hooked up. The same can be said about Windows Backup & Restore, though since setting that up I don't even think I've gotten a reminder. I'd love some sort of fool proof scheduling or reminder software so I don't have to leave my externals hooked up and on forever and ever.

**MEDIA**: I have two 3.5" HDD which I do most of my backups to. I also have a small handful of 2.5" externals and DVDs which I manually backup anything overly important to (mostly projects and multimedia files).

Please share! Opinions and feedback are, of course, quite welcome!

---

### Post by Tu1J4kXk8NUhMz on 2011-02-25
Bump...

---

### Post by dino99 on 2011-02-25
backintime:

Back In Time is a framework for rsync, diff and cron for the purpose of
taking snapshots and backups of specified folders. It minimizes disk space use
by taking a snapshot only if the directory has been changed, and hard links
for unmodified files if it has. The user can schedule regular backups using
cron.

---


---
title: "Data recovery, yet another story"
date: 2011-02-17
forum: General Help
---

### Post by RicardoSantos on 2011-02-17
Hello, everyone, I'm having a hard time trying to recover my lost data on Windows Vista and I decided to write searching for any thoughts, if this was already solved, please let me know, I searched the forum and found a few solutions, but none of them worked for me.

I had Windows Vista installed on my computer and a driver was corruted, I tried to use the repair windows vista option from the CD and the damn thing just formatted the HD in the blink of an eye and started to copy the files all over again.

I shut down the computer to preserve my precious files, but my disk was already erased and approximately 10MB were already written on the disk. I don't want to write more to the HD as it could overrite partially (or completely) some files.

In the hope to recover anything, I tried to use Ubuntu Live USB (created by Lili) to recover my files. I used the ntfsundelete tool, but it only shows the current files that are on the HD, ad I cant use any more software, because I can't find my NTFS partition on /dev.

Is there any tools that can be used to scan the HD searching for the files other than ntfsundelete? Or am I doing it wrong?

I am using the Ubuntu Netbook distro running live on a USB stick and I have 3 GB of persistent data space. I have not installed anything yet and I am kind of a noob on linux in general and ubuntu in particular.

My computer is a laptop with a Core 2 Duo processor, 2GB RAM and 160 HD.

---

### Post by quixote on 2011-02-19
Yeah, I don't know why they call those things "recovery" disks when all they do is erase everything you have!  That may have written a new partition table, which means that even though most of your files are still on the computer, only a direct disk read can get at them. That makes recovery pretty tedious, but not impossible. Linux systems put that information at several places on the disk, so your chances of recovery are better, but I don't think Vista or Win7 do that.  I know XP doesn't.

The best tools I've found for data recovery are [testdisk]("http://www.howtoforge.com/data_recovery_with_testdisk") and [photorec]("http://www.psychocats.net/ubuntucat/recoverdeletedfiles/").  Is that what you've already tried that didn't work?

Give us a brief rundown of what you've done and what happened.  Then it'll be easier to find a solution.

---


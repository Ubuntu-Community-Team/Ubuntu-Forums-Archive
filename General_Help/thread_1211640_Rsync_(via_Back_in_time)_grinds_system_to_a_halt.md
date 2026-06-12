---
title: "Rsync (via Back in time) grinds system to a halt"
date: 2009-07-12
forum: General Help
---

### Post by Zeedok on 2009-07-12
I am trying to sort out the best automated back-up system for my PhD data (read mission critical!!).

I am using DropBox, which is great, but in the interests of multiple redundant strategies I have been creating weekly archives which are copied to an external hard drive (which stays at home).  Recently Fileroller has been taking ages to create the archives - enough that I have been putting archiving off - which means that my current approach needs to change.  Ideally, I would also like to backup my home directory as well (my data is on a separate partition) but this is too time consuming using my current strategy.

My data is getting larger (2 main directories, each about 1.2GB - both are on a single NTFS partition) and more complex (few thousand files and multiple sub-directories).  I have been aware of rsync for some time, but being a GUI junky I have put off implementing it, until I discovered "back in time" that is.

I have successfully installed back in time with the [Ubuntu Geek instructions]("http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html#more-1621").

I have set-up a backup and all seems to progress perfectly well until . . . the whole system grinds to a halt - ie programs "grey" out and the system becomes unusable.  Last night I gave the backup about 5 hours before I gave up.  Here are my questions:

1.  Is this behaviour expected?  In other words, will the first backup usually take 6+ hours, then incremental ones much much less, or am I experiencing a problem?
2.  If this is a bug, how can I investigate/fix it?  All the websites suggest rsync is fast, but I am yet to see that.
3.  Could the fact that I am archiving from an NTFS partiton to another NTFS partition be a bottle neck?  Would formatting one or other to ext4 or something similar help? (I still need to have access to those directories when in Windows)
4.  Is there a way I could re-structure my data to make the process faster?  What else can I try?

Thanks for any useful comments

---

### Post by Zeedok on 2009-07-12
Just thought I'd also mention - I have a lot of directories with "spaces" in the names, like "Important Files" - probably an old windows bad habit(?).  Could this be causing havoc with rsync??

---

### Post by Zeedok on 2009-07-12
After a number of reboots and careful observation, I hopefully have the problem narrowed down.  Dropbox seems to have corrupted a few files and appends "(Case Conflict)" to the title.  Rsync seems to get stuck on these files I think they are corrupted because I can't open them anymore) and the whole system crashes.  By getting rid of these I hope to solve my problem.

EDIT:  I think that fixed it.  Now back in time completes it's processes within a minute or so and MeldDiff viewer says the original and backup are identical - yay!!

EDIT2: My original problem is fixed - but, I have just realised that Back in Time is only copying one sub-directory per directory . . .

---

### Post by XCan on 2009-07-13
Do you really need Back in time or can't you survive running rsync only, i.e, write a script that runs rsync only? I've never trusted all these fancy GUI backup apps, they seem to cause nothing but trouble for the users with too many useless settings. 

I do regular backups to my home computer from my workstation (PhD data as well) using a simple rsync script that grabs my /home dir from the workstation.

---

### Post by Zeedok on 2009-07-13
You might be right about GUIs - my system is crashing again!!  My data has got a number of subdirectory levels and thousands of small files, is that a problem for rsync?  

I'd be happy to use rsync alone, but my CLI/Scripting skills are not great.  Can you point me to some "easy" instructions or maybe show me an example script? 

Thanks for the response and any help.

---

### Post by XCan on 2009-07-13
I haven't noticed rsync having issues with many small files as I have a LOT of them. Now I'm not sure which paths you want to backup, if you want to backup from a remote location etc, but the following example shows what I would use if I wanted to backup /home/user/important/ into /home/user/backup/:

```
rsync -avz --delete /home/user/important /home/user/backup 
```

That's it! -a flag is the archive mode, which tells rsync to keep the ownerships, timestamps etc. -v is verbose mode. -z is compress upon transfer, which doesn't make sense if you do it locally but can be useful if backing up from a remote location. --delete tells rsync to delete any files in backup that doesn't exist in the source location.

The rsync manual can be found: [http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html) .

---

### Post by Zeedok on 2009-07-13
Hey, thanks for the command (which is way simpler than I expected) and the link.  I have tried it a couple of times and I am still having issues - which narrows the problem down to rsync at least.

When I run the command to back-up a particular directory, it starts perfectly and runs for a few minutes, copying most of the files, but eventually it seems to get "stuck" on a particular file and the whole system grinds to a halt.  With a terminal at the ready I have been able to "rsync killall" and get back to business without rebooting (which is progress at least), but I'm not sure what about my data has rsync in such a panic.  I am currently trying another directory to see if that runs ok. 

EDIT - it crashed towards the end of the backup as well.  How can I work out what the problem is??

PS this may be a silly question, but the options you've added in that command do an "incremental update" don't they?

---

### Post by Zeedok on 2009-07-13
I think that perhaps some of the files that rsync is getting stuck on a corrupt.  I had to restore from a zip backup a few weeks ago and it is possible that some of the less frequently used files aren't working properly.

I have tried nautilus and cp just to copy those troublesome directories and the whole system freezes.

Is there a utility that can scan my directories for errors/corrupt files?

---

### Post by Zeedok on 2009-07-14
I have concluded that either (parts of) my data or my data partition are the source of the problem.

I had to reformat the partition about 4-6 weeks ago as it started behaving oddly (ie couldn't delete a directory, despite altering permissions etc). At this time, I also unzipped an archive to repopulate the drive – so errors could have been introduced at either step.

I have successfully copied my music collection (as a trial – ~9.5GB from my home partition to another storage partition – neither of which have been reformatted or fiddled with since installation), so the problem lies on my main data partition – whether it is the filesystem or the files I have not yet definitively sorted out.

I tried to unmount the volume to run fsck, but the partition is an NTFS partition (need to have access to it in Vista), so I don't think it ran properly. I have also tried to edit my FSTAB so that it runs fsck on that partition (I put a 2 instead of 0 as the last entry for the appropriate partition). To cover my bases, I booted into Vista (as a last resort) and ran chkdsk, which I'm hoping has done the job, even if fsck hasn't.

Should I run fsck from a live CD when I get home tonight to check?  What else can I do to check the integrity of all the files?

---

### Post by XCan on 2009-07-14
I don't think Linux can scan a NTFS partition. As you've already run scandisk from Vista, I thought I would just mention that you can also run 'chkdsk' from your Windows installation CD's recovery console.

What did you mean btw with 'incremental update'? Rsync will only copy the changes made each time you run it. But it won't create a 'snapshot' if that was what you meant. :)

---

### Post by Zeedok on 2009-07-14
> **XCan said:**
> I thought I would just mention that you can also run 'chkdsk' from your Windows installation CD's recovery console.

I've done that, unfortunately it didn't help.

> **XCan said:**
> What did you mean btw with 'incremental update'? Rsync will only copy the changes made each time you run it. But it won't create a 'snapshot' if that was what you meant. :)

Clearly, I'm no expert, but I though rsync was capable of snapshots.  Isn't that the idea behind [Rsnapshot]("http://rsnapshot.org/")?

---

### Post by XCan on 2009-07-14
Indeed it is. I personally have not use Rsnapshot, so I can't provide any help of it. However, Rsnapshot is just extending the capabilities of rsync, it's not rsync, although it uses rsync. Instead of overwriting the changes made as rsync would have done, I believe Rsnapshot saves the changes instead, i.e., creating a snapshot. :)

---

### Post by Zeedok on 2009-07-14
I've decided to put this one in the too hard basket.

I still cannot work out what the problem is, but I have upgraded my dropbox account and will install that on another machine at home to give me a "local" backup.

---

### Post by Zeedok on 2009-07-15
UPDATE:

I had run chkdsk before I reformatted, but the problems persisted. I now realise there is an option on chkdsk to "check for bad sectors" or something like that which is not checked by default. Once I ran chkdsk with that option, there were 20+ errors found on the disk.

Hopefully now that these have been corrected, everything will go back to normal. I might re-visit rsync at some point, but for now I'm sticking with DropBox.

Someone on another forum suggested avoiding ntfs-3g and re-formatting the drive as ext3 after installing some windows side software (so the drive can be accessed on Vista).  Has anyone had any experience with this?

Thanks for all the help

---

### Post by Zeedok on 2009-10-03
My problem was ultimately due to hard drive errors.  I have the drive replaced and now rsync works beautifully.  I have started using grsync which is a really simple and so far very stable gui.

Really useful stuff - my next project will be addiung a NAS drive and working how to do network backups using rsync . . .

---

### Post by DeMus on 2009-10-03
I use Grsync for my backups and it works great. I back up my complete home folder, inclusive the hidden files and folders. The first time it took a long time, after that the program looks for existing files and if the date and time are the same they will not be backed up.
Since I also have my large (80GB) music collection in there I exclude that folder and all of its subfolders. Save a lot of time and space. When I loose the music it's a pain in the b*tt for a while but there will be no man overboard. I can always start collecting again.
Since there will be a lot of data going from one disk to another the computer might slow down. Not because of the CPU, which doesn't do that much, but the buses are overloaded.

---


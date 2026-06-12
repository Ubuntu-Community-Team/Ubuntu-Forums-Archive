---
title: "Brand new, trying to recover laptop"
date: 2010-08-09
forum: General Help
---

### Post by Nemmer on 2010-08-09
Hi, I have a Windows XP Dell laptop that completely froze the other day.  I cannot start it up, and cannot even access safe mode -- it just goes to black screen with underscore in the upper left corner.

So, I did some searching and saw a recommendation to create a Ubuntu Live CD to run and access the info on the hard drive, at least.  I have most of it backed up, but not the drivers and I know that will be a pain to redo.  So, I am mostly hoping at this point to recover a little info off the drive before reinstalling the OS.  Of course, if I could just fix it, that would be better...

I get an error message when I try to access the hard drive through Ubuntu that says it is in hibernation mode and I need to start windows and shut it down properly before Ubuntu can mount the drive.  Since I can't get into Windows, this is impossible.  It also said something about being able to mount it read-only.  Can anyone tell me how I would do that?  Or if you have any other suggestions to help, that would be great too.  Thanks!

Nemmer

---

### Post by aysiu on 2010-08-09
I'm hoping someone has a fix for the hibernation mounting issue.

If not, you may be able to do a low-level scan for "deleted" files and recover those:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by earthpigg on 2010-08-09
just did lots of edits within the last 5 minutes. please re-read if you need to.



the best and safest method, i think, would be to remove the laptop hard drive, put it in a hard drive enclosure, plug it into a fellow windows computer, and 'properly remove it' from within windows. i think that would be the absolutely best method, but would require that you get a hard drive enclosure. probably USB - it will turn the laptop hard drive into a really big USB thumb drive. i think they run about $30 at your local computer hardware shop. fry's electronics or best buy, if you are in America.

aysiu's solution is very safe, but ***very*** time consuming. do that if this hard drive has absolutely vital data that you are completely unwilling to risk losing, even if it takes you dozens of hours of work to save. testdisk is generally quick and outstanding for recovering pictures from a digital camera's SD card that you deleted on accident... not so quick and easy for entire hard drives, though.

you will end up with every file on that computer lumped into a single folder with arbitrary file names. picture 10,000 files all in the same folder with file names like "recovered file 0001" and "recovered file 5223". ugly and time consuming to dig through, but safe.

if you are ok with that, do it. if not, read on.


was your error message similar to this?

[IMG]http://mpathirage.com/wp-content/uploads/2008/11/ntfserr.jpg[/IMG]

look at the first suggestion in choice 2. replace 'sdb1' in that example with whatever ubuntu sees the hard drive as. 'sda1' is a likely choice.

replace /media/whatever with whatever you like. leave it as just /media if you want.

be aware that once you force mount, windows will probably be unbootable... but, it looks like that's already the case. either way, unsaved information in applications that where open when the laptop went into hibernate are probably lost at this point.


the reason ubuntu doesn't do this automatically and forces you to go to the command line is because, as i said above, this will break otherwise functional windows installs. it's generally a horrible idea to open windows hard drives or thumb drives that where not properly unmounted or shutdown by windows first, but it looks like you have no choice in this case. 

"ntfs ubuntu force mount" is the appropriate google search for more information about this known problem.

---

### Post by Nemmer on 2010-08-09
It was similar, I'll post the exact words:

> Unable to mount 160GB Filesystem

Error mounting: mount exited with exit code 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated.  Please resume and shutdown Windows properly, or mount the volume read-only with the 'ro'mount option, or mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:
   mount -t ntfs -3g -o remove_hiberfile /dev/sda1/media/D6F45125F45108DF

I read something elsewhere about a hard drive enclosure, will that let me access it from another computer as if it were an external drive?

I'll have to poke around more about how to use the command line on Ubuntu, I guess.

ETA:  Thanks, I saw your edit about the enclosure, that makes sense now. :)

---

### Post by earthpigg on 2010-08-09
> **Nemmer said:**
> ETA:  Thanks, I saw your edit about the enclosure, that makes sense now. :)

k. it'll cost $30, but an enclosure is a nice tool to have around regardless. you can probably borrow one from the nerdiest friend you have.

once it's been 'properly removed' from within windows, you can either use that windows computer to get your data, or an ubuntu machine. i don't think it will make any significant difference.

***make sure you ask about the return policy when you purchase the enclosure*** and keep the receipt. some laptop makers have unique hard drives that will not physically connect to a standard enclosure. (this is the company trying to lock you in to purchasing replacement parts from them, and only them. very annoying.)

---

### Post by aysiu on 2010-08-09
I'll wait for someone else to weigh in on whether this is actually safe to do, but if you do take the warning message's advice, you would do that by (after you've booted the Ubuntu CD, of course) going to Applications > Accessories > Terminal and then pasting in the command ```
sudo mount -t ntfs -3g -o remove_hiberfile /dev/sda1/media/D6F45125F45108DF
```

---

### Post by earthpigg on 2010-08-09
it's not particularly safe to do. it will likely render the windows install unbootable (which may not matter at this point) and may destroy data that was open when the machine went into hybernate.

i've done it on a laptop and been able to recover data (documents, mp3 files, pictures, etc) from the computer, but windows was no longer functional. not that it mattered at that point, of course. the problem was nearly identical to Nemmer's, except he had physically dropped the laptop as well. don't ask me how ubuntu's LiveCD managed to boot on that laptop, but it did. the owner had a document that was open when he hibernated the computer. that important document was lost - not just unsaved changes, but the whole essay.

consider a big fat "use this method at your own risk, and consider yourself lucky if it works" to be in effect.

---

### Post by Nemmer on 2010-08-09
Awesome, thanks to both of you.  I'll try the enclosure as soon as I can get my hands on one, but am glad to know a little more about how to use Ubuntu just in case.

---

### Post by gkestrel on 2010-08-09
Hi Nemmer placing the drive in an external drive case is your best option for easy data recovery, you may find that you have to take ownership of the files you want if you run into permissions problems. It would also be a good idea to get windows to do a chkdsk /r on your drive to check the filesystem over for any errors. After you have recovered all your data replace the drive in the laptop and try booting, if you still cannot boot then a factory reset would now be your best option, this is usually accessed by pressing Ctrl + F11 when you see the dell screen to access the restore function. so long as you are not dual booting which usually destroys dell custom boot record the restore function should still be available and will restore xp and all the drivers and all the programs that were preinstalled by dell.  If you need any further help don't hesitate to ask.

---


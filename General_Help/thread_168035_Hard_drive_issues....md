---
title: "Hard drive issues..."
date: 2006-04-29
forum: General Help
---

### Post by Killerah on 2006-04-29
Hello again folks. I've got ubuntu installed on my crappy old laptop which I'm forced to use because I'm temporarily without a computer. It worked just fine until the 30th time it had to boot up because it checks for errors. My hard drive is crapping out in it's old age and needless to say, it had a bunch of errors. I had this problem 2 times before, and the first time I just let it "fix" these errors, and apparently it decided the best way to "fix" the errors would be to delete all the files that were corrupt. Because of this my ubuntu install didn't work, and I had to wipe it clean and reinstall. The second time this happened I just told it not to do anything and it worked fine. Now we're in present day, earlier today it happened again, it came across tons of errors, I told it not to fix anything, it seemed to work fine until I tried to boot into kde or gnome. Everything in GDM looks good, I go to boot into kde or gnome, and then it just restarts my x session (or whatever the gui thing is called, sorry, I'm still sort of noobish). I figured it was probably GDM, so I installed KDM using aptitude. This didn't help, I got the same result.

So now I could really use your help. If you guys know of any way to recover my install so that I don't have to wipe it and start over, that would be really cool because I've spent alot of time setting it up the way I want it. If not, then could you folks please tell me a way to disable the checking of my hard drive after 30 times since it seems to be the root of my problems (it works just fine until it tries to fix itself). Also, you should know that I recently upgraded to dapper when it went beta (I know this is not the cause of my problem since it happened before when I was still using breezy, so I posted it here), so if there are any new data recovery features in dapper that could aid me that would be cool too.

Any help is appreciated, if I posted this in the wrong section, I'm sorry, please move it.

Thank you
-Nate

---

### Post by cilynx on 2006-04-29
If you can login on the command line, you have hope of maintaining your settings.  
Honestly, you have hope of keeping your system alltogether.

All I do to keep things the way I want is backup my home directory, redo the system, then copy the home directory back over.  

The real issue here is your bad blocks however...

Look into the badblock checking abilities of fsck.  I believe the option is: -c.  You need to have it do a thorough scan, marking the bad blacks as it goes.  Once you do this, Linux will no longer write to those blocks.  Your hard drive may appear smaller, but you couldn't use than space anyway.  If your drive is stable, you could get away with just doing this scan once.  If your drive in continuing to degrade, you may have to do the scan once a week or so to mark the new bad blocks.

Once you've run the scan on your system, if you want to save it, you'll become good friends with "apt-get install --reinstall [foo]" to put back the important files that got eaten.

Best of luck.

---

### Post by Killerah on 2006-04-29
Thanks so much! I really appreciate the advice, and I certianly will try the -c option. But if I just copy over my home directory, I will still have lost all my packages, is there any way I can keep those or keep a list so that they will redownload and reinstall themselves after I reinstall ubuntu? Also, do I just put in "apt-get install -reinstall [foo]"? or does [foo] mean something else?

---

### Post by jazzmuzik on 2006-04-29
Did you setup your partitions as ext3?

If you get tons of errors, and nothing can account for that, the hard drive is probably going bad and nothing can fix it except a new drive. The filesystem check that happens every 30 reboots is a good way to get feedback when things are going bad for a hard drive. While I'm sure it's possible to disable the check, is it worth it?

I'm not familiar with notebook computers, but a BIOS upgrade *might* offer a solution if the problem is related to that. Also, are you overclocking?

Does anything here help? :
[http://www.linuxquestions.org/questions/showthread.php?referrerid=78611&threadid=296730](http://www.linuxquestions.org/questions/showthread.php?referrerid=78611&threadid=296730)

cilynx mentioned using fsck. Using that command requires the partition to be unmounted, otherwise you can really screw things up much worse.

---

### Post by cilynx on 2006-04-29
Just to clarify: a dying hard drive can be used reliably so long as the badblock inode is kept up to date on what parts of the disk not to use.  I have a couple of laptops w/ drives with bad blocks that I have used for years successfully and stabily so long as I do my badblock scans every now and then.

On the fsck note, jazz is right:  you definately need to do your fsck operations with the filesystem unmounted.  Use a Live CD or whatever other method you have of looking at the filesystem without actually mounting it.

As for the "apt-get --install reinstall [foo]", [foo] is just my placeholder for whatever package broke.  If you need to find out what package a file came from, the "apt-file" utility is pretty nice.

As for keeping packages that you've installed, I don't know of an easy way to track what you've installed after the base system.  All you have to do is the package installs though.  If you keep your home directory, you'll have your settings for each program intact.

---

### Post by Killerah on 2006-04-29
I hope I don't sound stupid here, but is there any way to find out what files are corrupt? Some option for fsck?

---

### Post by cilynx on 2006-04-29
Other than watching the output of fsck as it runs (it sometimes spits out the names of broken files), you pretty much have to just wait until the system craps out and then reinstall whatever system it is that broke.  You don't sound stupid at all.  I've been playing w/ Linux for over 10 years and I don't know any way to detect corrupt files after the fact.

---

### Post by Killerah on 2006-04-29
So it doesn't keep any sort of logs or anything I can look at?

---

### Post by cilynx on 2006-04-29
I suppose you could do a:
```

fsck.ext3 -c /dev/whatever &> fsck.log

```
That would log the output of fsck as a text file.

---

### Post by jazzmuzik on 2006-04-29
Isn't there a dpkg option that will compare deb packages to the installed version on the drive? Isn't this similar to finding broken packages?

---

### Post by Killerah on 2006-05-04
Just got internet access again, that's why I haven't posted anything. If somebody could tell me the command for that feature (if such a feature exists) jazz was talking about that would be awesome. Otherwise, it looks like I'll have to just reinstall with the latest release and put my home directory back where it belongs. I tried that command you mentioned cilynx, this one: ```
fsck.ext3 -c /dev/whatever &> fsck.log
```
And it didn't work as hoped, it just spit out a little text file that said I had to use a terminal for it to be interactive. So I just decided I'd copy the output from konsole and save that in a text file, which would have worked except that it didn't put out any useful information. I think it worked though.

So thanks so much for your help so far folks, keep it coming ;).
-Nate

---

### Post by cilynx on 2006-05-04
Try adding the '-a' flag to fsck.  That tells it to run non-interactively and it might not complain about not having a console.

---

### Post by Killerah on 2006-05-04
Well, I already ran the "fsck -c" command, so unless it would output something different, or tell me what I already did, would that really be useful? But thanks anyway, I'll keep that in mind for next time.

---


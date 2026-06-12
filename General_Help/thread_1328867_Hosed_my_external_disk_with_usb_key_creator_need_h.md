---
title: "Hosed my external disk with usb key creator need help with data recovery"
date: 2009-11-16
forum: General Help
---

### Post by zaphodbblx on 2009-11-16
Ok super stupid thing here! I was going to make a usb boot disk and pushed enter before I confirmed which disk I had...it said it couldn't mount the disk but now all my data is a no show and what does show is nonsense...it was only about 3 seconds from the boo-boo to shutdown so I don't think I actually erased my 320 gb disk. any ideas to try to resurrect the data? i'm trying test disk but I really don't know what im doing!

---

### Post by t0p on 2009-11-16
First thing to do is **stop doing anything with the disk!**  You said you're "trying test disk but don't really know what you're doing"... No!! :o  Doing stuff to that disk when you don't know what you're doing is a big mistake.  So stop using it.

Now, go check out the help documentation on data recovery in Ubuntu - you'll find it [here]("https://help.ubuntu.com/community/DataRecovery").  Lots of good info there on what to do (and not do), what software to use etc.  All of it relevant to Ubuntu.

Once you've read the documentation, follow its advice.  Good luck!

---

### Post by zaphodbblx on 2009-11-16
> **t0p said:**
> First thing to do is **stop doing anything with the disk!**  You said you're "trying test disk but don't really know what you're doing"... No!! :o  Doing stuff to that disk when you don't know what you're doing is a big mistake.  So stop using it.

Now, go check out the help documentation on data recovery in Ubuntu - you'll find it [here]("https://help.ubuntu.com/community/DataRecovery").  Lots of good info there on what to do (and not do), what software to use etc.  All of it relevant to Ubuntu.

Once you've read the documentation, follow its advice.  Good luck!

Great advice! photorec(part of testdisk) seems to have done the trick..apearently it has 300+formats it will recover..tomorrow I buy myself another hdd to backup my  data..bad me!
btw I guess I mis spoke, meant to say I want to use testdisk but don't know what i'm doing(I was too afraid to actually do anything) but no matter what that was valid and welcome advice..I couldda' really screwed the pooch there!
I owe this forum a beer!  again!

---

### Post by gontofe on 2009-11-20
Yeah, just done this too :( Am trying various options, and it's getting laaate....

---

### Post by zaphodbblx on 2009-11-21
> **gontofe said:**
> Yeah, just done this too :( Am trying various options, and it's getting laaate....
get testdisk if you havent allready then fire up your terminal
and run photorec(its part of testdisk) I found all my mp3's and documents but lost all my iso files.  you also loose all the folders and file names. If they are properly tagged you should be able to rename the files from the id3 tag using easytag but if they're other types of files you're out of luck as far as I can tell.I would check your hdd that you hosed to make sure you didnt screw up the partition  before you put the files back
good luck I have 14,000 files to reorganize so its gonna be a while

Good luck dude...I wish they had a carbonite client for Linux!

---


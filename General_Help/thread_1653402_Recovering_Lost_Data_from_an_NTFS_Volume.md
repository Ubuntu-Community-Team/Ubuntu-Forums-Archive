---
title: "Recovering Lost Data from an NTFS Volume"
date: 2010-12-26
forum: General Help
---

### Post by Zelandeth on 2010-12-26
Okay, falling somewhat prey to my own obsessive-compulsive tendencies here!

You'd think that with two backups of all my data, which are syncronised twice weekly - that I'd be pretty safe.  Fine and good until in a reorganisation of my documents folders, I delete a bunch of files - and don't notice until after I've run the backup - so they're deleted from the backups as well.  Cue me beating myself around the head with the keyboard a few times about a week later when I realised.  

I'd advise against doing that if you have a keyboard like the IBM Model-M - it hurts.

Okay, so I figure it's at least worth having a stab at recovering this data.  The external harddrive's not had anything written to it since then, so is probably the best candidate.  It's formatted as an NTFS volume (1.5Tb).  

Now, I DO have a copy of R-Studio for Windows which I bought and paid for a few years ago when XP managed to destroy itself and the file structure on the harddrive when it fell over installing SP2 (this was the event which lead ultimately to me switching to Ubuntu).  I've found this to work quite well, though the initial scan does take a while.  Unfortunately, it does NOT seem to work from within Ubuntu through Wine.  It runs, but can't see any drives.  The only Windows environment I have access to now is Vista, and R-Studio seems to hang after running for an hour or so under Vista.

Are there any tools - preferably simple enough that I can get my head around them - which I can use from within Ubuntu to have a scrub through an NTFS drive to look for and potentially recover deleted data?  I've found several tools which claim to recover things from ext3/4 drives from Windows - but not the other way around!

There are a fair selection of filetypes involved here, some word documents, probably most of interest to me though are some old videos, mostly <5Mb taken on my old phone camera from university.  Nothing really mission critical...but memories nevertheless.

Moral of the story...Having a time-delayed backup is probably wise too!

Any ideas guys?

(Running Ubuntu 9.10 on the laptop I'm using just now, 10.04 on my main PC at home).

---

### Post by Mark Phelps on 2010-12-26
The standard recommendation you get in this forum is to look around for Testdisk or Photorec.  Those are two Linux-based tools that claim to be able to do data recovery.

While some folks have had great results with those, my experiences have been quite the opposite -- great huge long lists of useless filenames lacking any directory structure at all.

So, my own preference, largely from my own experiences, has been to use MS Windows tools to recovery NTFS partitions, not Linux tools.

Yeah, the better of them require purchasing ($70 US or so) -- but it's a one-time purchase and, IMHO, recovering personal stuff is well worth that price.  However, if you go to Runtime Software, you can download a trial version for free.  It won't recover anything, but it will show you what it can find on your drive.

Also, you'll need to remove the damaged drive and hook it up to a Windows box because you have to install their recovery app on another drive, not the one with the damaged partition -- but you would want to remove the drive and quit using it anyway.

---

### Post by Zelandeth on 2010-12-26
Thanks Mark.

I'll give those programs a look.

As indicated - I do have a copy of R-Studio (seem to recall it was about that much), which I've found does work pretty well as far as recovering the data is concerned, so long as you're willing to sit and go through the thousands of files it initially finds!  Just it doesn't work with any OS I currently have to hand...and I'd rather not have to buy a copy of XP just to dig through a harddrive!  It's meant to work fine under Vista...however as usual I've found that not to be the case!

No problem with this machine as far as installing/running software relative to the target drive is concerned.

I've got a 1Tb main drive with Ubuntu and my documents on it, a separate 750Gb drive which simply contains a complete copy of my /home folder (updated regularly via Rsync) - and the one we're talking about is an external drive which contains exactly the same plus a few backups from my flatmate's computer - these are intact thankfully!  Was only my data I zapped.

Still kicking myself here that I've managed to do this!

---


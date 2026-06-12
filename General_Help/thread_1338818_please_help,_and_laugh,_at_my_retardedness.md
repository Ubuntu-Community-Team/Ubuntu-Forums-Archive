---
title: "please help, and laugh, at my retardedness"
date: 2009-11-26
forum: General Help
---

### Post by paulqueen on 2009-11-26
Okay.  SO - i'm positive that there is something simply I am overlooking here... i'm still fairly new at linux and ubuntu so bare with my ignorance please:

i have a setup like this 3.5gb swap, 20gb for /, and 227gb for /home.
if i reinstall ubuntu, do i have to del the entire /home partition?  i have a large chunk of media files on there i would prefer not to lose, like, if i had a choice from taking a punch in the stomach from a pro boxer or losing those files id take the punch.

what is my best option here to save the files, without ability to back them up on external meda, and still get a clean ubuntu reinstall?

thanks for the help and holding my hand through this ordeal

btw i am on a plain Ubuntu 9.10 64bit

---

### Post by BenAshton24 on 2009-11-26
no, you don't have to delete the home partition, simply remove the other two and create new root and swap partitions then set the home partition's mount point.

---

### Post by cascade9 on 2009-11-26
You dont need to format /home.

I actually setup my drives with /, /home, swap and /mnt/media, just so I can format /home if I want and not lose any data.

---

### Post by paulqueen on 2009-11-26
awesome what a relief - - i was totally antsy sitting here waiting on a reply, thanks 

will i have to delete any of the /home files ubuntu created before reinstalling over it?  im still used to windows so reinstalling without formatting everything scares me still since windows will **** up permissions and paths and try to use old config files and next thing you know you wake up on the floor with no recollection of what happened until you look at your monitor and its a BSD staring you down ... and then you black out again.  <- damn near true story

---

### Post by akakingess on 2009-11-26
> **paulqueen said:**
> Okay.  SO - i'm positive that there is something simply I am overlooking here... i'm still fairly new at linux and ubuntu so bare with my ignorance please:

i have a setup like this 3.5gb swap, 20gb for /, and 227gb for /home.
if i reinstall ubuntu, do i have to del the entire /home partition?  i have a large chunk of media files on there i would prefer not to lose, like, if i had a choice from taking a punch in the stomach from a pro boxer or losing those files id take the punch.

what is my best option here to save the files, without ability to back them up on external meda, and still get a clean ubuntu reinstall?

thanks for the help and holding my hand through this ordeal

btw i am on a plain Ubuntu 9.10 64bit

That is why you were wise to create a separate home partition, now you can do a completely clean install, and it will not touch anything within your home directories, just so long as you leave it alone during install (don't format it on accident, just label it /home and leave the rest alone)!!!  Be glad you prepared and looked ahead for this particular situation.

---

### Post by poebae on 2009-11-26
Out of curiosity, how much RAM do you have?

What's with the 3.5GB swap?

---

### Post by akakingess on 2009-11-26
> **paulqueen said:**
> awesome what a relief - - i was totally antsy sitting here waiting on a reply, thanks 

will i have to delete any of the /home files ubuntu created before reinstalling over it?  im still used to windows so reinstalling without formatting everything scares me still since windows will **** up permissions and paths and try to use old config files and next thing you know you wake up on the floor with no recollection of what happened until you look at your monitor and its a BSD staring you down ... and then you black out again.  <- damn near true story

There may be some apps you need to reinstall, but you would be surprised, most will come up just as it was before, and sometimes even the desktop pattern (if you had changed it) will come back up!

---

### Post by cascade9 on 2009-11-26
Exactly akakingess. 

Thats why I have /mnt/media. Most of the time, getting your settings back is nice, but just sometimes, you want to nuke the whole previous setup and start again. Well, I do anyway. ;)

---

### Post by paulqueen on 2009-11-26
@ aka - puttin home on a separate partition only happened cuz it was one of the suggestions from the community here on the forums on a post about installing

@ poe - 4gb ram, or 3998gb or whatever it registers at officially

@ cascade - gotta love nuking it and starting over.. sadly it hasnt been an optino for me at the moment =\

alrite, im gonna finish watchin a movie on here then get to the reinstalling.

thx again

---


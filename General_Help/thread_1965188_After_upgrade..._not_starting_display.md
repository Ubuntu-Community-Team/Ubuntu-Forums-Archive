---
title: "After upgrade... not starting display"
date: 2012-04-25
forum: General Help
---

### Post by cazazo on 2012-04-25
Hi I'm using Ubuntu 12.04 with the fallback packages installed... after an update/upgrade process, the diskplay is not starting, I have to press ALT+F2 in order to enter my login and password from command line... then I have to type startx to start the display, but with no panels and or buttons no sound... only the background
Can anyone help me??? I'm giving up on Ubuntu... since Unity I'm having so much problems... It's a shame after almost 5 years using it.

---

### Post by houseworkshy on 2012-04-25
I haven't tried it yet but as you can get to the command line does "sudo start gdm" still work?

---

### Post by cazazo on 2012-04-25
> **houseworkshy said:**
> I haven't tried it yet but as you can get to the command line does "sudo start gdm" still work?

Unfortunately not...

```
:~$ sudo start gdm
start: Job is already running: gdm

```

---

### Post by houseworkshy on 2012-04-25
Well you could try reinstalling the gui.  You could also try Mate or  Cinamon as an alternative GUI.  LXDE is one that is in the repro's.    Worth trying "sudo apt-get update" and "sudo apt-get upgrade" if you  haven't already.  

The 10.04lts is working great still and has another year of support  left, you could use that, wait for the next lts ( releaced tommorow I  think ) to go through it's teething period, a couple of months usually,   and then upgrade to that.  That would be the best bet I think, if you  do a duel boot you could use the other to test things out.  That's what I'm doing anyway, if I get debian sweet on the other drive while using 10.04 during the rest of it's support whether 12.04 works out for me or not won't be so crucial.

There is also Mint which is where many unity haters have fled when  the gnome fallback doesn't work.  There are several distrbutions which  are gnome2, I've been browsing around distrowatch.com just in case I  can't  make 12.04 do the retro things I'd like.  Debian's stable branch is  usually rock solid once one has set it up,  they keep the development  section and the stable section seperate and nothing crosses the line  untill they are absolutley sure.   Crunchbang looks pretty good too.  In the 'buntu's Kubuntu is full  featured and the support is switching away from cannonical after this  next release, the people who are to take it over say that they will be  emphasising stability over development.   Lubuntu seems to be a popular  lighter  'buntu alternative judgeing by the forums.  
 
Whatever you do get your work backed up, Puppy linux, with any form of external storage medium 
( includeing dvd/cd's even on a machine with only one cd/dvd drive  because one can run puppy in ram freeing up the drive ) is ideal for  that sort of task. 

Good luck.

---

### Post by cazazo on 2012-04-25
Thank you for the replies guys... I tried to install mate but didn't work at all, so I decided to reinstall the ubuntu 12.04 I was using the version 10.10 before and was really great! I don't hate Unity, but it doesn't work for myself, just clumsy and awkward... not very user friendly IMHO! I tried mint and is not very stable at the moment (using it in my laptop) I'm having few issues with mint 12. 
Well, I hope this scenario changes pretty soon or I'll give up using linux and hit back to the old windows... Thank you once again!

---

### Post by cazazo on 2012-04-29
Changed to Solved. 
Thanks

---


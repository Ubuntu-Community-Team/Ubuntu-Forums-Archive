---
title: "Need Help!"
date: 2006-04-21
forum: General Help
---

### Post by Binny45 on 2006-04-21
Howdy folks

Been posting a time or two, however I've now started taking steps towards installing UBUNTU on my home machine.  I used Partition Magic to setup my partition and my swap partition for linux.  I go into the installation and I'm trying to avoid using my NTFS partition, and just want it to use the other two, however when I go next, it comes up with a big red Root error and forces me back to the partition screen.

I'm feeling pretty over my head, otherwise I'd just go looking around the site, but if someone could direct me to a VERY simple install guide for those of us in this situation and are VERY new to Ubuntu and Linux as a whole.

Any and all help is immensely appreciated.

---

### Post by moon_dog on 2006-04-21
are you sure that the partitions were created?  when i first tried installing ubuntu i couldn't get any partitioning software to partition my drives and just ended up reformatting everything and overwriting windows with linux.

---

### Post by Binny45 on 2006-04-21
Aye, the installation process picks up the three partitions
`

---

### Post by Binny45 on 2006-04-21
This install process isn't that simple :confused: 

For someone that's trying not to wipe his hard drive, I already have the partitions set up.  The Ubuntu install recognizes the linux partitions I've set up, yet when I try to go beyond it, it gives me some sort of Root error (something about not being assigned or something?).  What is this? I really want to try this OS, but I can't even get through the install ](*,)

---

### Post by Binny45 on 2006-04-22
Ok....got it installed now (Yay Me!)

However, during the install it asked me what resolution I'd like X Server to run at.  I left it at the defaults and continued.

The Ubuntu load up screen shows up, loads up the programs, but then I get a blue screen of death, with something along the lines of X Server not being configured properly and to restart the GDM (whatever that is and however you do that hehe).  It then sends me back to a prompt, of which I have no idea what to do.

I noticed this error pop up when I tried the live CD's, however I thought it would fix itself during the Install, however it seems to still be around. :-k

---

### Post by Binny45 on 2006-04-22
Any takers?

Anything I should try?  Anything I should try and install?

Please, I really want to make this work :(

---

### Post by Binny45 on 2006-04-22
It seems it's a problem with my graphical interface.

I dunno if this is a code issue, or my video card issue or what not.

Gonna try using Kubuntu to see if I can get any joy that way.  If no luck there, are there other Linux platforms that I can check out?

---

### Post by Binny45 on 2006-04-22
Ugh, Kubuntu install was worse than Ubuntu install.  And Mandrake 10.1 stalls at the license portion, near the beginning of the install.

I dunno what's going on, but damn, I'm glad I kept Windows Xp Pro on my machine, otherwise I'd be out of luck.

This is not going well at all :(

---

### Post by Binny45 on 2006-04-22
Hmmm, going to try the 32 bit version of Ubuntu.  According to the 64 bit forums, it's not going so good.  I'm hoping that this is the source of my problems.

/crosses fingers

---

### Post by Face1 on 2006-04-22
To touch the tip of the iceberg here, the root error you are getting is probably because you did not set a partition with the mountpoint '/'.  / is the root of your filesystem, so you need to specify your linux partition to start there.

---


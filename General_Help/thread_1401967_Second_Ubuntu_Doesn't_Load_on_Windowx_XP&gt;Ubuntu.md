---
title: "Second Ubuntu Doesn't Load on Windowx XP&gt;Ubuntu 9.10&gt;Ubuntu 9.10 System"
date: 2010-02-08
forum: General Help
---

### Post by Tech Mom on 2010-02-08
First time poster here, so please bear with me.  I am working on a distro for someone based on YLMF OS (Ubuntu 9.10) and was having trouble making the Grub2 splash screen modifications I wanted.  Last night I installed BURG, which I love btw, and was able to get my Grub splash screen working on my 'working copy'.  However, I have the distro copy on another partition and now when I try to boot into it, it gets past Grub and loads the splash screen, etc.  After selecting the copy I want to run, it just comes up with the splash image and sits there.  The only thing I can think of that I did differently on these two versions was last night I installed splashy which removed usplash.  I feel perhaps this has confused the system.  I'm only going on my gut as to what it's 'thinking' but something changed in this area of the load.  I cannot get to the login screen at all.  I can load the partition in my other version so can make changes as necessary if someone could give me some opinions on things to try.  

I'm running Windows Media Center (XP Home)
Ubuntu 9.10 (YLMF - Ubuntu 9.10)
Ubuntu 9.10 (YLMF - Ubuntu 9.10 customized)

all the options are coming up in my bootloader and I can boot into windows just fine.  I noticed today that the / was set to load in MBR which I had changed.  I have changed it back to my original working copy partition to see if that helps.  Also, recovery mode doesnt work either so there's a missing link in the process that I may not have the experience to identify.  

<NOTE:  After changing my boot to sda5 again, when I try to boot into sda6 it stops at this message:

*Starting init crypto disks...    [OK]

Then nothing.

:KS

---

### Post by Tech Mom on 2010-02-11
> **Tech Mom said:**
> First time poster here, so please bear with me.  I am working on a distro for someone based on YLMF OS (Ubuntu 9.10) and was having trouble making the Grub2 splash screen modifications I wanted.  Last night I installed BURG, which I love btw, and was able to get my Grub splash screen working on my 'working copy'.  However, I have the distro copy on another partition and now when I try to boot into it, it gets past Grub and loads the splash screen, etc.  After selecting the copy I want to run, it just comes up with the splash image and sits there.  The only thing I can think of that I did differently on these two versions was last night I installed splashy which removed usplash.  I feel perhaps this has confused the system.  I'm only going on my gut as to what it's 'thinking' but something changed in this area of the load.  I cannot get to the login screen at all.  I can load the partition in my other version so can make changes as necessary if someone could give me some opinions on things to try.  

I'm running Windows Media Center (XP Home)
Ubuntu 9.10 (YLMF - Ubuntu 9.10)
Ubuntu 9.10 (YLMF - Ubuntu 9.10 customized)

all the options are coming up in my bootloader and I can boot into windows just fine.  I noticed today that the / was set to load in MBR which I had changed.  I have changed it back to my original working copy partition to see if that helps.  Also, recovery mode doesnt work either so there's a missing link in the process that I may not have the experience to identify.  

<NOTE:  After changing my boot to sda5 again, when I try to boot into sda6 it stops at this message:

*Starting init crypto disks...    [OK]

Then nothing.

:KS
BUMP!  -- Anyone out there???

---


---
title: "Uninstall?"
date: 2009-07-13
forum: General Help
---

### Post by spaceship.rodeo on 2009-07-13
I recently got a netbook which is going to be used for ubuntu, so don't worry, I'm not leaving, haha.  Anyway, I'm dual booting xp and 9.04 and I was going to just uninstall ubuntu and use my desktop for gaming and the like.  I searched for guides as to how to do this because I know if you just format the partition, you can't do anything because the grub menu is still there and looking for linux or something.  However, all the guides I looked at wanted me to get a livecd (which I did) and use fdisk via the command line.  However for some reason I can't use fdisk when I try.  Maybe I'm just doing it wrong, I don't know.  I was wondering if anyone knew of a guide that would tell me how to either use fdisk and get it to work or use a different method.  Thanks for any help!

---

### Post by lisati on 2009-07-13
Here's a quick guide. You'll need a Windows disk and an Ubuntu Live CD, and a means for making backups.
[LIST=1]
[*]**Important:** Make a backup of your important data
[*]Boot from a "Live CD"
[*]Start the partition manager (on System->Administration->Partition manager)
[*]Delete the Ubuntu partition(s)
[*]Resize the Windows partition(s) as required
[*]Restart, this time booting from the Windows CD
[*]use the fixmbr and fixboot commands from the Windows recovery console (I forget which option to get there for now, maybe someone else can step in and remind me)
[*]Exit, and restart as usual.
[*]Don't be surprised if Windows goes through a rigmarole of running chkdsk and restarting your machine
[/LIST]

---

### Post by spaceship.rodeo on 2009-07-13
Weird. Maybe my cd is messed up.  I tried opening the partition manager and for some reason it wouldn't work.  It also took way too long for any program to boot, for that matter.  I haven't used a livecd since I first installed ubuntu like a year and a half ago, so maybe I'm just remembering incorrectly.  But I'll give it a shot, thanks.

---


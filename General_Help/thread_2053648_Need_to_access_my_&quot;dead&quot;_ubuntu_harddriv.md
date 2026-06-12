---
title: "Need to access my &quot;dead&quot; ubuntu harddrive using a Linux Mint 10 live disk"
date: 2012-09-05
forum: General Help
---

### Post by JacobRogers on 2012-09-05
I'm in a sticky situation, I had Ubuntu 10.04 on my computer and in the update manager it said to update to 12.04 by clicking a button.  I clicked the button and the computer did it's thing for a long while and then it broke.  The first time it restarted it showed my desktop but no panels and everything was wonky.  I restarted again and I get error messages about the monitor being out of frequency.

I have a Linux Mint 10 live Cd laying around and that's what I've used to boot up the computer.  Can I use the Linux Mint 10 Live CD to mount my hard-drive and try to back up my files onto a flash drive?

How do I mount my old hard drive using Linux Mint 10?   Help greatly appreciated.  I have some important files that I'd like to back up.

I feel like I've royally messed up.  :guitar:

---

### Post by notoriousdbp on 2012-09-05
It should work, no problem.  However, if your /home is on a separate partition to / then you should also be able to do a 'clean' install of 12.04 adding your original user credentials when prompted.  Quick question, do you have an Nvidia graphics card on your computer?  Unfortunately the Nvidia drivers in 12.04 are a bit flaky to say the least.

---

### Post by JacobRogers on 2012-09-05
Hey thanks for the reply.

I don't know the right commands to enter into the terminal to mount my old hard drive, that's why I'm asking for help.

---

### Post by JacobRogers on 2012-09-05
Success.  I used sudo fdisk -l to look at the different disk on my drive and I guessed and used context clues to figure out which one I wanted.

Then I used sudo mkdir /media/oldhd 

And then I used sudo mount /dev/sda1 /media/oldhd 

And now I have access to my files.

awesome

---

### Post by TheFu on 2012-09-05
**Before** doing possibly destructive things to your HDD, like an install, a backup is required.
Ok, with that said, I have great news ... provided you didn't encrypt your HOME directory or format the HDD during your attempted upgrade.  I've never used Mint, but the Ubuntu partitions will be either ext3 or ext4 file systems.  Mint can read those just fine.  Boot up Mint and look for the partitions to be mounted automatically under /media.  If they aren't there, I can't tell you how to do it with a GUI, but you can mount them using the shell/CLI easy.  To learn how:
**$ man mount**

After you get the partitions mounted, you need to copy your files off somewhere. A USB flash drive or another HDD is probably the easiest.

You really don't need mint, any Linux distro in the last 2-3 yrs should be able to do this, but mint should work too.

If you did encrypt your HOME things will be a little harder provided you have the key. If you don't have the key, you are screwed and that data is gone.  Gone, unless you have a backup on a different HDD somewhere.



Having a backup is part of responsible computer use. Ubuntu has made it really easy to automate with the current backup tools. It is up to each of us to use those tools.

Before going through all of this, perhaps it would be easier to just boot into Ubuntu and on the login screen, select a different desktop environment - something lighter than Unity - XFCE, LXDE, OpenBox ... and the GUI issue will probably go away.  Unity requires more capable graphics than some people have - myself included.

---


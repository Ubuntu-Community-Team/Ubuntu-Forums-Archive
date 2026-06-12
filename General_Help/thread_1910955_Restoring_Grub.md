---
title: "Restoring Grub"
date: 2012-01-18
forum: General Help
---

### Post by Quarkrad on 2012-01-18
After much frustration I have settled on these commands to restore grub via LiveCD after a reinstall of Windows:

[B]sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/B]

they have worked successfully for a number of re-builds.  The above assumes Windows is on sda1 and Ubuntu on sda2.  However, I'm forced to do a reinstall of Windows where Ubuntu will be on sda1 and Windows on sda2 - not the preferred way round.  How should I change the above or is there is neat/safe way to move Ubuntu from sda1 to sda2 before I reinstall Windows (xp).  I have Ubuntu backed up on another HD but only recently rebuilt this machine so would prefer to keep Ubuntu 'as is' rather than rebuild.

---

### Post by raja.genupula on 2012-01-18
Hi i am not getting your question properly . But what do you wanna restore your grub ? try boot repair . it will fix all .

---

### Post by Quarkrad on 2012-01-18
I have ubuntu installed and working on sda1.  I am going to install wnxp on sda2 so when I've finished the install the pc is going to boot to winxp every time.  To get back to a dual boot pc I am going to have to boot to a LiveCD and re-install grub.  I normally boot to 'Try Ubuntu' and when I get to the Desktop I open the Terminal and enter the following commands:

[B]sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/B]

(assuming ubuntu is mounted on sda2 and HD is sda)

but in my case Ubuntu is not on sda2 it will be on sda1 so I need to amend the Terminal commands. Is it as simple as:

sudo mount /dev/sda**1** /mnt
sudo grub-install --root-directory=/mnt /dev/sda

---

### Post by nipunshakya on 2012-01-18
Hi. I would suggest you to have a thorough look at [FONT=verdana][SIZE=3][here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") [/SIZE][/FONT]. Hope it will help you fix the error the other way round.


Regards,WinuxUser

---

### Post by dragonfly41 on 2012-01-18
Myself I have a dual boot configuration (my current headache being that I have to repair/reinstall ubuntu since it does not come out of the splash to launch into desktop).

I might be wrong .. but I thought that Windows requires to be installed in the first physical partition (sda1)?

If that is correct (please confirm this theory from others) then you might need to juggle your partitions using Live CD. 

...

My own struggles are here ..

[http://ubuntuforums.org/showthread.php?t=1909151](http://ubuntuforums.org/showthread.php?t=1909151)

---

### Post by nipunshakya on 2012-01-18
^^I just saw my partition scheme here.(i have a dual boot too.) I found out that my windows 7 is in sda1 and its not a coincidence.

Regards,WinuxUser

---

### Post by Quarkrad on 2012-01-19
To complicate things I'm having to do this remotely over the phone with my brother-in-law.  If I boot into LiveCD is there a command that would copy/transfer the contents of sda1 (my working Ubuntu partition) to sda2?  I know Clonzilla would do this but there is no way I could talk my brother-in-law through Clonezilla.  If I have to have winxp on sda1 and Ubuntu on sda2 then the ideal scenario, if it exists, would be a terminal command via LiveCD.

---

### Post by nipunshakya on 2012-01-19
I guess, its better a clean re-installation of your OSs rather than going for a clone. Its better that way. Still, u can wait for others to reply too...goodluck

Regards,WinuxUser

---

### Post by Quarkrad on 2012-01-21
I've decided to to rebuild the whole thing from scratch.  At the end of the day it's quicker than other methods.  Thanks for your help.

---

### Post by nipunshakya on 2012-01-21
Well, at the end, thats a better way to make things right...Goodluck

Regards,WinuxUser

---


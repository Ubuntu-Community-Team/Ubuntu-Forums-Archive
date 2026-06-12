---
title: "need to reinstall, how do i keep my files?"
date: 2011-04-30
forum: General Help
---

### Post by slgtheindividual on 2011-04-30
I completely messed up my 11.04 install so I need to completely reinstall it. I have a live cd and I'm booting in a clean ubuntu on a seperate windows partition (I was dual booting). I want to transfer all of my files and installed programs from my messed up 11.04 partition but without copying all of the broken files (none of my personal files or music or installed programs are broken) so that I can make a clean install and then just copy them straight back. Is this possible?

Thank you

---

### Post by Thewhistlingwind on 2011-04-30
Go to /, then /home, then copy the whole folder with your name on it. (Verify that your data is in it.)

Copy it to the windows partition, or an external storage device. Move on with the rest of your day.

Not sure about programs though, that's much harder.

---

### Post by slgtheindividual on 2011-04-30
ok, that's a good start, thank you.
Maybe I'll just have to install them all again? Could be worse, at least they're free =]

Also what about my settings? Will they be copied by this?

---

### Post by oldfred on 2011-04-30
You mention windows partition. Was this a wubi install? It gets a bit more complex if it is. Also if you copy /home to a NTFS partition then you lose ownership & permissions as NTFS does not support them.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

If not wubi ignore above.

---

### Post by slgtheindividual on 2011-05-01
No it wasn't a wubi, just a clean install on a seperate partition, thank you anyway

---

### Post by slgtheindividual on 2011-05-01
would it be possible to create a new partition on the hard drive that has the broken ubuntu on and then install a clean ubuntu on that partition and transfer my files over to that?

---

### Post by dragonfly41 on 2011-05-01
This is one reason why I'm exploring how to generate a re-install script ..

[http://ubuntuforums.org/showthread.php?t=1745622](http://ubuntuforums.org/showthread.php?t=1745622)

If you can get into your old ubuntu you can generate a reinstallation script in Synaptic Package Manager.

---

### Post by slgtheindividual on 2011-05-01
Unfortunately I can't even get in. Re-install script sounds like a great idea though

---

### Post by vanadium on 2011-05-01
It is a simple matter of having a good backup of your own user data, which you should have in any situation. Then you can reinstall without any worry that something unrecoverable would happen. Your own data are valuable and unique to you. Operating systems come for free and with Freedom, and are reinstalled in less than an hour.

After reinstalling the OS, add your applications that are not there by default and put your own data back in place.

If, in your case, you do not have an up-to-date backup, bot from a live CD and backup from there. You could also boot into a recovery prompt, but then you will need to work with a command to copy your data, such as "rsync".

---

### Post by oldfred on 2011-05-01
I have 3 partitions in rotation. Old install, current install & alpha/beta final. I usually both upgrade alphas & reinstall the newest to make sure my updates are working. I usually copy some user settings from old install's /home and have a /data partition that I link in for all my personal data. I just saved history from manually doing all the settings and converted it to a bash file.

---

### Post by collisionystm on 2011-05-01
> **slgtheindividual said:**
> I completely messed up my 11.04 install so I need to completely reinstall it. I have a live cd and I'm booting in a clean ubuntu on a seperate windows partition (I was dual booting). I want to transfer all of my files and installed programs from my messed up 11.04 partition but without copying all of the broken files (none of my personal files or music or installed programs are broken) so that I can make a clean install and then just copy them straight back. Is this possible?

Thank you

Your /home saves your personal files and preferences for the programs you installed. Not the programs themselves. I suggest you make a note of what you want reinstalled and do it fresh. It will minimize your problems. Plus with your home folder settings the programs will be back where you left off.....

---


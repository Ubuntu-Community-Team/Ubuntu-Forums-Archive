---
title: "Getting USB going before fstab"
date: 2009-10-16
forum: General Help
---

### Post by Swil on 2009-10-16
Hi.

Despite my novice skills I've managed to get a ubuntu 9.04/mediatomb based server going. However I have one small problem I can't sort, hoping the ridiculously high combined IQ of these forums can help me.

I use an external NTFS formatted USB hard drive to store all my media on. This works fine - however I have to manually mount it at startup.

I have tried sticking a line in my fstab, but that throws an error as it tells me
/dev/sdb1
(my hard drive) doesn't exist.

I'm guessing this is because whatever process automatically loads my USB drive (so I can mount it) happens *after* fstab.

This means mediatomb loads before my USB drive, and removes all the external media from its database because it can't find it. I have to reload my entire media database every time I boot.

How can I make the USB loading thingy that sets up /dev/sdb1 happen before fstab?

Or is there a better approach?

---

### Post by razorboy5 on 2009-10-16
not any good and this but did a quick google and

"If a device/partition is not listed in fstab **ONLY ROOT** may mount the device/partition."

perhaps that's the problem?


this seems quite useful: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by JKyleOKC on 2009-10-16
Yes, there's a better approach!

Open /etc/rc.local in a text editor, using "sudo" to be sure you have root privileges when editing. Just in front of the line that says "exit 0" near the bottom of the file, insert a line that has the exact same mount command that you enter manually. However you should omit the "sudo" from the command, because rc.local executes as root at the very end of the boot sequence.

The whole purpose of this file is to deal with situations such as you face. I have to stop my network processes, set up packet forwarding, and start the network again, in order for my rather complicated little network to function properly, and will eventually launch a couple of third-party programs to run in background at all times, also. Lines in /etc/rc.local will take care of all these happenings.

---

### Post by Swil on 2009-10-18
Thanks JKyleOKC, that got it mounted automatically - but unfortunately *after* mediatomb starts so I still lose my database... Is there a way I can find where mediatomb gets started on startup and move it to after rc.local? Or perhaps run it in rc.local instead of wherever else it's being run?

Thankyou muchly for your help so far

---

### Post by JKyleOKC on 2009-10-18
You might take a look in /etc/init.d to see if there's a file there that's used to start mediatomb (I'm not familiar with mediatomb so can't be more specific). If you find one, take a look inside it with gedit or mousepad or kate (depending on which desktop you have; these are the text editors for the three main flavors of *buntu) to see what parameters it takes. The files in init.d all follow the same general pattern: they take a single parameter which can have one of several defined values, such as "start" or "stop," and near the end of the file you'll find a few lines of script to be executed if the parameter has any other value. Those lines include one that gives a list of the acceptable values.

If you do find such a file for mediatomb, and if it includes "reload" as an acceptable value, you can try adding "/etc/init.d/mediatomb reload" to the rc.local file right after your already added lines and before the "exit 0" line. This should force a reload of the daemon and get what you want. Incidentally "mediatomb" in that line to add should be replaced by the actual name of the file you find, if it's different.

EDIT: This won't actually solve your problem of losing the database, though, as I realized after re-reading your original post. Instead, you need to locate the point at which mediatomb now loads, and stop it from loading. The simplest way to do this is to look through the /etc/rc2.d directory and find the file whose name begins with "S" and has "mediatomb" or whatever the name you found above as its 4th and later characters. The second and third will be numeric digits. To prevent this from loading, just change the capital S at the start of the name to a lowercase s; since Linux is case sensitive, this will make the file invisible to the startup process. Then make the addition to rc.local that I described above, except using "start" instead of "reload" as the parameter. This should achieve what you want.

If it doesn't work, you can put things back to their original state by changing the "s" back to "S", and deleting the line added to rc.local.

Hope this helps!

---

### Post by Swil on 2009-10-21
Your solution worked a treat - thanks Jim!

---

### Post by techguy615 on 2009-11-01
Another option that I used was changing the mediatomb startup file to always run as root. Like this:

1) stop mediatomb if it is started: sudo /etc/init.d/mediatomb stop

2) edit mediatomb startup file: sudo nano /etc/init.d/mediatomb

3) edit the file and comment out the lines shown below with the # at the front of the line.

# Run as root if USER not specified
#if [ ! $USER ]; then
        USER=root
#fi

4) Save the file.

5) start mediatomb: sudo /etc/init.d/mediatomb start

That should do it. When you go back to the page for mediatomb and tell it to open the USB drive in the file system it should work.

I just ran into this with version 12 from the repository. I am running 9.10 (Karmic Koala). Seems to be working fine now.

Cheers. ;)

---


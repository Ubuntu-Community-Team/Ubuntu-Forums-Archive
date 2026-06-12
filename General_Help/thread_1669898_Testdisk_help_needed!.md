---
title: "Testdisk help needed!"
date: 2011-01-18
forum: General Help
---

### Post by GoBears2011 on 2011-01-18
(My apologies - I started this yesterday in the wrong place.  [http://ubuntuforums.org/showthread.php?p=10371068&posted=1#post10371068](http://ubuntuforums.org/showthread.php?p=10371068&posted=1#post10371068))


New user - in need of help!

Here's the story - my NHD/NAS stopped working. Hoping it was a problem w/ the network card I pulled the hardrive out of the NHD case and mounted it in an external case. Windows 7 won't mount it, neither will XP, neither will a Mac. The drive shows up in the device manager but won't mount. It sounds fine spinning. Quiet and no different than before.

The NHD was a 250GB Iomega black series. The actual drive inside is a Western Digital.

After searching a while I came across some threads here. I've been planning on trying Ubuntu for a while on an older laptop that really slowed down with XP SP3. Loaded ubuntu up - all went very smoothly. I'm quickly becoming a huge fan of the OS.

Now back to my problem - I plugged in the drive on my new Ubuntu system and it MOUNTED!!! Well sorta..........see the 1st screen shot. The drive shows up as 3 drives which I'm assuming are partitions. I can actually access the middle 66 MB drive. It contains what I suspect is the Linux operating system for the NHD.

If I try to access the other two I get a pop-up per:
For the 66 mb I can't access - "Error mounting" mount /dev/sdc2: can't read superblock"
For the 250 gb I can't access - "Error mounting" mount /dev/sdc4: can't read superblock"

I then tried to run the testdisk utility on the 250 gb drive both using "sudo testdisk /dev/sdc4" and just "sudo testdisk".  I've also tried NONE and the INTEL partition. Based on my earlier post and playing around with options I think running it with "sudo testdisk" and INTEL might be the way to go.  See the screen shots for the errors and sequence of events.

I don't know what to do next - I'm worried about messing something up and I haven't found a post detailing the problem I'm having - which seems to be something to do with testdisk thinking my drive is a heck of a lot bigger than it is.

If testdisk can't fix it - does anybody have a professional service they can recommend? I really need this drive recovered.

Stupid me - I had a 2nd drive ready to back up this 250 GB NHD. Never did it. That is a mistake I'll only make once!

Thanks in advance!

---

### Post by Lukiwuki on 2011-01-18
Hey,

Try to plug in the NHS while ubuntu is running.
Tehn press Alt+F2 and enter 
> gnome-terminal
Then a terminal pops up and now you can try to repair the superblock that seems to be broken.
Enter 
> sudo umount /dev/sdc2
and
> sudo umount /dev/sdc4
then you can try to repair it by entering
> sudo fsck -a /dev/sdc2 
and 
> sudo fsck -a /dev/sdc4
into the terminal.

Then unplug and plug the NHS in again.
Now you should be able to use your NHS.

Let me know if it worked or what kind of issues you had.

---

### Post by GoBears2011 on 2011-01-18
No luck -

gobears@T41:~$ sudo umount /dev/sdc2
[sudo] password for gobears:
umount: /dev/sdc2: not mounted
gobears@T41:~$ sudo umount /dev/sdc4
umount: /dev/sdc4: not mounted
gobears@T41:~$ sudo fsck -a /dev/sdc2
fsck from util-linux-ng 2.17.2
fsck: fsck.xfs: not found
fsck: Error 2 while executing fsck.xfs for /dev/sdc2 gobears@T41:~$ sudo fsck -a /dev/sdc4 fsck from util-linux-ng 2.17.2
fsck: fsck.xfs: not found
fsck: Error 2 while executing fsck.xfs for /dev/sdc4 gobears@T41:~$ 

No change when I disconnected/reconnected the drive.

---

### Post by Lukiwuki on 2011-01-18
Try 
> sudo apt-get isntall xfsprogsand then
> sudo fsck -a /dev/sdc2and
> sudo fsck -a /dev/sdc4
Then un- and replug the Device and if you are lucky it works ;)

---

### Post by GoBears2011 on 2011-01-18
Thanks for the replies.

No luck yet - after the install:

gobears@T41:~$ sudo fsck -a /dev/sdc2 
fsck from util-linux-ng 2.17.2
/sbin/fsck.xfs: XFS file system.
gobears@T41:~$ sudo fsck -a /dev/sdc4
fsck from util-linux-ng 2.17.2
/sbin/fsck.xfs: XFS file system.
gobears@T41:~$

Unplugged/Reconnected.  Same superblock errors on sdc2 and sdc4.  Can only access the one partition on the drive.

---

### Post by Lukiwuki on 2011-01-18
Try "xfs_repair /dev/sdc2" bzw "xfs_repair /dev/sdc4". But I cant help you on that one, never did it by my self. Maybe you should first read the manpage or google it.

---

### Post by Lukiwuki on 2011-01-18
Sry Laptop posted twice :/
But maybe [this]("http://www.google.de/url?sa=t&source=web&cd=1&ved=0CBsQFjAA&url=http%3A%2F%2Flinux.die.net%2Fman%2F8%2Fxfs_repair&rct=j&q=man%20xfs_repair&ei=5Ng1TYDyBcPKswaursCSCg&usg=AFQjCNFlveTk51ttw24u2YzbkW1Pu2Z-vg&cad=rja") will help. Its the Manpage.
Or you can acess it by typing "man xfs_repair" into your terminal ;)

---

### Post by GoBears2011 on 2011-01-18
I may be back in business!!!

I figured based on the size the /dev/sdc4 partition was what I cared about so I did some testing with sdc2.

I tried diag mode -
sudo xfs_repair -n /dev/sdc2 

then I tried 
sudo xfs_repair /dev/sdc2

This threw an error back basically telling me I had to unmount and remount the drive.  Which is the problem - the drive won't mount.  It also warned me I could use the "L" option as well.

The L option is "Force Log Zeroing.  Forces xfs_repair to zero the log even if it is  dirty  (contains  metadata changes).  When using this option the filesystem will likely appear to be corrupt, and can cause the loss of user files and/or data."

Still using sdc2 to experiment -
sudo xfs_repair -L /dev/sdc2

I tried sudo mount /dev/sdc2 - nothing happened.  I then unplugged and reconnected the drive.  SUCCESS!!!  I can access this partition which turns out to be the media server portion of the drive.

I now felt I had the guts to attempt the /dev/sdc4 partition and followed the same steps.

SEEMS TO HAVE WORKED!!!!!!!!

My folder structure and files are back!  I immediately started copying everything from /dev/sdc4 to a different drive.  There is 202 GB and it is running at approx 14 MB a second.  I should know for sure in a few hours.  I'll report back.

Thanks a million!

---

### Post by Lukiwuki on 2011-01-18
No problem :)
Im glad it worked :)

---

### Post by GoBears2011 on 2011-01-18
The complete directory/folder structure is intact along with the file names – which I’ve read are commonly lost when drives are recovered.  I’ve successfully copied the contents off that drive and will focus on a more robust data storage solution.
 
I am amazed by my 4 day Linux/Open Source experience.  It’s amazing that there are thousands of people out there perfectly happy to work for free AND the stuff works well!  I realize I got very lucky - but to think a free Open Source utility succeeded where every commercial Windows product I tried failed – really causes me to rethink this Open Source movement.  I will be keeping this old laptop on Ubuntu and probably load it up in VMWare on my other tower as well.
 
I will be dancing the jig and drinking Irish whiskey in celebration tonight.

Thanks again!

---


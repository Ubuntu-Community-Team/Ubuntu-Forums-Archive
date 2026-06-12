---
title: "Karmic file system check problems"
date: 2009-11-13
forum: General Help
---

### Post by 5nak3 on 2009-11-13
Hi all,

Right I was having this problem with intrepid and disabled fsck, never had a problem with jaunty and now with karmic it has come back to haunt me.

Basically on every 30 or so boots the computer will run a file system check which is great. However, it will hang. The text will become garbled, the  splash screen will become warped in some way (e.g. logo breaking up) and the whole PC will freeze.

To get by this problem I have to press escape, wait until the message saying ctrl+d will resume the check. And then press ctrl+d to go back to the check at which point hopefully and with some luck the check will complete.

If I don't press escape in time the PC will freeze and result in a hard reboot!

So I would like to know if anyone has had this problem and if so how to get around it. 

Or better still I would like to disable the checks all together and run them via live CD.

Many thanks

---

### Post by philinux on 2009-11-13
Open  system>admin>disk utility. In the right hand pane you'll see a blue underlined link "More information". Click that and have a look to see if there's any problems with the hard drive.

---

### Post by 5nak3 on 2009-11-13
Hi thanks for pointing that out.

Well the assessment has come back as "Disk has a few bad sectors"

A lot of the test assessments came back as N/A with the only warning being indicated as:

Reallocated Sector Count: 
Normalised: 100
Worst: 100
Threshold: 50
Value: 7 sectors

I'll be honest I don't know what this means. So any help with it will be useful!

---

### Post by philinux on 2009-11-13
Fsck is doing it's job then. I would give fsck a go from the live cd.

A few bad sectors is not a problem. But I would have a look through /var/log/messages and see if there are any read write errors in the log. It could indicate a failing hard drive.

I would definitely make sure I had good backups of anything important.

---

### Post by 5nak3 on 2009-11-13
Well i had a look at the log and found this error coming up quite often

Nov 11 10:50:09 rob-laptop kernel: [   12.143099] piix4_smbus: probe of 0000:00:14.0 failed with error -16

Other errors included a program error (sound juicer)

Nov 11 11:48:14 rob-laptop kernel: [ 3497.864266] sound-juicer[3269]: segfault at 0 ip 0805c99b sp bf9bb480 error 4 in sound-juicer[8048000+29000]

And 

Nov 11 23:31:05 rob-laptop kernel: [ 2254.332193] nautilus[2858]: segfault at e5895597 ip 00b27803 sp bffdb4a0 error 5 in libgobject-2.0.so.0.2200.2[b02000+3c000]

None of these really mean much to me...if needed I might start looking at a new hard drive. I have my backups but still this is a major inconvenience mainly because the time it takes to setup the PC.

---

### Post by 5nak3 on 2009-11-22
Hi all,

I ran into the problem described in the first post again today.

So basically as I have found no fix, and since I do not have the money for a new HDD I was to stop fsck all together in karmic. I will run the check via live cd which works for me. 

Can someone please explain how to stop fsck completely?

Many thanks!

---

### Post by 5nak3 on 2009-11-29
Still looking for a way to turn off fsck on boot, as again this morning I had to hard reset the PC to get it running. 

Any solutions.

---

### Post by john newbuntu on 2009-11-29
One way:
Edit/open the file /etc/fsck as root(using sudo or gksudo).  You need to change the last field (6th) of the uncommented lines to 0.  Save the file.

Another way:
Presuming /dev/sda2 to be your linux root partition, run this command from a terminal
```
sudo tune2fs -l /dev/sda2
```

Note the 2 values: "max count" and "mount count".  Every time you boot, the mount count is incremented by 1.  When it reaches max count, fsck gets run.  You can change this max count to a high value so that fsck happens less frequently.  The command to set it to, say run fsck after 200 boots:

```
sudo tune2fs -c 200 /dev/sda2
```

---

### Post by Junkieman on 2009-11-29
Hi 5nak3. I stumbled on your post looking for another answer.

To disable fsck you need to edit your fstab file, and change the fsck option for your ubuntu partition to 0, that will disable disk checks.

First you have to backup your fstab file, in case anything goes wonky:

```
sudo cp /etc/fstab /etc/fstab.bak
```next you can edit it like so

```
sudo gedit /etc/fstab
```That should do it. Info on the fstab file format can be [found here]("http://www.debianhelp.co.uk/fstab.htm").

Hope this helps :D

Edit: As an example, my fastab contained this line:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=71123120-9dbc-4eb5-ac09-dc81cbfc44a4 /               ext4    errors=remount-ro 0       1
```
Change the last column value 'pass' to 0, to disable fsck for that partition

---

### Post by 5nak3 on 2009-11-29
Hi thank you so much for the information!!!

It isn't so much that the file system check annoys me. But rather the fact that it forces my computer to freeze whenever it is run.

I noticed by using the recovery option in grub and in turn not loading xspalsh I could complete the fsck. The thing is when xsplash loads the fsck will not run and so I'll just run it via live cd :)

---


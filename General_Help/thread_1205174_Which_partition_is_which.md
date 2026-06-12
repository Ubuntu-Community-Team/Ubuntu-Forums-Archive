---
title: "Which partition is which?"
date: 2009-07-05
forum: General Help
---

### Post by arsenic_creed on 2009-07-05
Somehow (Seriously I don't remember how. I've been playing Warcraft a lot lately so I haven't been on Ubuntu.) I managed to change my dual boot. I had windows xp on one partition and Ubuntu on the other and the swap one. 
Now I have two Ubuntus and one Windows XP. Neither Ubuntu installation is working and, as I have nothing important on them, I was going to uninstall both and then reinstall Ubuntu. So I opened GParted to take a look.
In there it's showing:
/dev/sda1    (Which I think is the windows partition because it is the biggest and is the only ntfs.)
/dev/sda2    (ext3 filesystem)
/dev/sda3    (extended; has a pull down menu with the following three things under it.
/dev/sda6    (ext3)
/dev/sda7    (linux swap)
/dev/sda5    (linux swap)

Which ones are the Ubuntu installations?

---

### Post by matrixblue on 2009-07-05
Everything except the /dev/sda1 is Ubuntu

---

### Post by arsenic_creed on 2009-07-05
So could I use GParted (off of a live disk) to get rid of all but sd1 and then reinstall Ubuntu? Or would that mess something up?

---

### Post by michy99 on 2009-07-05
If you are going to reinstall, then deleting the linux partitions will be ok. Be sure to back up any personal data you want to save.

---

### Post by matrixblue on 2009-07-05
The best way to do it is to start the Ubuntu install from the live CD. But when it gets to the part about disk allocation, select manual. From there delete all the partion except sda1 and create a new ext3 or ext4 partion and a swap partition that is at least equal to the amount of RAM you have.

Make sure set the mount point of your new ext3 or ext4 partition to "/" then just continue the install as normal and everything will be set.

---

### Post by arsenic_creed on 2009-07-05
Alright, I did as martrixblue said so far but got an error when it started installing the system.

> The ext3 file system creation in partition #2 of SCS14 (0,0,0) (sda) failed.

When I hit okay it reopened the partitioner. I had to reselect manual and it is now showing me my partitions.

---

### Post by matrixblue on 2009-07-05
Try deleting the ext3 and swap partions first and apply the changes then create the new ext3 and swap partitions.

You may wanna choose this moment to upgrade to ext4 which has speed improvements and will be the default file system in the new Ubuntu release while you at it.

---

### Post by flyingsliverfin on 2009-07-05
yea, but ext 4 still has some data loss errors and you need  a seperate partition for grub i think

---

### Post by arsenic_creed on 2009-07-05
What do you mean by 'apply the changes'? If I delete the ext3 and swap partitions I can't go to the next step because I haven't specified a partition for the root file system. That's what ext3 is. 
Also, I can't use anything as ext4. It's not in the use as list when I make partitions.

(P.s. The live CD I have is 7.04. That's the last time I've done Ubuntu installations.)

---

### Post by flyingsliverfin on 2009-07-05
oh yea, you might not want to use that CD, its really outdated

try to get your hands on a 9.04 or 8.04 or 8.10 CD. i dont think that 7.04 is even supported any more)i had lots of trouble upgrading it later on when the repos were "gone"

---

### Post by sdlynx on 2009-07-05
Instead of going into the installer off the live disc choose to try Ubuntu and open up the Partition Editor and delete your linux partitions from there.  Then proceed to install and allocate the partitions manually.

---

### Post by matrixblue on 2009-07-05
Yeah you do seriously need to upgrade. Ext4 is available in Jaunty (9.04) and you don't need a separate boot partition to use it.

---

### Post by arsenic_creed on 2009-07-05
flyingsilverfin: I remember updating to which ever one was right after 7.04 but I don't remember having trouble with it. Unique experience, or something?\
Anyway, I'll see what I can do about getting a newer disk.

sdlynx:  That's what I'm doing. I booted from the disk and opened the partitioner from there. I deleted the two old Ubuntu partitions that I was getting rid of and then opened the installer.
Am I misunderstanding you?

matrixblue: I was hoping I could install from the disk I have and then upgrade. My disk burner is currently out getting fixed and I didn't really want to wait for another disk. The free-ness, while wonderful, means that receiving an actual disk takes a while. (Or at least it did when 7.04 came out...)

---

### Post by flyingsliverfin on 2009-07-05
it doesnt say what the error was except what you posted right?
im wondering if CDs keep temproary logs

---

### Post by velopimp on 2009-07-05
hey all, 

i am having a similar issue with multiple ubuntus.  i also seem to have a bit of difficulty booting from the cd ( i had to do the whole 'get help booting from a cd' thing) for the install.

longish story short:  installed ubuntu with only 2.5 GB by accident.

got mad

tried to follow instructions to partition and reinstall

installation failed

installation succeeded

now ubuntu shows up 3 times in the os selection menu....

also, my external was plugged in during the install and now it has some sort of ubuntu stuff on it (like a back up of my files???)....

i didn't ask for that and i would like to get rid of it.



any thoughts on this?

---

### Post by arsenic_creed on 2009-07-05
I posted exactly what it said. (As to your wondering, I have no idea. If wonder how they would.)

---

### Post by sdlynx on 2009-07-05
when you choose to make the partitions manually for the one that is ext3 you have to choose to make it mount at "/".  Then you won't have a no root filesystem error.  As for the cannot create ext3 partition error I'm not sure what you can do.

@velopimp I suggest you delete everything you have that is Ubuntu (ext3/2 and swap partitions), but backup what you need first, and then try to install a clean installation

---

### Post by arsenic_creed on 2009-07-05
When I got the error earlier I had set it to mount at "/". At least, I thought I had. I tried re-making the partitions again and making absolutely certain that it was set and got a different error when I tried to go forward. (Didn't even get to the installation point this time.)

> The file system on /dev/sda2 assigned to / has not been marked for formatting. File systems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other file systems (/home, /media/*, /usr/local, etc.) may be used without reformatting.

---

### Post by sdlynx on 2009-07-05
> **arsenic_creed said:**
> When I got the error earlier I had set it to mount at "/". At least, I thought I had. I tried re-making the partitions again and making absolutely certain that it was set and got a different error when I tried to go forward. (Didn't even get to the installation point this time.)

Isn't their like an 'OK' and 'Cancel' option for when that pops up? There is for me.

---

### Post by arsenic_creed on 2009-07-05
There's an okay that just closes it and leaves you again at the partitioning screen. It opens whenever you hit forward. 
I don't have a cancel button, though.

---

### Post by matrixblue on 2009-07-05
I still say you need to upgrade. OSDisc.com should ship you a new CD pretty fast (2-5 days if you're in the US) for $3.50 (shipping included). 

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu?ad=distrowatch](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu?ad=distrowatch)

Or try reaching a LoCo team near you who'll be happy to give you a CD.

---

### Post by sdlynx on 2009-07-05
If you're doing a clean install set it to also format the partition that it gives you an error when you hit format, I think that might do it.

Or if you have it set to formatting it, set it to not to...

---

### Post by arsenic_creed on 2009-07-05
Yeah, I'm doing a clean install.
So, check the box in the 'format?' column for /dev/sda2? That's all I'd have to do to set it to format, right?

---

### Post by arsenic_creed on 2009-07-05
I marked it for formatting and it got me all the way to the installation step again. It started and then I received the first error again.

In case you don't remember and so you don't have to look back the error was:
> The ext3 file system creation in partition #2 of SCSI4 (0,0,0) (sda) failed.

---

### Post by merlinus on 2009-07-05
Did you select a mountpoint for that partition?

---

### Post by arsenic_creed on 2009-07-05
The ext3 one is the root file system partition so it was set to "/".

---

### Post by sdlynx on 2009-07-05
Sorry but I don't know what to do for that.

It was happening to me when I decided to try out openSUSE so I gave up and installed Ubuntu lol

---

### Post by arsenic_creed on 2009-07-06
:biggrin:
 I got my (repaired) disk burner back early (really early) this morning. Burned the .iso of 9.04 and installed it. It worked fine, so I think it might just be because my disk is so old. 

(P.s. The partitioning screen for 9.04 was really cool. I liked how it recognized which partition was my windows one and everything. Very nice.

---

### Post by sdlynx on 2009-07-06
> **arsenic_creed said:**
> :biggrin:
 I got my (repaired) disk burner back early (really early) this morning. Burned the .iso of 9.04 and installed it. It worked fine, so I think it might just be because my disk is so old. 

(P.s. The partitioning screen for 9.04 was really cool. I liked how it recognized which partition was my windows one and everything. Very nice.

Oh haha thats good and I always figured gparted looked the same but cool.

---


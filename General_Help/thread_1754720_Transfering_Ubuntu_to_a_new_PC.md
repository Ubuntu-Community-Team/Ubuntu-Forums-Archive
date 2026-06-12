---
title: "Transfering Ubuntu to a new PC"
date: 2011-05-10
forum: General Help
---

### Post by meddyuk on 2011-05-10
Hiya Guys,
 
This is just a query really. I've just been given a new desktop and wondered if i could easily transfer the Ubuntu environment that i already run on my current PC, to the new one without actually taking the IDE Harddrive out and installing it.
 
Would i be able to just back up my Ubuntu to a disk, Install Ubuntu fresh on the new PC and then do a restore?
 
Look forward to your comments.
 
Cheers.

---

### Post by chirag64 on 2011-05-10
Just copy all contents of your home folder (including the hidden files and folders) to the home folder of your new PC. You will get all your settings this way....
You can use Ubuntu One to copy all these files on the cloud and then download them all via Ubuntu One of the new PC, instead of using a physical device to copy-paste everything.
I haven't tried this myself, but it should work properly

---

### Post by alenis on 2011-05-10
You can also try Clonezilla and copy everything from the old disk to the new one. Copy all the partitions. Then, if the new PC has a larger disk, you can use gparted to enlarge the partitions.

If it doesn't work you can always install ubuntu and copy the home directory as suggested in the previous post.

---

### Post by deserthowler on 2011-05-10
> **meddyuk said:**
> Hiya Guys,
 
This is just a query really. I've just been given a new desktop and wondered if i could easily transfer the Ubuntu environment that i already run on my current PC, to the new one without actually taking the IDE Harddrive out and installing it.
 
Would i be able to just back up my Ubuntu to a disk, Install Ubuntu fresh on the new PC and then do a restore?
 
Look forward to your comments.
 
Cheers.

I use remastersys for this and it works great.
Earl

---

### Post by meddyuk on 2011-05-14
The new PC has got vista on it. I hate Vista, but need it for the Itunes for the missus' Iphone and Ipod.

I'm interested in the clonezilla but im wondering if i'm able to load it onto the new pc whilst keeping the Vista?

My only other choice would be to install Ubuntu fresh on the new PC and then using my home folder from the old PC. But it seems a pain to set the newly installed Ubuntu up all over again so it looks like this one.

---

### Post by pqwoerituytrueiwoq on 2011-05-14
you can copy your partition(s) to the other hdd and it will run fine (may be issues if yuo have proprietary drivers on one system)
rhythmbox has a ipod plug-in, though i never used it i just use [rebuild_db]("http://shuffle-db.sourceforge.net/") on my ipod shuffle
as for the iphone i done have one so idk on that
edit according to alternativeto.net Spotify is a alternative to itunes

---

### Post by meddyuk on 2011-05-14
I dont suppose you know how to do this do you without losing the vista that is on the new machine?

---

### Post by linuxuser12345 on 2011-05-14
Use the Deja Dup backup tool, and back everything up to a flash drive.

---

### Post by meddyuk on 2011-05-14
I know i can back my files up, but i want to know about installing it onto the new PC which currently has Vista on it. I want to be able to dual boot, but dont know whether this can be done without actually installing Ubuntu from fresh.

---

### Post by ManualSparrow on 2011-05-14
You can do a 'fresh' install of Ubuntu, then copy your old home folder onto it to restore all of your docs and a lot of your settings (as mentioned above). 

You could MAYBE use DejaDup to backup the old machine, then install Ubuntu and DejaDup on the new machine and use that to 'Restore' the old machine to the new one. I don't know if that will cause the hardware to be mismatched with the config files, but it might work.

EDIT:
I don't if this is possible, but you could:
Make a LiveUSB, boot it in trial mode, and use GParted to shrink your Vista Partition and create a new partition in the leftover space. Then use one of those tools to copy the specific Ubuntu partition you have on the old drive onto the newly-created partition. I don't know how you would link all of those devices together, though - it sounds like you would need to create an adhoc network or something.

(Plus, you would need to get GRUB on the MBR, which wouldn't happen automatically in this case but would if installed Ubuntu directly).

---

### Post by meddyuk on 2011-05-14
I'm wondering if it's worth cloning the new PC hard drive with this Ubuntu and then re-installing Vista inside Virtual box?

---

### Post by wilee-nilee on 2011-05-14
> **meddyuk said:**
> I'm wondering if it's worth cloning the new PC hard drive with this Ubuntu and then re-installing Vista inside Virtual box?

You can clone it the Ubuntu and if you have enough HD space on the new drive to make a partition for the Ubuntu clone equal or larger then the original and just slip it in. You just need to shrink the Vista.
[http://clonezilla.org/](http://clonezilla.org/)

Personally I never do a backups I clone it, and keep those images and all the stuff I can't loose on a external HD.

You can clone the vista as well after you shrink or and /or before this and do the same, and have your self covered there as well.

---

### Post by meddyuk on 2011-05-15
Ok ive decided to use GParted to reduce the Vista partition. I've also used Clonezilla to make an image of my current Ubuntu machine. The intention is then to clone the unallocated partition on the new machine.

Do i have to fomat the unallocated partition to ext 3/4 before doing this or will clonezilla give me the option to clone the unallocated partition?

---

### Post by wilee-nilee on 2011-05-15
> **meddyuk said:**
> Ok ive decided to use GParted to reduce the Vista partition. I've also used Clonezilla to make an image of my current Ubuntu machine. The intention is then to clone the unallocated partition on the new machine.

Do i have to fomat the unallocated partition to ext 3/4 before doing this or will clonezilla give me the option to clone the unallocated partition?

You make a partition of the same type same size or larger, and it will load the mbr as well so once your image is in boot to it and run.
sudo update-grub 
to pick up the Vista and add it to the grub menu.

---

### Post by meddyuk on 2011-05-15
what about the swap partition will that go over as well?

---

### Post by meddyuk on 2011-05-15
well that didnt work. I initially had 3 partitions on the drive, sda1, sda2(recovery) sda 3 (vista). I used gparted to reduce sda3, then i allocated the rest of the drive to ext3. I used clonezilla to restore the image on sda3 but when i went to reboot, i had a warning, saying there wasn't anything to boot.

I'm now reinstalling vista. im thinking of just booting from the live ubuntu cd and dual booting that way

---

### Post by wilee-nilee on 2011-05-15
> **meddyuk said:**
> what about the swap partition will that go over as well?

I would have saved only the partitions needed. The swap is a delete and create when needed. I'm not sure here I have never done a full HD save then slipped it into another in a dual boot. I suspect that if you build the exact same set up in the new HD that clonezilla will install exactly as it was cloned.

In the future you might only save partitions, that have a OS or data, that is what  do, but I change the OS on my computer often, but I havent done it the way you have whicj=h probably works fine.

The cool thing about back ups is that you can copy and paste them into another folder and have a back up of your back up.

---

### Post by wilee-nilee on 2011-05-15
> **meddyuk said:**
> well that didnt work. I initially had 3 partitions on the drive, sda1, sda2(recovery) sda 3 (vista). I used gparted to reduce sda3, then i allocated the rest of the drive to ext3. I used clonezilla to restore the image on sda3 but when i went to reboot, i had a warning, saying there wasn't anything to boot.

I'm now reinstalling vista. im thinking of just booting from the live ubuntu cd and dual booting that way

You had 3 partitions with vista, you could only add one more primary or a extended which could hold as many logical's you could fit in.

It sounds like you may have either made 5 partitions or don't understand the loading of the mbr. If you have it still in place the transfer follow theses instructions so if fixable we can do it.

So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

There is a good reason why I suggested cloning everything, if you have clones of everything and the Ubuntu still in place on the first HD, you just need to slip the vista in if detroyed and just clone the partion the UBuntu is in and get on the same page here.

Post the bootscript though if you have the broken HD with everything still in place.

---

### Post by meddyuk on 2011-05-15
Just had a search for my original ubuntu ISO and only managed to find the netbook iso. I dont suppose i can install this one can i? Looks like i may have to put this project on hold until i download the desktop iso.

---

### Post by meddyuk on 2011-05-16
Right, im not giving up! Everytime i clone just the partion i lose the abilitly to boot into ubuntu.
 
If i clone the full disk am i then able to just restore it to the partition. Any step by steps would be usefull.

---

### Post by dandnsmith on 2011-05-16
You lose the ability to boot because the grub needs to be installed after you load the new ubuntu partition from the clone info.
You cannot restore the full disk, as the partition setups will be different.
There is a downloadable iso image for a CD from which you can boot any of you operating systems (forget what its called, but try [Ultimate Boot CD ](http://www.ultimatebootcd.com/faq.html)), and once booted you'll be able to use ubuntu to install Grub2 (as that is what comes with 11.04).
I advise looking for a tutorial on installing/reinstalling grub2.

---

### Post by meddyuk on 2011-05-16
ok, i've just reformatted the new pc's hard drive. I loaded Vista back on and then reduced it. I then installed the Ubuntu Netbook iso disk and installed it manually, by partioning the hard drive into:

sda1 = ntfs
sda2 = /home
sda3 = /
sda5= swap

The problem i have now is the original / that i want to clone is on sdb1 and i get an error message saying Failed to restore partition image file  /tmp/2010-07-29-18-img-tmp-cnvted/sda3* to /dev/sda3! Maybe this image  is corrupt! Press "Enter" to continue......"

Ive got a feeling its because im not moving it to a partion that is named the same. Any help with this?

---

### Post by meddyuk on 2011-05-17
I've read somewhere that i need to rename the image. How do i do this?

---

### Post by meddyuk on 2011-05-18
Manged to get somwhere but its far from sorted.
 
I saved the image to an external hard drive and then renamed that image so that it matched the drive of the new machine, i.e. from sdb1 to sda3. I then renamed the parts.txt file to the same.
 
When it came to restoring, i had to reinstall grub 2, and that worked. I got the exact same grub screen as the old machine, however i have now got 2 new problems.
The grub from the old machine has got XP as a dual boot, however  Vista is on the new machine and therefore I am unable to boot into that.
 
Also when i boot into Ubuntu i get a message saying that /home drive is not ready, either wait, press S to skip or M to sort it manually.

I waited that did nothing. I pressed S to skip and it booted to black screen and did nothing. If i choose M for manual then it brings up the command root prompt.
i had nvidia drivers on the old machine, im wondering if this has anything to do with why it shows a black screen after pressing S? 
 
I wonder if this has a problem with etc/fstab, which reportedly needs altering after a clone. However i dont know how to do this
 
Anyone knowing how to sort this will be saving me a massive headache!

---

### Post by pqwoerituytrueiwoq on 2011-05-18
> **pqwoerituytrueiwoq said:**
> you can copy your partition(s) to the other hdd and it will run fine (may be issues if yuo have proprietary drivers on one system)
rhythmbox has a ipod plug-in, though i never used it i just use [rebuild_db]("http://shuffle-db.sourceforge.net/") on my ipod shuffle
as for the iphone i done have one so idk on that
edit according to alternativeto.net Spotify is a alternative to itunes
> **meddyuk said:**
> I dont suppose you know how to do this do you  without losing the vista that is on the new machine?
shrink the vista partition and copy ubuntu's partition next to it
then it is just a matter of reinstalling grub ([https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT))

---

### Post by dandnsmith on 2011-05-18
> **meddyuk said:**
>  
Also when i boot into Ubuntu i get a message saying that /home drive is not ready, either wait, press S to skip or M to sort it manually.

I waited that did nothing. I pressed S to skip and it booted to black screen and did nothing. If i choose M for manual then it brings up the command root prompt.
i had nvidia drivers on the old machine, im wondering if this has anything to do with why it shows a black screen after pressing S? 
 
I wonder if this has a problem with etc/fstab, which reportedly needs altering after a clone. However i dont know how to do this
 
Anyone knowing how to sort this will be saving me a massive headache!

I had a happening like that a couple of times recently.
I reckon that the easiest way to sort it out is to boot from a live CD, and then check on what the grub menu entry is, and what is in the fstab.

You can then use blkid to find the current partition  ISs are, and update the fstab and, possibly the menuentry, accordingly.

When you have that right, you'll be able to see if there really is a graphics problem (but there shouldn't be, unless you've installed special hardware drivers, eg nvidia, which aren't needed, or have hand configured the graphics entry)

---

### Post by meddyuk on 2011-05-19
SO i need to uninstall the nvidia drivers and update the fstab. How do i so this from the command line or from the live cd?

---

### Post by dandnsmith on 2011-05-20
I'd do the fstab update from a terminal window, invoked from the LiveCD.

Don't know about the nVidia stuff, as I've never installed it, and don't know what it entailed or what shape mess it leaves behind.
Added to which are the recent changes to what is included in the releases - I'm under the impression that some of the changes relate to how the graphics are handled (since 10.04).

Have you done any xorg configurations (which would be better removed now)?

---

### Post by linuxinstalledfromhdd on 2011-05-20
If I bought a new computer and I wanted to install a clone of my entire system. And can remove anything that can be easily backed up to an external drive, to get the space under 4.7 Gb total.  

You can install remastersys and do a complete clone of your system and burn it to a live installation disc of Ubuntu.  

(this lists  karmic, but don't change it) 
sudo su
sudo echo "deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/" >> /etc/apt/sources.list
sudo apt-get -f update && sudo apt-get upgrade
sudo apt-get install remastersys ubiquity-frontend-gtk

---

### Post by meddyuk on 2011-05-20
Got so fed up with the longwinded way of doing it, i just installed maverick updated to natty and installed the relevant packages. Easy. Thanks for your help.

---


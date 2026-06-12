---
title: "Cannot Install Ubuntu  Need some guidance for new Ubuntu user"
date: 2012-03-19
forum: General Help
---

### Post by mwkeeler on 2012-03-19
I downloade Ubuntu to a thumb drive and can boot up without a problem on the thumb drive.
 
I have a dell XPS that got hit with a virus and it was too painful to remove it. I wiped the hard drive clean using the XP install disc (NTSF). When I tried to install and run windows it said that the drive was not available. I gave up at this point and got out my thumb drive and booted up in Ubuntu. :lolflag:
 
I formatted and partioned the hard drive using the disk utiliities. It was extremely fast and this got me concerned. I formated a 150 gb and 100 gb partion. It took less than 10 seconds for each. I formatted one in NTSF and the other in FAT. Is FAT the same as FAT 32? 
 
How do I install Ubuntu? When I click on the install icon, it says that the installation is starting. I get that annoying spinning wheel! Nothing happens. 
 
I know that I am not the only new Ubuntu user with this problem. If you can point me to a thread that helps me I would be so happy!
 
What if my hard drive is dead? I can buy and install a new hard drive. Just not sure how to get it working. Do I need to install the BIOS so that it recognizes all the Dell hardware?
 
Worst case scenario: Anyone know of a 5000 foot cliff to throw my Dell off into the abyss?
 
Cheers!
 
Mark

---

### Post by Paqman on 2012-03-19
NTFS and FAT32 are Windows filesystems. Ubuntu can read and write to them, but you can't install it on them. If you're not dualbooting, there's no advantage to keeping any NTFS or FAT32 partitions around, just delete them and start from scratch. The Ubuntu installer will create any filesystems it needs. By default it will create a single EXT4 partition and a swap partition.

---

### Post by grahammechanical on 2012-03-19
Do you live anywhere near Beachy head on the south coast of England?

Let us try one thing at a time.

How far do you get when you try to boot form the live USB? What version is it anyway, 11.10?

Can you select Try Ubuntu? How well does that work?

To install do you select Install at that first screen or do you let the Try option load and then click the Install icon on the Desktop?

Both should work but sometimes we may get better success with one method or the other.

Can you run the live USB and then run Disk Utility and tell us what information it gives you about the hard disk? A screenshot would be nice if that is possible.

Regards.

---

### Post by mwkeeler on 2012-03-19
I have version 10.10 installed on the thumb drive.  it does not give me an option of where to install it.  I reformatted the hard drive for ubuntu. 

 I made some screen captures but I am not sure how to put them in this post.  I uploaded them but don't see them.

Do you think it's trying to install on the thumb drive?  

I tried to install the latest version and it sent all the files to the thumb drive!  Where is the option to choose a install destination?

Thanks for all the quick replies.  This forum is outstanding!

Mark

Bay Area California.

---

### Post by Paqman on 2012-03-20
> **mwkeeler said:**
> it does not give me an option of where to install it.

After you click through those screens you showed it will come up with a page of various options for installing, including wiping the whole drive, or the enigmatically-named "do something else". Do you get that screen?

---

### Post by mwkeeler on 2012-03-20
It does not come up with a page of various options for installing, including wiping  the whole drive, or the enigmatically-named "do something else".

---

### Post by dino99 on 2012-03-20
my own way : [http://ubuntuforums.org/showpost.php?p=11654218&postcount=3](http://ubuntuforums.org/showpost.php?p=11654218&postcount=3)

---

### Post by mwkeeler on 2012-03-20
> **dino99 said:**
> my own way : [http://ubuntuforums.org/showpost.php?p=11654218&postcount=3](http://ubuntuforums.org/showpost.php?p=11654218&postcount=3)

Thanks for the advice.  However, since I am having such issues while attempting to install Ubuntu, the install of this program looks even more complex.  Here is the warning that I just read on the download page 

"[COLOR=#FF0000]*NOTE: Partitioning is serious business  and if you can't figure out how to burn a CD image, you probably  shouldn't be attempting to use this program in the first place. Trust  me, this is going to end badly. Find a friend to help you and **BACK UP YOUR DATA!***[/COLOR]"

I have nothing to loose since my hard drive is completely erased.

My main issue now is that I cannot install from the simple Ubuntu install program.  I know that Ubuntu is great because people rant about it.  However, I have found that I am not alone in having issues installing it.

---

### Post by wildmanne39 on 2012-03-20
Hi, in the screenshot did you put a check by download updates while installing and third party software then hit forward? If so what happened?

Here is a link for manually partitioning.
[http://ubuntuone.com/6snmL8cnGbpYPBegqcHrnr](http://ubuntuone.com/6snmL8cnGbpYPBegqcHrnr)
Thanks

---

### Post by mastablasta on 2012-03-20
> **mwkeeler said:**
> I downloade Ubuntu to a thumb drive and can boot up without a problem on the thumb drive.
 
I have a dell XPS that got hit with a virus and it was too painful to remove it. I wiped the hard drive clean using the XP install disc (NTSF). When I tried to install and run windows it said that the drive was not available. 


Are you sure you wiped the whole drive even the boot sector? some nasty viruses can hide there.

> 
I formatted and partioned the hard drive using the disk utiliities. It was extremely fast and this got me concerned. I formated a 150 gb and 100 gb partion. It took less than 10 seconds for each. I formatted one in NTSF and the other in FAT. Is FAT the same as FAT 32? 
 Fat16 is old, FAT32 is newer but still not usefull a lot. Since it fragments and can't support files larger than 4GB and also can't support partitions larger than 130 GB or so.
NTFS is windows partition format that is in now common use.

Ubuntu Linux uses (usually) Ex3 or Ext4. so i am not sure i see any use in your partitions. Additionally just delete one of them and then choose install the Ubuntu on largest free disk space (assuming you want windows on the other paritition. if you want only ubuntu on your disk then delete both partitions and select use whole drive (or similar) during install.
> 
How do I install Ubuntu? When I click on the install icon, it says that the installation is starting. I get that annoying spinning wheel! Nothing happens. 
 [/QUOTE]
here is how Ubuntu install looks like screen by screen.: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

i hope you did a md5sum check of your image after the download and used a trustworthy programme such as unebootin or LlinuxliveUSB or pendrivelinux to "burn the image on the USB stick.

---

### Post by mwkeeler on 2012-03-21
Thanks for all the help!  How to I delete the small boot sector to get rid of the nasty viruses that hide there? 
 
I got Unbuntu 11.04 installed with no problems.  My dvd/cd drive died and that was one of the problems.
 
I will get a new one then install windows for dual boot.

---

### Post by mwkeeler on 2012-03-27
> **mastablasta said:**
> Are you sure you wiped the whole drive even the boot sector? some nasty viruses can hide there.


here is how Ubuntu install looks like screen by screen.: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

i hope you did a md5sum check of your image after the download and used a trustworthy programme such as unebootin or LlinuxliveUSB or pendrivelinux to "burn the image on the USB stick.[/QUOTE]

Do I have to be concerned about viruses in Ubuntu?  I used the disk utility on the thumb drive to reformat the 250 gb hard drive.  I have no idea how to wipe out the boot sector.  Any suggestions?

Thanks for all the help!  My install really looks great.  I installed the Macbuntu theme because my wife and I both use Macbooks and I don't want to teach her another system.  She freaked out when I suggested that she start using a Macbook because she is always getting viruses.  Hence, she wiped out my Dell XPS again.  By by Windows!

---

### Post by aerom on 2012-03-27
> **mwkeeler said:**
> I downloade Ubuntu to a thumb drive and can boot up without a problem on the thumb drive.
 
I have a dell XPS that got hit with a virus and it was too painful to remove it. I wiped the hard drive clean using the XP install disc (NTSF). When I tried to install and run windows it said that the drive was not available. I gave up at this point and got out my thumb drive and booted up in Ubuntu. :lolflag:
 
I formatted and partioned the hard drive using the disk utiliities. It was extremely fast and this got me concerned. I formated a 150 gb and 100 gb partion. It took less than 10 seconds for each. I formatted one in NTSF and the other in FAT. Is FAT the same as FAT 32? 
 
How do I install Ubuntu? When I click on the install icon, it says that the installation is starting. I get that annoying spinning wheel! Nothing happens. 
 
I know that I am not the only new Ubuntu user with this problem. If you can point me to a thread that helps me I would be so happy!
 
What if my hard drive is dead? I can buy and install a new hard drive. Just not sure how to get it working. Do I need to install the BIOS so that it recognizes all the Dell hardware?
 
Worst case scenario: Anyone know of a 5000 foot cliff to throw my Dell off into the abyss?
 
Cheers!
 
Mark
hello, i'm not a expert, but learning all about sitems so after read your message think i have to say you something!
well, i think you should not be despered, usually your bios is not affected, however to have shore, you can do it yourself, easy, when start pc, see what he show you on screen( first seconds after you press start and screen turn's on- usually F2, F10, F12 or another it depend's of the pc), usually he tell's you to press some keys to have acess to bios or boot menu, ( if necessary reboot) so, you should chose, bios and there search for bios settings, there you should chose default, and that's all; about your hard disk, usually you should see in your pc, if your hard drive works, usally pc's got a smal led that indicates the disk is running, however, ubuntu is light, so make shore you got a good instalation CD, note, when you copy image for CD, you should aply the lowest speed! Usually Ubuntu should get instaled, even if multiple sectores of you hard drive are death, i've experimented myself already and i get it done! 
If you can't do it is because your hard drive is death and you got to buy another, not expensive! hope can be helpfull! greatings, peace!

---


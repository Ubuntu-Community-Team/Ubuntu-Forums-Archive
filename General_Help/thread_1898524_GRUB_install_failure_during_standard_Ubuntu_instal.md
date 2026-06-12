---
title: "GRUB install failure during standard Ubuntu install"
date: 2011-12-21
forum: General Help
---

### Post by Attempt on 2011-12-21
Hi All, 

have you encountered such error before:

Grub-install failure at the end of normal Ubuntu installation procedure

(failure of grub-install/dev/sda)

-> the error occurs with or without windows 7 installed, even after a full format of the hard drive and a repartinioning

specs of the computer: SONY VAIO VPCSE with Insyde BIOS (H20)

I am also unable to display the BIOS if windows seven is not installed

the live CD works normally and Ubuntu can be used with it, but installation will fail per the GRUB whether or not launched under the live CD's environment

sudo grub-install /dev/sda also fails in the terminal


thank you very much

---

### Post by BC59 on 2011-12-21
Can you post the results of these commands, when you boot from a Live CD?

```
sudo parted /dev/sda print

sudo fdisk -l
```

---

### Post by Attempt on 2011-12-21
sudo parted /dev/sda print

(I translate from French)

--> error: partition cannot be outside the disk

sudo fdisk -l   ( I assumed it's letter L rather than 1, which was invalid)

--> unable to seek on /dev/sda: invalid argument

---

### Post by Attempt on 2011-12-21
PS: the precise error message to

sudo grub-install /dev/sda 

--> /usr/sbin/grub-probe : error : cannot find a device for /boot/grub (is /dev mounted?)

 /dev is mounted

---

### Post by BC59 on 2011-12-21
In that case can you post a screenshot of the Gparted screen? You have to boot from LiveCD and execute the application Gparted.

---

### Post by Attempt on 2011-12-21
Here it is

for translation: 

"drapeaux" = flags
"étiquette" = label
"utilisé" = used
"inutilisé" = unused

---

### Post by BC59 on 2011-12-21
Anyways Gparted will not clear the situation. 
You have to use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to repair the partitions.
The good thing is that you can use the instructions in French, pushing the flag on the top of the page.

---

### Post by Attempt on 2011-12-21
PS:

"inconnu" = unknown

---

### Post by BC59 on 2011-12-21
Yes I see it. As a first step I would delete with Gparted the last 2 partitions, the ext4 and the other one with the problem.
Then check if you can reinstall Ubuntu.
I'm sure you cannot use now Windows so try first to see if you can install Ubuntu and then you can solve the problem with Windows.

---

### Post by Attempt on 2011-12-21
the computer is brand new, how come the partitions have to be repaired? 

Also, it may turn out that Ubuntu cannot take the VAIO VPC SE drivers. I lost them all while partitioning the hard drive and cannot even find them back for windows 7, but they won't even install on Ubuntu

---

### Post by Attempt on 2011-12-21
Ok let me check

1) I delete the last two partitions with Gparted
2) I reinstall Ubuntu

3) you say I can solve the problem with windows. Sorry for my noobitude but what is the problem exactly? I mean, what is there to solve on windows and how?

---

### Post by BC59 on 2011-12-21
If you like to start repairing the Windows there is a solution:

If you have a Win7 repair CD, then boot from it and run Startup Repair at least three times. 
Maybe it will not work at first, it takes several passes to completely repair the booting process. 
If you don't have the original Windows disc you can download one from [here]("http://www.mydigitallife.info/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/").

---

### Post by BC59 on 2011-12-21
> **Attempt said:**
> Ok let me check

1) I delete the last two partitions with Gparted
2) I reinstall Ubuntu

3) you say I can solve the problem with windows. Sorry for my noobitude but what is the problem exactly? I mean, what is there to solve on windows and how?

We post simultaneously.. 
The problem with Windows is that when installing Ubuntu/Linux, it's installed a new program to control the boot of the 2 systems. This program belongs to Ubuntu, if you don't have Ubuntu you cannot boot. If you like to have only Windows you have to reinstall the Windows program for boot.

---

### Post by Attempt on 2011-12-21
oops, my last post did not go through

I was asking: just for checking

1) I download and install testdrive
2) I delete the last two partitions

3) I fix the problem on windows. yet sorry if I didn't understand: what is the problem exactly and how can I fix it even on windows?

---

### Post by BC59 on 2011-12-21
You have to decide, continue the installation of Ubuntu or leave it and only repair Windows? 
Installing Ubuntu will repair Windows as well.

---

### Post by Attempt on 2011-12-21
Ok I have done just that already

I have a win7 ultimate install disk and have reinstalled it from scratch on a completely formated hard drive (256 SSD) which I have partitioned into two 128 spaces.

Win7 further partitioned one of the 128 Go spaces during the intall. I thought to leave the other 128 space to Ubuntu which I did. But however the partition (I have tried at least a few others before) GRUP won't install

---

### Post by Attempt on 2011-12-21
Ok: so I do have a working windows seven

but all the factory drivers are missing so the computer cannot even connect to the internet and I can't find a single package encompassing all of the drivers

the point is: I'd rather have no windows and a working ubuntu (although I still have to check whether ubuntu can even run on my VAIO because it may not support the drivers)

I hope it is clearer here. thank you very much for your time

---

### Post by BC59 on 2011-12-21
For the Windows you have to download from Sony Support the corresponding drivers for your model. It's not a big problem.
For Ubuntu I write now how you will partition the disc.

---

### Post by BC59 on 2011-12-21
Now to install Ubuntu boot and choose install. Put the corresponding data and when you reach the screen where you asked where do you like to install Ubuntu, choose "something different"
Then starts the application Gparted and you have to create  3 logical partitions for Ubuntu/Linux:

1. The system ( **/** ) about 12-15GB
2. The swap about equal to your RAM installed
3. The rest of the space dedicated to **/home** (inside are the folders Documents, Videos etc).

This way you could reinstall the system in a case of a problem, formatting the **/** but leaving intact the **/home**, on which you will have your personal data.

Then put the rest of the data and continue with the installation.

---

### Post by oldfred on 2011-12-21
The /dev/mapper says you have turned on RAID. Grub then does not install to the MBR, but to the RAID set.

Is this motherboard/BIOS RAID?

I do not know about RAID, but have these links. 

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)

RAID often writes hidden meta data on a drive that will interfere with installs if you are removing the RAID.

---

### Post by Attempt on 2011-12-21
what is RAID ?

Do you mean the motherboard automatically writes metadata that prevents GRUB from being installed whether I am formating the hard drive or not? 

besides, my disk is SSD do I don't think I have a MRB

---

### Post by Attempt on 2011-12-21
Is there any risk I have to reinstall windows if I do that?

---

### Post by oldfred on 2011-12-21
Is this one of those SSD with built in RAID, I think someone before had one of those and it just did not work with Linux. Or is RAID turned on in BIOS?
What SSD is it?

---

### Post by Attempt on 2011-12-21
Sorry for the delay

Well, you may be right about the problem being likely to come from the SSD

Actually I could not display the BIOS setup, neither F2 nor F3 or del worked. So long story short here's what happened from the dleivery of the brand new computer today

- Windows 7 was installed
- I tried to install Ubuntu, had to remake the partition
- the install worked until the GRUB error message came about
- I decided to overwrite windows 7, lost all the drivers of the SONY VAIO
- still the same error message for Ubuntu, whatever the partition

the SSD is an ultraSATA but I have no idea how I can figure out whether it has RAID or not

---

### Post by oldfred on 2011-12-21
When you go into BIOS, you can usually set drives to IDE, SATA, or RAID if it has RAID. Mode should be AHCI with SATA.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

But if you installed Windows with RAID it becomes a reinstall to remove it. And with regular hard drives you scrubed the drive with 0, not sure about SSD.

Normal way to remove RAID meta data, but do not run unless you are sure you do not want RAID.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Attempt on 2011-12-22
OK I think I got it

I opened the BIOS and saw only two options: enable or disable the RAID display, I could not switch from RAID to anything else

Yet as you know an SSD drive is not one drive but 4 blocks of flash memory (64Go in this case) so if I disable or overturn the RAID how can I be sure that my computer will continue to recognize one disk out of those four blocks? 

I ask that because basically I have an awful amount of work to do and I cannot, positively, risk any critical failure of my system now

So sorry to disturb you then, but what would be the safest way?

---

### Post by Attempt on 2011-12-22
update:

I am about to de-RAID all my 4 x 64Go flash units. I believe it will leave me with four separate hard drives that I will put in SATA AHCI, and then won't even have to do the partition of my hard drive to install ubuntu

---

### Post by oldfred on 2011-12-22
I do not understand your 4 64GB units. It sounds like one of those SSD with RAID built in that you cannot remove.

I have a 64GB SSD and it is just like a 64GB rotating drive except a lot faster.

---

### Post by Attempt on 2011-12-22
I have a 256 SSD but concretely it is a concatenation of four blocks of 64 Go each. This could give me the opportunity of having four hard disks. 

so I have de-RAID the big 256, showing the 4 blocks but have troubles reinstalling windows now. I have not tried Ubuntu yet, I trying it right now

---

### Post by Attempt on 2011-12-22
by the way do you know how to convert RAW to NTFS under DOS?

---

### Post by Attempt on 2011-12-22
solved, no need for NTFS conversion

---


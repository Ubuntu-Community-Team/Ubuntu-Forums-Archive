---
title: "How to clean U3-USB-Stick ?"
date: 2009-11-05
forum: General Help
---

### Post by WanneBeAHippy on 2009-11-05
):P
Hi @ all

Im defacto new at Ubuntu and  i have a really annoying problem.
I can't kill the U3-Launchpad-partition.
My Usb-stick is a 4,1GB cruzer, but there will be mounted only 3,8GB from /dev/sdc1 to /media/disk.

I already made "sudo dd if=/dev/zero of=/dev/sdc" two times.
The issue said that dd wrote zeros on whole 4,1GB.
But after i put it in a Wintrash-pc the U3-Launchpad was reloaded again.

I hope anyone of u can me give a tip, how to eraze/kill/exterminate every single bit of this U3-Launchpad on bit/byte-level.

yours sincerly
WanneBeAHippy

---

### Post by Penguin Guy on 2009-11-05
[GParted]("apt:gparted")?

---

### Post by Mighty_Joe on 2009-11-05
[Sandisk Support: How to remove U3]("http://kb.sandisk.com/app/answers/detail/a_id/2550/kw/usb%20flash%20drive%20remove%20u3/r_id/101834")

---

### Post by WanneBeAHippy on 2009-11-05
I already used gparted for format the fs.
it had no effect too.

Now i tried the scandisk-removal-tool.
stick-space: 3,8GB :mad:

After that i do dd again.
Maybe after that i will get my paid 4,1GB .

I'll post the result.

for now
W...

[COLOR=Blue]EDIT:
Well then, dd+gparted are done.
The issue of dd was 4,1GB written again.
And again, gparted only was able to format 3,81 GB.[/COLOR]

[SIZE=3][COLOR=Red]Lets speak it out:

1.) There is no way to get back the few "strangly lost" hundred MB.
2.) The scandisk-removal-tool only deaktivates the reinstallation of the u3-launchpad onto the visible patition of the stick.
3.) The U3-stick betrays dd/user/owner by preventing the writing onto the memory.[/COLOR][/SIZE] 


thx 4 answers
(surely i have more questions)

WanneBeAHippy

---

### Post by dcstar on 2009-11-05
> **WanneBeAHippy said:**
> 
Im defacto new at Ubuntu and  i have a really annoying problem.
I can't kill the U3-Launchpad-partition.
.........
I hope anyone of u can me give a tip, how to eraze/kill/exterminate every single bit of this U3-Launchpad on bit/byte-level.


Try using the **Device-Create Partition Table** option in gparted.

As well, gparted reports in GiB **NOT** GB - there is a difference.

---

### Post by Mighty_Joe on 2009-11-06
> **WanneBeAHippy said:**
> 
Now i tried the scandisk-removal-tool.
stick-space: 3,8GB :mad:


I have an 8GB Cruzer and successfully removed U3 to restore the drive to full capacity.  Be aware that the process I linked to has three different methods of removal.  I used "METHOD 2 - Download and run the U3 Removal tool.".  After you remove U3, you will have to repartition the drive (creating a new partition table as dcstar will force this) to see the full capacity.

---

### Post by WanneBeAHippy on 2009-11-08
hmm, actual im not at the ubuntu-computer.
i know:
i got gparted version 0.3.5 
there wasnt a menue-point like "**Device>>Create Partition Table**"

Maybe on a newer version, but i havnt any idea, how to update gparted.
All trials fail.
The version stays allways 0.3.5.

I hope u tell me the correct apt-get-command, so that i can follow your steps.


W...

---

### Post by P4man on 2009-11-08
You need a removal tool. dd and parted and all that won't do it because to remove U3 you have to change the FIRMWARE.

Download an U3 removal tool.
This one works for windows:
[http://u3uninstall.s3.amazonaws.com/U3Uninstall.exe](http://u3uninstall.s3.amazonaws.com/U3Uninstall.exe)

I heard there is an alpha or beta available for ubuntu but I dont have the link

edit: btw this irreversible but thats probably a good thing.

---

### Post by P4man on 2009-11-08
Here is one for linux:
[http://zenthought.org/content/project/youthree](http://zenthought.org/content/project/youthree)

By its own admission highly experimental and not updated in over a year so try at your own risk.

---


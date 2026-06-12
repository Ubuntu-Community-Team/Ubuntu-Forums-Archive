---
title: "Cannot adjust partition size? (Newb question)"
date: 2011-05-12
forum: General Help
---

### Post by Shakuras on 2011-05-12
Like I mentioned in the title, this question is probably very newbie-like so I apologize, I'm very very new to Ubuntu.

In previous Ubuntu installations, you were required to manually create partitions in order to dual-boot it alongside another operating system (in my case; Windows 7). In Ubuntu 11.04, you can *apparently* adjust a slider which allocates a chosen amount of memory to the partition. When I was installing Ubuntu 11.04 (64-Bit from a USB flash drive), I did not get this screen/step in the installation. Am I misinterpreting this? Am i still supposed to manually create a partition and THEN be able to use the slider? Again, very newb question, sorry.

Thanks.

---

### Post by lithopsian on 2011-05-12
11.04 does not* require* you to manually create partitions but it does give you the option.  I think it is very easy to miss, but there is a button on the screen that shows you the partitions that will take you to a screen to create your own.

---

### Post by Shakuras on 2011-05-12
> **lithopsian said:**
> 11.04 does not* require* you to manually create partitions but it does give you the option.  I think it is very easy to miss, but there is a button on the screen that shows you the partitions that will take you to a screen to create your own.

Wait, you're not talking about the button in the list of installation choices right? The "Something Else" button? If it's not, I definitely missed it o_O

---

### Post by lithopsian on 2011-05-12
Yes, that's the one.  A cogwheel that says Something else.  Select that and you'll go to some screens that let you define partitions.

Or you can just create the partitions you want using gparted from the Live CD and then do the install.

---

### Post by Quackers on 2011-05-12
The slider option, when available, had a nasty habit of messing up Windows partitions. If you need to shrink a Windows partition it is safer to do it from within Windows.

---

### Post by Shakuras on 2011-05-12
> **Quackers said:**
> The slider option, when available, had a nasty habit of messing up Windows partitions. If you need to shrink a Windows partition it is safer to do it from within Windows.
Hmm, I see.. How come it isn't available for me though? I know you told me to make a seperate partition (with the 'cog' selection in the installation choices), but it honestly just confuses me most of the time, and I've messed up at least 2 times before. I've seen videos before of people using the "Install alongside Windows 7" option and they get the slider, but I don't for some reason.

EDIT: I just realized this thread should probably be in the "Absolute Beginner" section. -_-

---

### Post by Quackers on 2011-05-12
You should be able to use the "alongside" option on 11.04. Isn't it the first option?

---

### Post by Shakuras on 2011-05-12
> **Quackers said:**
> You should be able to use the "alongside" option on 11.04. Isn't it the first option?
Yes, it is, but for some reason, the slider doesn't show up. It goes straight to the installation.

---

### Post by Quackers on 2011-05-12
Do you have un-partitioned space on your hard drive already? Or is it filled with partitions - even if they have free space on them.

---

### Post by Shakuras on 2011-05-12
> **Quackers said:**
> Do you have un-partitioned space on your hard drive already? Or is it filled with partitions - even if they have free space on them.
I only have one partition, which is my Windows 7 installation. I have about 14GB of unallocated space.

---

### Post by Quackers on 2011-05-12
Ok, I assume that you have quit the installer and are now posting from the live desktop?
If so, please go to System > Admin > gparted and post a screenshot of that window.

---

### Post by Shakuras on 2011-05-12
> **Quackers said:**
> Ok, I assume that you have quit the installer and are now posting from the live desktop?
If so, please go to System > Admin > gparted and post a screenshot of that window.
Haha, you guessed right. xD Will do.

---

### Post by Quackers on 2011-05-12
Ok thanks. Do you want to install Ubuntu to that 14GB unallocated space or do you want to create more space for it first?

---

### Post by Shakuras on 2011-05-12
> **Quackers said:**
> Ok thanks. Do you want to install Ubuntu to that 14GB unallocated space or do you want to create more space for it first?
Hmm, I guess I'd rather create more space for it first, unless it's easier to install it and then expand it. Whatever is easier and will have a less chance of screwing up really. Btw, thanks for helping a newbie out :)

---

### Post by Quackers on 2011-05-12
Your setup is not a normal one.
Usually Windows 7 will use at least 2 primary partitions. sda1 for some of its boot files and sda2 for the C: drive partition.
Your Windows 7 installation appears to be on one partition only. If that is the case then it would usually be on sda1 rather than sda2.
Do you know how this came about?

---

### Post by Shakuras on 2011-05-12
Hmm, I think I do. I recall deleting the "recovery" partition by mistake, could this be the partition you're talking about?

Do you need me to take a screenshot in Disk Management in Windows, if that would help you?

---

### Post by Quackers on 2011-05-12
It could be.
Since you did that has Windows still booted up ok?

---

### Post by Shakuras on 2011-05-12
Yeah, perfectly fine actually. How abnormal is this? -_-

---

### Post by Quackers on 2011-05-12
If Windows is booting ok, it's not really a problem, but it does give you a choice to make.
You can install Ubuntu using the "alongside" option which should be fine, but this will only give you a 14GB installation.
Or
You can boot into Windows and defragment the C: drive then in Disk Management you can right-click the C: drive and select "shrink" and then the system will tell you how much you can shrink Windows by. You can change it to less, but not more than it says.
This will give you some more unallocated space at the end of the disc. Ubuntu could then be installed in this empty space but, as a disc can only have one extended partition (and you already have one at sda1) I would recommend that you first delete sda1 and replace it with a new partition of type "primary" using the same space.
This new partition can then be used for whatever you want in the future.
Ubuntu should then be installed to the new unallocated space at the end of the disc, using the "alongside" option (which will probably create a new extended partition by default).

The other option would be to delete sda1 and move your Windows partition to the beginning of the drive. However this would take a long time, I believe, and carries risks.
Or you could wipe the disc and start again with Windows at the start of the drive (probably too drastic though).

---

### Post by Shakuras on 2011-05-12
> **Quackers said:**
> If Windows is booting ok, it's not really a problem, but it does give you a choice to make.
You can install Ubuntu using the "alongside" option which should be fine, but this will only give you a 14GB installation.
Or
You can boot into Windows and defragment the C: drive then in Disk Management you can right-click the C: drive and select "shrink" and then the system will tell you how much you can shrink Windows by. You can change it to less, but not more than it says.
This will give you some more unallocated space at the end of the disc. Ubuntu could then be installed in this empty space but, as a disc can only have one extended partition (and you already have one at sda1) I would recommend that you first delete sda1 and replace it with a new partition of type "primary" using the same space.
This new partition can then be used for whatever you want in the future.
Ubuntu should then be installed to the new unallocated space at the end of the disc, using the "alongside" option (which will probably create a new extended partition by default).

The other option would be to delete sda1 and move your Windows partition to the beginning of the drive. However this would take a long time, I believe, and carries risks.
Or you could wipe the disc and start again with Windows at the start of the drive (probably too drastic though).
Okay, I deleted sda1, and am left with the same 14GB. I basically make a new primary partition (I presume with the default ext2 file system?), then in Windows, I shrink the partition so all the unallocated space is used by Ubuntu, right? Also, it's ok if I just use the initial 14GB for the primary partition right? Then just shrink, let's say, 250GB for Ubuntu?

Edit: Wait, sorry, I'm not even sure if I'm understanding this correctly. It's the 'Primary' partition the one being used for the Ubuntu installation right? So I just shrink my Windows 7 partition, then make a Primary partition with all the unallocated space right?

---

### Post by Quackers on 2011-05-12
You can create another Primary partition in the 14GB space - maybe FAT32 type, as both Ubuntu and Windows could then store files there if you want.
That will be just a spare partition for the moment.
Then DEFRAGMENT Windows C; drive from within Windows.
Then shrink the C: drive with Disk Management screen.
If you shrink C: by 250GB Ubuntu can then be installed to that 250GB using the "alongside option" in the installer.

---

### Post by Shakuras on 2011-05-12
Okay, I created a FAT32 Primary partition with the 14GB space. I'll now go and defragment, then shrink the Windows partition. I'll update you when this is all done! THANK YOU SO MUCH for being so helpful, even though I (think) I'm wasting your time.

---

### Post by Quackers on 2011-05-12
No problem, good luck :-)
Why wasting my time? 
I'll be around for a while yet, but I'll have to sleep some time I suppose :wink: it's 1-40am here.

---

### Post by Shakuras on 2011-05-12
> **Quackers said:**
> No problem, good luck :-)
Why wasting my time? 
I'll be around for a while yet, but I'll have to sleep some time I suppose :wink: it's 1-40am here.
Wowow. It worked PERFECTLY. I now have 2 partitions, one is 242 GB and the other is 8GB; both used by Ubuntu. Seriously, thank you SO SO much, you've saved me a lot of trouble ! :)

---

### Post by Quackers on 2011-05-12
That's good news. Glad things worked out ok :-)

---


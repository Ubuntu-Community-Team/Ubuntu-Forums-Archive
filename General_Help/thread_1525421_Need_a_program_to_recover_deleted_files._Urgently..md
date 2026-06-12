---
title: "Need a program to recover deleted files. Urgently."
date: 2010-07-06
forum: General Help
---

### Post by wilwil0 on 2010-07-06
Deleted a whole bunch of files, I have backed it up but it was from about 2 weeks ago and as I had added loads of stuff in the meantime I urgently need to recover the files.

Ubuntu 9.10. 

Any and every file recovery program you know please. 

Preferably one that allows me to recover an entire directory, not just individual files, but it'll be fine if that is it.

---

### Post by wilwil0 on 2010-07-06
I've downloaded Testdisk via the synaptic but can't find it in any repository, where is it and if it just isn't there how can it be run by commands?

---

### Post by warfacegod on 2010-07-06
I've never needed such software but I see Photorec usually recommended as the best one.

---

### Post by bcbc on 2010-07-06
You need to boot from a live CD - if you're running off the system you want to recover then there's a chance you'll overwrite the deleted files.

+1 on photorec but you don't get directories and/or file names.

It seems testdisk can recover directories so try this first
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2) (I assume the latest testdisk will work for ext4 in the same way)

---

### Post by wilwil0 on 2010-07-06
I downloaded testdisk but I can't find where the launcher is or what the commands are to start it in the terminal?

---

### Post by wilwil0 on 2010-07-06
I have an external drive so I can write them to that right? 

It has a lot of free space, c'mon guys.

---

### Post by wilwil0 on 2010-07-06
Also can Scalpel or photorec recover ODT office files? That's kind fo major for me at the moment....

---

### Post by SoFl W on 2010-07-06
Did you check the trash can?  You do know that downloading and installing other programs has a very good chance of over writing files.

---

### Post by wilwil0 on 2010-07-06
Yes I checked the trash can, deleted it from there by accident, only less than an hour ago though so chances of recovering are fairly high, for now.

urg, I really need to recover those ODT files.

---

### Post by wilwil0 on 2010-07-06
So the first thing I should do is to go onto the try bit of a live cd and install testdisk and that, right?

---

### Post by warfacegod on 2010-07-06
> **wilwil0 said:**
> So the first thing I should do is to go onto the try bit of a live cd and install testdisk and that, right?

Yes. Absolutely. In fact, stop using the computer all together unless you're in a Live Environment.

---

### Post by wilwil0 on 2010-07-06
I'm on a sifferrent computer making a live cd, the one I had I formatted a while ago, does it matter if I use a cd of 10.04 if my Ubuntu system is 9.10?

---

### Post by warfacegod on 2010-07-06
> **wilwil0 said:**
> I'm on a sifferrent computer making a live cd, the one I had I formatted a while ago, does it matter if I use a cd of 10.04 if my Ubuntu system is 9.10?

Not in the least.

---

### Post by wilwil0 on 2010-07-06
Just downloaded 10.04, wrote it to a cd. 

Now on it but whenever I search for "testsisk" on the synaptic I can't find it. 

I've tried Sudo apt-get install testdisk aswell, says it cannot find the package. Yes it is connected to the Internet.

---

### Post by warfacegod on 2010-07-06
Go to: System> Admin.> Software Sources> Other Software tab> enable .../ubuntu lucid partner> Updates tab> enable Unsupported updates (lucid-backports).

Close. Reload. Try getting testdisk again.

You *might* need the ubuntu-restricted-extras package.

---

### Post by wilwil0 on 2010-07-06
Don't know what you said I should enable on the other software tab, but I enabled all of the multivese and universe things as well as the thing you said to do on the Updates tab.

Still doesnt find it.

Where would I get that ubuntu-restricted-extras package? not on synaptic.

Thank you for all the help btw

---

### Post by wilwil0 on 2010-07-06
The update manager says there are over 250MB of updates, would installing them increase the chances of finding it?

One thing is that this crappy disk is only 700MB, meaning the 699MB of Ubuntu 10.04 has it pretty much full up.

I have a 2 or 4GB USB I could launch it from instead, would have to find it though...

---

### Post by wilwil0 on 2010-07-06
Oh wait, its installing from the terminal command, what if it is too big to fit in the disk though?

---

### Post by wilwil0 on 2010-07-06
OK, sonow I have a completely different problem, I have started photorec in the terminal but it only shows the CD disk I'm running from :/

How do I find the hard drive from this?

---

### Post by spydeyrch on 2010-07-06
Here are two links that can help you with what you are needing:


[http://www.howtogeek.com/howto/13706/recover-deleted-files-on-an-ntfs-hard-drive-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/13706/recover-deleted-files-on-an-ntfs-hard-drive-from-a-ubuntu-live-cd/)

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Let me know if they help at all!!!

-Spydey :D

---

### Post by wilwil0 on 2010-07-06
Here's what a screenshot of my problem is if this makes it esier to understand the rpoblem

[http://i45.tinypic.com/1409o9w.png](http://i45.tinypic.com/1409o9w.png)

---

### Post by chalewa on 2010-07-06
are you root?

---

### Post by bcbc on 2010-07-06
at the bottom it says "some disk won't appear unless you are the root user". Did you run it with 'sudo'?

---

### Post by warfacegod on 2010-07-06
> **wilwil0 said:**
> Oh wait, its installing from the terminal command, what if it is too big to fit in the disk though?

Your "Live" isn't going to write anything to the disc its on. It exists in you RAM and that where anything you install will go also.

---

### Post by wilwil0 on 2010-07-06
As I already have testdisk on the disk I am trying to recover stuff from, is there anyway I could use photorec to send the output to a different harddisk? Like an external hard drive?

---

### Post by wilwil0 on 2010-07-06
Aha, the sudo thing worked, I forgot that what root meant.

Just to confirm, I want to chose this option one I've selected here    [http://tinypic.com/r/20jjqlj/6](http://tinypic.com/r/20jjqlj/6)  ) if I want to check the linux partition of my disk.

Oh yeah, where am I posting this output to if not the disk then? What if it is quote large?

---

### Post by chalewa on 2010-07-06
> Finally it asked for a location to store recovered data; I went again with the default, which creates a new directory wherever you have the program installed. And we were off and running; the first file to pop up was a PDF, and since my new directory showed thumbnails by default, I could see that everything was going to be okay. Four minutes later, we were all done; all Vickie had to do was re-create her directory structure, re-name her files, and figure out which belonged where.

looks like further in the process you can specify output location

---

### Post by bcbc on 2010-07-06
You can tell photorec where to place the output on the command line as well.

Mount your external drive e.g. /media/ExternalUSB
Then tell photorec where to recover to with the /d option ... e.g. if your data was on /dev/sda1

```
sudo photorec /d /media/ExternalUSB /dev/sda1
```

---

### Post by chalewa on 2010-07-06
i would scroll through those options at the bottom... carefully... to see if you can specify output. 

and as far as which disc to select... i really don't know, i mean linux seems like a logical choice, but it depends on where the files you are trying to recover sit.

---

### Post by wilwil0 on 2010-07-06
I'm now at this oint, yes I do want to save it to another lace but I'm not sure what to send/click here.

[http://tinypic.com/r/1t38rp/6](http://tinypic.com/r/1t38rp/6)

Sorry if I'm taking eveything in baby steps, one wrong thing and it's lost and I kind of need those files...

---

### Post by wilwil0 on 2010-07-06
> **bcbc said:**
> You can tell photorec where to place the output on the command line as well.

Mount your external drive e.g. /media/ExternalUSB
Then tell photorec where to recover to with the /d option ... e.g. if your data was on /dev/sda1

```
sudo photorec /d /media/ExternalUSB /dev/sda1
```

So should I go back to the very opening command line? I only typed in sudo photorec to start this up

---

### Post by bcbc on 2010-07-06
> **wilwil0 said:**
> So should I go back to the very opening command line? I only typed in sudo photorec to start this up

You can proceed until the point where it asks you where to store them, or you can go back and run it again from the command line. I don't think either takes too much time.

Just make sure you choose a different partition to that of the files you want to recover.

---

### Post by wilwil0 on 2010-07-07
Hmmm, this process says there are no files to recover, what does fdisk do differently to photorec?

---

### Post by wilwil0 on 2010-07-08
Is there any difference?

---

### Post by bcbc on 2010-07-08
> **wilwil0 said:**
> Is there any difference?

they are completely unrelated. photorec recovers data files from your disk regardless of whether they are identified as being there or not. fdisk is a partition table manipulator.

If photorec can't find anything then either the data is not there anymore or you are not using it correctly. Here is a step by step guide:[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 

Did you try the testdisk method to recover deleted directories  I posted earlier?

---

### Post by wilwil0 on 2010-07-08
No, I haven't used testdisk at all so far. 

There's nothing wrong with the partition table.

---

### Post by wilwil0 on 2010-07-08
I'll try to put down as much data about the process I did here:

I typed in the command:

 sudo photorec /d /media/HD-HBU2 /dev/sda5


It said there were many hidden sectors:

Disk /dev/sda5 - 76 GB / 71 GiB (RO) - SAMSUNG HM160HI

Hidden sectors are present.

size       150271947 sectors
user_max   312581808 sectors
native_max 10591920 sectors
dco        312581808 sectors
Device Configuration Overlay (DCO) present.


It's now asking me to select the type of partition table, it started on [none] but I'm fairly certain that this is an Intel, it's a PC not a MAC. Which should I choose? What does a non-partitioned media thing mean?, it says at the bottom they are very rare so  I assume it is wrong and I should select [Intel].

---

### Post by wilwil0 on 2010-07-08
Accodring to the link you posted:

> 
 [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") first - it's usually faster  and TestDisk can retrieved the original file names

What do you mean it can recover directories? 

Is this the link you meant you had posted earlier:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by bcbc on 2010-07-08
> **wilwil0 said:**
> I'll try to put down as much data about the process I did here:

I typed in the command:

 sudo photorec /d /media/HD-HBU2 /dev/sda5


It said there were many hidden sectors:

Disk /dev/sda5 - 76 GB / 71 GiB (RO) - SAMSUNG HM160HI

Hidden sectors are present.

size       150271947 sectors
user_max   312581808 sectors
native_max 10591920 sectors
dco        312581808 sectors
Device Configuration Overlay (DCO) present.


It's now asking me to select the type of partition table, it started on [none] but I'm fairly certain that this is an Intel, it's a PC not a MAC. Which should I choose? What does a non-partitioned media thing mean?, it says at the bottom they are very rare so  I assume it is wrong and I should select [Intel].
/dev/sda5 is a partition - and partitions don't have partition tables. If you had selected the whole disk /dev/sda then it has a partition table and it would have probably defaulted to Intel

---

### Post by bcbc on 2010-07-08
> **wilwil0 said:**
> Accodring to the link you posted:



What do you mean it can recover directories? 

Is this the link you meant you had posted earlier:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2)

---

### Post by wilwil0 on 2010-07-08
The operation just worked and showed literally 10's of thousands of files, but aborted because it said there was now space. This is because it was still trying to save the files to the CD, so I've thought of a sneaky plan and just wanted to see if it would work.

I'm going to use a separate laptop to put ubuntu onto an external hard drive like a USB (can it work like that) and then run the live cd off that. I can then run photorec and the files should simply go onto that.

Any problems with that?

---

### Post by wilwil0 on 2010-07-08
Would I format my external hard drive if I used the startup disk creator  on ubuntu to put ubuntu live cd on it?

---

### Post by bcbc on 2010-07-08
> **wilwil0 said:**
> The operation just worked and showed literally 10's of thousands of files, but aborted because it said there was now space. This is because it was still trying to save the files to the CD, so I've thought of a sneaky plan and just wanted to see if it would work.

I'm going to use a separate laptop to put ubuntu onto an external hard drive like a USB (can it work like that) and then run the live cd off that. I can then run photorec and the files should simply go onto that.

Any problems with that?

Why don't you just mount the external usb from the live cd and then extract the files to it? 

Your plan doesn't make any sense to me - how is it going to access the internal drive on your other computer?

Also, really, try the testdisk option as you can get exactly the file you are after if it works (it's worth a try first). With photorec you'll get a bunch of files called file00001.xxx and you have to figure out what it is and where it's from (only the .xxx will tell you the file type eg .jpg or .doc)

If you have to use photorec, limit it to the file type you are after so you don't have to sift through unnecessary stuff later.

---

### Post by wilwil0 on 2010-07-08
OK, I'll try the testdisk thing first, having a bunch of files that arent called file00001.xxx is a big upside.

---

### Post by wilwil0 on 2010-07-08
testdisk doesn't allow undelete for the partition containing my linux, it doesn't come up as one of the options below, it does for my windows partition however, must be to do with the partition table types or something.

---

### Post by wilwil0 on 2010-07-08
According to this      [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step#Select_where_recovered_files_should_be_written](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step#Select_where_recovered_files_should_be_written)

I should be able to find external drives under a /media or /mnt sub-directory, but there aern't any, just ones one the cd. That's why I want to do it off an external hard disk, so i can store it where there is space as there isn't any on a cd.

---

### Post by wilwil0 on 2010-07-08
OK, don't worry, I didn't realise you could navigate on the menu, it's found lots of files and finding them now, and extracting them to an external hard drive :)

Won't be done for about 12 hours and I'll post if it works, or doesn't but I think it's done.

Thank's for all the help guys!

---

### Post by wilwil0 on 2010-07-08
Well it has worked, thanks a lot!

Did the trick by only allowing one file type, got lots of fun sorting to do now ¬_¬

Cheers again.

---

### Post by jandugacek on 2010-07-12
Try scalpel or foremost. Both can undelete files.

---


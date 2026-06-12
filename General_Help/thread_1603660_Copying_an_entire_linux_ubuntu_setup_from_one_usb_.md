---
title: "Copying an entire linux ubuntu setup from one usb to another!!"
date: 2010-10-23
forum: General Help
---

### Post by freesparks on 2010-10-23
Hello all,

   I have Ubuntu 10.04 (lucid)  installed on an external usb harddrive, and I must say it is extremely efficient.  What is prompting me to basically copy the exact contents of this hard drive onto another brand new one that is connected to my laptop is the fact that I dropped my other one and it hasn't been able to boot, so to avoid ever having to go through this again, I just want to copy and be able to boot from a new hard drive that I purchased that I will basically "mirror" the contents of so I can just be up and running in case I drop a working hard drive again.  Any help on this would be greatly appreciated.  I would love to be able to learn how to this from the command line.  And, if I can't, the person who introduced me to Ubuntu showed me this software that basically copies drives completely onto new hard drives.  

Best Regards,

freesparks

---

### Post by P4man on 2010-10-23
You can do it with 'dd'
Something like

```
dd if=/dev/sd**b** of=/dev/sd**a** bs=512
```

Assuming sda is the internal (new) drive and sdb the usb drive. It also assumes sda is at least as big as sdb, and when its done you will want to resize the partition to fill the entire drive. 

This command will wipe everything from sda, cant be reversed, so use at your own risk. It doesnt produce any output until it finished.

To verify the drive letters sda and sdb or sdc, run this in a terminal

```
sudo fdisk -l
```

Or check in disk utility.

Grub  might need some editing before the new install works, Im not sure if UUIDs get copied over.

---

### Post by matt_symes on 2010-10-23
Hi

You can also you clonezilla to take an image of your hard drive

Kind regards

---

### Post by freesparks on 2010-10-23
Hello All,

Thank you Matt and P4man for the quick replies.  In having read several posts,I did read up on Clonezilla, and it's the grub portion of it that makes me apprehensive about doing it, and to further clarify, it's my current working external usb drive with Ubuntu 10.04 on it that I want to copy the contents of to another brand new external usb hard drive; ---so with that said, the  disk set up would look like this:

/dev/sda = internal hard drive(this is not what i want to copy)

/dev/sdb = this is my current bootable Ubuntu 10.04 (lucid) external usb hard drive that I use that I want to copy to another brand new usb drive..

and lastly:

/dev/sdc =  this is the brand new external usb drive that i want to use in case /dev/sdb ever brakes.

Is this possible, and can someone give me some pitfalls and step by step direction in doing this so I can keep the integrity of GRUB from /dev/sdb and simply copy the same exact characteristics to /dev/sdc.?

Any help on this would be extremely appreciated.

Best Regards,

freesparks

---

### Post by C.S.Cameron on 2010-10-23
I have used dd many times to clone one bootable drive to another

You should be booted from a third drive.

If you are booted from sda:

> sudo dd if=/dev/sdb of=/dev/sdc

If sdb is bootable sdc will also be.

---

### Post by freesparks on 2010-10-23
Hello C.S.Cameron,
 
   This is pretty much my system configuration.  /dev/sda has XP Professional on it and is installed on my internal harddrive.  Again, /dev/sdb is the external usb harddrive that I want to copy to /dev/sdc which is another brand new external usb drive that I want to copy to.  Currently, I'm pretty sure /dev/sdb has to be bootable because in order to boot from it I have to hit F1 and select that external drive from my laptop's bios and then GRUB loads.  So, /dev/sda is not what I want to copy.  Thank yu for your advice.
 
Best Regards,
 
freesparks

---

### Post by bumanie on 2010-10-23
Use the code posted by C.S.Cameron - I am fairly sure the code by P4man would only copy the MBR and partition table, not the entire drive. Just make sure the target drive (in your case /dev/sdc) is equal to or larger then then input device (in your case /dev/sdb).[Here's]("http://kubuntuforums.net/forums/index.php?topic=3090824.0") a good dd command tutorial written for kubuntu

---

### Post by P4man on 2010-10-23
oops, you're right, I shouldnt have put that count=1 in there. But its better to add a blocksize, probably even one bigger than I took, like 1M, otherwise dd will copy one byte at the time and its horribly slow.

---

### Post by C.S.Cameron on 2010-10-23
I am doing the same thing at this moment copying a UNetbootin pendrive install to an EEE using a casper-rw file and home-rw partition.

Use:

> sudo dd if=/dev/sdb of=/dev/sdc

if booted from sda or the Live CD.

I don't specify the bit size.

---

### Post by freesparks on 2010-10-26
It seemed as all was well and it was copying it, but i did get an error at the end.  I know this didn't help much considering I didn't post it, however I'm gathering this occured because the system fell asleep.  Does this matter??  Being that it takes so long to complete there was no way of knowing what caused this.  And, seeing that I did't post the error, I'll probably get no response to this post unless someone had a similar problem!!

Thanks for all the help guys,

Best Regards,

freesparks

---

### Post by freesparks on 2010-10-26
Hello all,

  Well, the error recreated itself quicker than I imagined.  This is what outputted after entering the command:

> mysystem@mysystem:~$ sudo dd if=/dev/sdb of=/dev/sdc
dd: writing to `/dev/sdc': Input/output error
551993+0 records in
551992+0 records out
282619904 bytes (283 MB) copied, 97.0593 s, 2.9 MB/s

Any help on this would be grealty appreciated.  

Best Regards,

freesparks

I guess my next question would be if there is a way to make the command verbose??

---

### Post by P4man on 2010-10-27
Thats not good. Any chance you dont have enough USB power to drive both drives (especially if at least one of them doesnt have its own power brick) ? Can you try other ports and/or powered hub?

You could try this as a test, to see if you can write to the new drive alone:

```
sudo dd if=/dev/zero of=/dev/sdc bs=1MB
```

That will write zero's to sdc. The 1 MB blocksize will make it a LOT faster, 2.9 MB/s you had is going to take forever to copy the entire drive.

I dont think you can make dd more verbose. Im not sure what it could tell you, other than give a block count, since it doesnt copy files or anything, it doesnt verify, it copies block  per block

---

### Post by freesparks on 2010-10-27
Hello P4man,

  Wow, the power of Linux!!  By having, > Any chance you dont have enough USB power to drive both drives  (especially if at least one of them doesnt have its own power brick), do you mean that that /dev/sdc should be powered by its own outlet; because for me that seems very logical considering the one that purchased does have a 5V DC input, but I did not purchase one..  I had no idea that by having multiple drives one could use more power based on the port, I did know about the usb drives having different speeds based on which usb port one uses however.  Well, anyway, I will just have to order one from newegg,  Thank you so much for your help.

Best Regards,

freesparks

---

### Post by freesparks on 2010-10-27
Yup, seems as though you are absolutely right P4man,  these are some of the comments posted on newegg about the drive:
> 
I highly recommend buying a USB cable separately that has two USB ports  to port your drive. Lots of laptop USB ports are the less powerful  (110mA IIRC) variety.> 
Included USB cord only lets you power the enclosure with one USB  connector. If you want to power the drive with two USB connectors you  must buy a separate cable that has two connectors.Now, I suppose its a matter of buying the right cord, or all of them generic.  This is the drive that i purchased.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817155602](http://www.newegg.com/Product/Product.aspx?Item=N82E16817155602)

Thanks for all your help.

Best Regards,

freesparks

---

### Post by P4man on 2010-10-27
Yeah those external drives without power supply are trouble, especially on laptops where the usb ports often dont even provide enough power to meet the usb specs. If you are trying 2 of those, then failure is a given (laptops typically only have one root hub, so all usb devices draw power from it). Even with one drive that came with 2 USB connector (to draw power from 2 ports) I had my share of issues, and it would often fail to spin up.

Im not sure what cable you are looking at, but a cable wont solve it. You to supply the drive with reliable power. A powered usb hub is your best bet if the cable mess isnt a problem.

---

### Post by freesparks on 2010-10-27
Thanks P4man,

 Luckily that particular USB harddrive comes with a 5V DC input in the back of it, so I ordered both the Y cable and the power adapter that comes with it.  i will test both and let you know how it fairs out.  See, i think that's wrong for these computer manufactures to do that. What if it damaged the drive??
Anyway, I thank you so much.

Best Regards,

freesparks

---

### Post by P4man on 2010-10-27
Well, it can work if you have a low power drive and/or an active USB hub. Or even a good motherboard root hub. Keyword being "can". 
500 mA per port is the spec for USB 2.0, and like I said, many  laptop ports dont even get there and many (most?) harddisks require more. Especially fast disks (5400/7200 rpm ones). 

For the heck of it, I just looked up my 500GB 2.5" hitachi travelstar [spec]("http://www.hitachigst.com/tech/techlib.nsf/techdocs/1F70FDFFB4DE1EBB86257538007E4CFE/$file/TS5K500.B_OEM_Specification_R15a.pdf"). It takes 1.7W during seeks, 3W "average from power on to ready" and 4.5W to spin up. At 5V. A USB port will at best deliver 5Vx500mA = 2.5W. And thats not even counting the enclosure's usb to sata controller, which may well take half a watt or more. Problems are a given then.

I doubt it will cause damage though. And that y-cable should do the trick.

---


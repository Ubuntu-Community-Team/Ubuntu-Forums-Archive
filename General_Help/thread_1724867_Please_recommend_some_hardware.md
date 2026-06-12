---
title: "Please recommend some hardware"
date: 2011-04-08
forum: General Help
---

### Post by Bruce Kuhn on 2011-04-08
Hi All,
 
I recently bought a touch screen All-In-One Point-Of-Sale cash register. It is basically a PC running register software. The operating system is running Ubuntu, and know absolutley nothing about Unix based systems or hardware. But, the cash register system is easy to use, and I didn't need to know Unix to use it. But, my store was hit by lightning, and now I need some advice. So, here my two issues:
 
1. Only the ethernet port was taken out by the lightning strike. Everything else works. So, to get the system running again, I figure I could just use a USB to ethernet adapter. I know how to do this on a windows based system, but have no cluse for Unix based. I don't know how to verify if the USB to ethernet adapter will work on this Unix based All-in-one. So, can anyone recommend a brand of adapter that will give me networking through a USB port on this system?
 
2. Because I am worried about other failures on this cash register, I would like to ghost the hard drive, and keep this drive as a backup. This register can only take the 1 drive. So, I would like to plug a external drive enclosure to the POS system, that will let me plug in a spare drive. Then, I will ghost the main drive, and then remove the drive enclosure. Again, I know how to pick external drive enclosures that will work on a windows system, but not for Unix. Can someone please suggest a brand of drive enclosure that will work on a USB port of a Unix based system?
 
Thanks!

---

### Post by Bruce Kuhn on 2011-04-09
Anything?

This question has had 40 views so far, and no replies.

Please understand that I am not asking for help to set up the two items I was asking about. I will do the research to install the drivers, and get everything working. All I ask is for someone to tell me the model number of something YOU have used, that you know works. If you have a TrendNet USB to Ethernet dongle that you know works with Ubuntu, list it. If you have a D-Link DWA-140 USB wireless stick that you know works with Ubuntu, list it as a solution that will work instead of the USB to Ethernet dongle. If you have an external hard drive enclosure that works with Ubuntu, tell me.

It only needs to be a one word reply with a model number, and I will look it up, and install it. I have been to the hardware page of this site to look for a list of accessories, but it seemed geared toward computers. I did not see a way to list USB wireless adapters, or dongles, that I can look at to use.

I will do the research, i would just like to be pointed in the right direction. Any reply is appreciated.

Thanks,
Bruce

---

### Post by Hedgehog1 on 2011-04-09
Greetings Bruce!

Any USB external hard drive works with Ubuntu.  I have had very good success with the Western Digital 'Elements' models of external USB drives.  Just be sure that the external drive is larger than the internal one!

You can leave the USB drive attached to the POS system and even setup a nightly backup to the USB drive (not a bad idea even without any lighting damage).

The free 'Deja Dupe Backup Tool' is a good place to start.

***The Hedge***

:KS

---

### Post by Bruce Kuhn on 2011-04-09
Thanks for the welcome Hedge
 
The POS is running Open Bravo, and it is not storing any sales data on the All-in-one.  It is writing sales data to a server on the nerwork, and that server has a RAID mirror running on it.  So, that takes care of my backup of sales data.  No need for a nightly backup of the POS.
 
The ghost of the POS drive is just so I can get the register up and running on a hard drive failure, which is what fails the most on my systems.  It will then be 1 screw to pop out the drive, and get the machine running again.
 
The lightning strike took out a lot of electronics and computers.  It fried my hub and destroyed all ports connected to the hub.  The full desktops were easy to replace, but not the all-in-one

---

### Post by Hedgehog1 on 2011-04-10
> **Bruce Kuhn said:**
> The POS is running Open Bravo, and it is not storing any sales data on the All-in-one.  It is writing sales data to a server on the nerwork, and that server has a RAID mirror running on it.  So, that takes care of my backup of sales data.  No need for a nightly backup of the POS.

If the goal is a pre-staged hard drive with OS and programs ready to swap in case of emergency, then the best method of copying the All-In-One's hard drive to the external is using the 'dd' or 'ddrescue' commands.  These copy the drive completely, and no matter that the OS is on the source drive, the target drive is a duplicate.

I had some bad sectors on my smaller (640 gig) drive, and used ddresuce to copy the dual-boot (Win7 & Ubuntu) drive to the new 1tb drive. I just unplugged the source drive after the copy, and the system booted perfectly from the target drive.

If you did this ahead of time, you can then be ready when 'lighting strikes twice' :(

***The Hedge***

:KS

---

### Post by SeijiSensei on 2011-04-10
Take a look a [Clonezilla]("http://clonezilla.org/") as a drive-imaging solution.

If you're going to open up the device anyway, maybe you should just install a new network card if it has PCI slots.  [Intel cards]("http://www.newegg.com/Product/Product.aspx?Item=33-106-122") are very well supported.

---

### Post by MrEgg on 2011-04-10
Hi Bruce,

+1 on what The Hedge said - any usb drive will work, and dd is perfect to ghost your system drive.

As for usb-to-ethernet connector, I have a Sitecom LN-013 (that I bought many years ago). It works out of the box, no drivers required. If I were to buy such an adaptor today, I wouldn't worry about compatibility issues (jmho).

Egg

---

### Post by Bruce Kuhn on 2011-04-10
Thanks for the replies.

After searching several forums, I decided to try the Trendnet Tu2-et100 USB to Ethernet adapter. That worked out of the box, and I have network connectivity once again!!! I also bought a drive enclosure when I was at tiger picking the adapter up, but have not connected that yet. I spent last night looking for a ghost program first.

I stumbled on to Clonezilla, and downloaded that. When reading through the install, it said the drive needed to be unmounted to copy, and I needed to boot off a USB drive or stick, it was late, so I called it a night, and was going to try today.

Hedge mentioned 'dd' like it was available at the command prompt. If so, can I just run that without unmounting the drive? Are there any attributes I need to use to run dd? Keep in mind I know nothing about command prompts in Linux. I've been using computers for 30 years, and back before windows even existed ( dos prompts), but have never done anything Linux based.

Thanks for all the help! I'm almost there!

---

### Post by linuxuser12345 on 2011-04-10
I would recommend most Intel products, as Intel "just works". I would, however recommend AMD products if you *know* it works, as you get more bang for your buck.

---

### Post by MrEgg on 2011-04-11
> **Bruce Kuhn said:**
> Hedge mentioned 'dd' like it was available at the command prompt. If so, can I just run that without unmounting the drive?

Yes, you can run dd to copy your drive without unmounting it first. The drive must only be unmounted to *restore* the image.

I'm using dd on a regular basis, and have always been happy with its ability to restore my system as-it-was-before-I-messed-up.

dd will create an image the size of the entire partition, no matter how full or empty it is. If your system is on a 20 GB partition only 1/4 full, it will create a 20 GB image, period.

Because of this, you want to make sure your external HD is formatted with a filesystem that supports such large files. FAT won't do, for example.

This structure of the dd command is like this :
```
dd if=your_input_partition of=your_output_file [options]
```

You want to be careful not getting mixed up between input and output files.

So, lets say your system is on /dev/sda1 and you want to send the image to your external drive which is on /media/HD_drive. The command would be the following :
```
dd if=/dev/sda1 of=/media/HD_Drive/Ubuntu.img bs=4096 conv=notrunc,noerror
```

You can give the image whatever name you like, with whatever extension you like, it doesn't matter. I like to use the .img extension as a personal preference.

dd will take quite some time to complete, as an image the size of the whole partition must go through the usb cable - which is not very fast, even 2.0. dd has no gauge to let you know what percentage has already been completed, which is too bad. You only know it's done when you get the prompt back in Terminal.

Let us know how it goes or if you need more help.

Cheers,
Egg

---

### Post by Bruce Kuhn on 2011-04-11
Thanks for all the help!!
 
I now have my Ethernet port working again (using the dongle), and I have successfully cloned my Hard Drive.
 
I will mark this thread as solved!!

---

### Post by oldsoundguy on 2011-04-11
your point of sale unit is specially designed and modified.  It may be using Linux as it's core, but all the bells and whistles were added by the vendor.  Your best bet  is to call them.

Lowes uses a king sized version of a custom Red Hat install, for instance.  And Red Hat Enterprise division services their software. (for a fee .. how they make their bucks!)

---


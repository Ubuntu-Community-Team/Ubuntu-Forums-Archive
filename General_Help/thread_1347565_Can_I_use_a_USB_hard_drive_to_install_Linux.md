---
title: "Can I use a USB hard drive to install Linux?"
date: 2009-12-06
forum: General Help
---

### Post by roa414 on 2009-12-06
I have to say that the moment I switched from Windows to Linux, I was loving it.  Linux has everything that I need.  The only problem is that I use an SATA hard drive and when I put the live cd in the tray and let it load, it will take me to the desktop.  But when I want to install the real thing, without the livecd, Ubuntu doesn't see my Hard Drive.  I know everything is pluged in, it just doesn't notice my hard drive.  It notices flash drives but not my hard drive.  Therefore, I bought an adapter that let's me connect my hard drive to my computer via USB.  The problem is that I am worried that my adapter will get too hot or get damaged.  Will it?  I am currently using it so that way Ubuntu sees my Hard Drive for installation.  Now, I am using it and I just want to know, can I use a hard drive that's plugged in my USB as my primary hard drive to use?

---

### Post by MelDJ on 2009-12-06
try unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by IllegalCharacter on 2009-12-06
When you boot into the LiveCD, you should be able to run System->Administration->Partition Editor (might be called GParted). Run this and see if it sees your hard drive in there. You might have to manually create the partitions.

---

### Post by sikander3786 on 2009-12-06
How are you using Ubuntu? From a live cd only? Haven't you installed it yet on your HDD?

Ubuntu is very good in detecting SATA HDD so it shouldn't be a problem. You should not use SATA HDD through a USB connector as it will eventually result in decreased speeds.

---

### Post by roa414 on 2009-12-06
Yeah, I already tried using the Partition Editor.  It still doesn't work.  And I am using Ubuntu through my hard drive.  I installed it using the live cd, though.  Will using the USB connector really slow down speeds?  I am just worried that my USB adapter will get too hot and not work or something along those lines.

---

### Post by dcstar on 2009-12-06
> **roa414 said:**
> I have to say that the moment I switched from Windows to Linux, I was loving it.  Linux has everything that I need.  The only problem is that I use an SATA hard drive and when I put the live cd in the tray and let it load, it will take me to the desktop.  But when I want to install the real thing, without the livecd, Ubuntu doesn't see my Hard Drive.  I know everything is pluged in, it just doesn't notice my hard drive.  It notices flash drives but not my hard drive.  Therefore, I bought an adapter that let's me connect my hard drive to my computer via USB.  The problem is that I am worried that my adapter will get too hot or get damaged.  Will it?  I am currently using it so that way Ubuntu sees my Hard Drive for installation.  Now, I am using it and I just want to know, can I use a hard drive that's plugged in my USB as my primary hard drive to use?

Check your BIOS for any special eSATA settings that will allow it to be used as a "normal" bootable drive.

---

### Post by roa414 on 2009-12-07
Thanks for the reply, but I don't have any settings for SATA in my BIOS.  Thanks for the help though.

---

### Post by Marvin666 on 2009-12-07
OS's don't like running on usb disks. I tried to dual boot with server 2003 on a usb disk, and linux on by first one, but during start up, half way through server 2003 crashed. It did this every single time, but not on my internal hard drive.

---

### Post by ranch hand on 2009-12-07
I do not understand exactly what you are asking here.  If you look at  my sig you will see the basic specs of my box.  SATA  is not a problem.

You say Ubuntu doesn't see your HDD yet you are running from the HDD.

How about some info on your box and a discription of how Ubuntu fails to see your drive.

While I have an external dual SATA  enclosure with two 320Gb drives in it that has 8 Linux distros on it, I do not think this is the answer to your problem.

From what you are saying it really sounds like an OS problem that needs worked out.

Another thing that would be a big help is if you would tell us how you installed Ubuntu and what version it is.

The results from this script posted here would be nice to;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It is really for use in diagnosing boot problems but it gives a lot of information on how your box is set up.

---

### Post by blueridgedog on 2009-12-07
While booted on the LiveCD, can you post the output of

```
sudo fdisk -l
```

and 

```
mount
```

Thanks.

You can install to a USB drive, and there are several thread on this forum that will give you instructions.

This is a good one:

[http://ubuntuforums.org/showthread.php?t=1179595](http://ubuntuforums.org/showthread.php?t=1179595)

---

### Post by roa414 on 2009-12-10
Sorry for the slow reply.  But thanks for the replies you guys made.  It's not that SATA is my problem.  It is that my BIOS don't have the right settings.  I don't want to mess up the BIOS so I don't touch them, unless I have given instructions from a website.  And yes, it is reading from the Hard drive.  So this means that it is not the HDD.  When I get to the installation, Ubuntu asks me where to install.  And it shows a blank page.  It shows my flash drives, but not my actual HDD.  I have no clue on why it is doing that.

---

### Post by ranch hand on 2009-12-10
When you boot to your Live CD desktop, are your drives mounted there?

This will cause the partitioner in the installer to not "see" them.  If you right click on them you will see the option to "unmount".  Unmount them and try it again.

---

### Post by Gizenshya on 2009-12-10
Hmmm... yeah, it could be a BIOS problem.  You really shouldn't be worried about your BIOS settings.  You can change whatever as much as you want, and screw it up as much as possible... and you'll always be able to change it right back, and it will be just like before.  The key isn't screwing up-- you will screw up.  The key is writing down original settings, and writing down what you changed, and what you changed it to.

The absolute worst-case scenario is this: You screw up[ settings so bad that the computer resets infinitely, and you can't get into the BIOS to change the settings back.  Fortunately, this is very easy to fix.  There is what is called a "BIOS reset jumper" on the motherboard itself.  Just take off the jumper, wait a few seconds, then put it back.  This resets all BIOS settings automatically. :)

Just don't mess with anything that has to do with "voltage." On some special "overclocking" motherboards, you can change the amount of electricity going to parts of the computer.  On some of those motherboards, you can change the voltage enough to fry (burn) components.  Motherboards that can do this are rare, but just don't change voltages and you'll be fine.  Changing voltages will not fix your problem anyway.

My advice: Write down your BIOS settings.  Then just keep playing and guessing to see if you can find something that works.  It would hours to go over the BIOS capabilities and possibilities for your computer, so just play.  You will get to know your computer more, and you'll find some useful functionality in your BIOS that you might use in the future.

Aside from the BIOS, you can try re-installing (physically) your hard drive.  Sometimes your problem is caused by a loose connection.  I have a Seagate hard drive that has a really loose connector, so I have to take it out and put it back in about once a week.  When I start having it missing when my computer starts up, or when I get incomplete file transfers, I re-seat the connectors and I'm good to go :)

If you do this, turn off your computer, unplug it, and wear an anti-static wrist strap (that is connected to you, and your computer case, or something else that grouds your mobo).  If you don't have an anti-static wrist strap, google how to make one yourself.  They are essential for any time you are massing with your computer's internals.  They are so cheap they are basically free, so there isn't really a reason not to use them.  If you don't, all it takes is one static spark to cost you hundreds :o

Regarding OS's and external USB drives...

Windows sucks at it, to be honest.  There is really no reason for it to (capability-wise).  They just don't want it to work.  There are various reasons, but basaically Microsoft sees USB drives as a threat because they want you to buy a copy of an OS for each and every computer you own, and sometimes more.  USB HDD's would let you use one copy on multiple computers, so they add in their little bugs to stop it.  Linux OS's work great in external USB drives, though.  I have several and I've never had an issue with them.  Windows uses them fine as long as it isn't trying to boot from it.  Windows OS's will run programs from USB drives perfectly fine, though.  Annoyed with not having your favorite program at windows computers?  Just install it on yours, and copy the program folder to a USB drive.  Unless the program calls the registry on startup, then you're set.  ... but that's a bit off-topic. ;)

---

### Post by roa414 on 2009-12-16
thanks for the reply.  Ok, I managed to get to my BIOS and try to find the right settings.  But it's just too complicated.  Is there a certain part I should be looking for in my BIOS that fixes this?

---


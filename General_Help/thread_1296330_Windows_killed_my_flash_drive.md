---
title: "Windows killed my flash drive"
date: 2009-10-20
forum: General Help
---

### Post by NeuB27 on 2009-10-20
I have a usb microSD card reader which I have used for a while and recently windows killed it.

Previously I have used this drive on any ubuntu systems without any problems, just plug and auto-mount as normal. I have also used it on my own XP64 and XP systems which I have set up to NOT automatically do everything that windows normally does.

So when I used this drive at school or on others computers it was no problem as long as I didn't say yes to windows prompt to set up the device correctly (ie, ruin it).

Unfortunately, I gave it to a classmate to present out project (on the drive) to the class on his vista laptop and his computer did something to the drive and was unable to read anything from it.

Now I cannot find the drive on any computer. If anyone can help me I would love to be able to use this again, I would love even more if I were able to get the data off of the drive (if it is still there).

---

### Post by philinux on 2009-10-20
Plug it in and type this in a terminal.

```
lsusb
```

Post back what it says.

---

### Post by badger_fruit on 2009-10-20
> **NeuB27 said:**
> ... on his vista laptop and his computer did something to the drive ...

Oh dear, yes, the wonderful Vista and it's "hey man, you've go to 'fix' this (previously working without a problem) memory stick so it's 'VISTA COMPATIBLE' ... now click here".

What happens if you put this stick into an XP machine? Can it be seen in Start Menu > Right Click on "My Computer" > Manage > Disk Management?

If so, all is not lost, assign it a drive letter (Right-click on the drive > Change Drive Letter and Path ... if nothing shows, click ADD, then choose a drive letter ... if something shows (unlikey) then REMOVE it and ADD a new one) and you're off ... copy the files AT ONCE as a backup then re-format in XP/Ubuntu.

If it does not, then give it back to your friend or another vista owning person and ask them to copy the contents to a CD for you.  Return the memory stick and wipe it under XP/Ubuntu.

Good luck and remember kids ... "VISTA SUCKS".

---

### Post by prshah on 2009-10-20
> **NeuB27 said:**
> 
Unfortunately, I gave it to a classmate to present out project (on the drive) to the class on his vista laptop and his computer did something to the drive and was unable to read anything from it.

Now I cannot find the drive on any computer. If anyone can help me I would love to be able to use this again, I would love even more if I were able to get the data off of the drive (if it is still there).

Huh, he probably set it up to be used as a ReadyBoost drive. If that is infact the case, then I don't think you can recover your data.

However, it is far more likely that he simply unplugged it without using "safely remove". If your card was setup with ntfs, then it will not auto-mount in Ubuntu since the partition will be marked as dirty. In this case, there is a far better chance that your original data is undisturbed.

I suggest you open a terminal (Applications-Accessories-Terminal) and give the command ```
tail -f /var/log/messages
``` Then plug in your drive, wait a few seconds (5-10) and post back the fresh output from the terminal. This will give us a clue as to what is wrong. You can close the terminal after you have pasted the output.

After plugging it in, can you also post the output to the below terminal commands?```
sudo fdisk -l
lsusb # what he (philinux) said
```

---

### Post by CharlesA on 2009-10-20
> **badger_fruit said:**
> 
Good luck and remember kids ... "VISTA SUCKS".

Remember kids, bash Windoze whenever you can!

:popcorn:

Post the result of sudo fdisk -l

---

### Post by NeuB27 on 2009-10-20
First: Thanks for the prompt replies

Now the output, then the answers:

The results of fdisk -l are empty, they only list my hard drive
```
neub@neuLap:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa315a315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4701    37760751   83  Linux
/dev/sda2            4702        4864     1309297+   5  Extended
/dev/sda5            4702        4864     1309266   82  Linux swap / Solaris
neub@neuLap:~$ 

```

The var/log/messages holds the following information
```
neub@neuLap:~$ tail -f /var/log/messages
Oct 20 14:03:23 neuLap kernel: [ 9736.135404] usb 3-3: USB disconnect, address 2
Oct 20 14:03:30 neuLap kernel: [ 9743.444070] usb 3-6: new high speed USB device using ehci_hcd and address 3
Oct 20 14:03:30 neuLap kernel: [ 9743.590083] usb 3-6: configuration #1 chosen from 1 choice
Oct 20 14:03:30 neuLap kernel: [ 9743.595101] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 20 14:03:35 neuLap kernel: [ 9748.602290] scsi 3:0:0:0: Direct-Access     Generic  USB  SD Reader   1.00 PQ: 0 ANSI: 0 CCS
Oct 20 14:03:35 neuLap kernel: [ 9748.623251] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Oct 20 14:03:35 neuLap kernel: [ 9748.624065] sd 3:0:0:0: Attached scsi generic sg2 type 0
Oct 20 14:23:50 neuLap -- MARK --
Oct 20 14:43:50 neuLap -- MARK --
Oct 20 15:03:50 neuLap -- MARK --
^C
neub@neuLap:~$ 


```

And lastly lsusb
```
neub@neuLap:~$ lsusb
Bus 003 Device 003: ID 090c:6200 Feiya Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
neub@neuLap:~$ 

```

Now the answers, my classmate was unable to read any data from the drive, and so I do not think it was an issue where he just pulled out the drive (I've never actually heard first-hand of that going poorly). I cannot say whether or not he did the ready-boost stuff. When I plug the drive in on an XP system nothing shows up, nothing is even listed in the disk manager.

---

### Post by Mark Phelps on 2009-10-20
I wish you the best of luck -- really!!

I had a very similar problem two weeks ago with a USB stick.  Working fine for months then, suddenly, stick it in the machine -- no desktop folder anymore.

lsusb -- nothing.

fdisk -- nothing.

Tried 5 different OSs ( two Linux, three MS Windows) on three different machines -- nothing.

Tried three different data recovery programs, one of which claimed to be able to read devices in RAW mode (even when no filesystem could be recognized) -- nothing.

So, if someone posts details that work for you, I'd be interested in reading them, too.

---

### Post by P4man on 2009-10-20
you say its a card reader.. have you tried it with a different microsd card?
Most likely is that the sdcard is toast (and that it happened while your friend used it is probably coincidence), but it could also be the card reader I guess.

---

### Post by NeuB27 on 2009-10-20
I don't know about the use of another microSD card, I'll see if I can find out.

Does anyone have any suggestion on how to fix the device? Surely the physical hardware wouldn't have been damaged, right?

---

### Post by Mark Phelps on 2009-10-21
> **NeuB27 said:**
> I don't know about the use of another microSD card, I'll see if I can find out.

Does anyone have any suggestion on how to fix the device? Surely the physical hardware wouldn't have been damaged, right?

Following up on my earlier post ... when my USB stick refused to be readable anymore, I did some research and learned that physical damage is apparently quite common.  In the case of a memory card, all it takes is a little static across the leads (as in, walking across a carpet and picking up the card, touching the leads) and the card is toast.

---


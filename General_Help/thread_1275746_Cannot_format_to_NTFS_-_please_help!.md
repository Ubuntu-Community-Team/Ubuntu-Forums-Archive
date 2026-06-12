---
title: "Cannot format to NTFS - please help!"
date: 2009-09-26
forum: General Help
---

### Post by Pipps on 2009-09-26
Intro: I have an 8GB Compact Flash ("CF") drive connected at /dev/sdc .

1. I try to format the drive in the terminal using:

```
mkfs.ntfs /dev/sdc
```

However, I receive the following error message:

> /dev/sdc is entire device, not just one partition
Refusing to make a filesystem here!

2. When I use:

```
fdisk -l
```

I am told:

> Disk /dev/sdc: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

3. GParted recognises the drive. But when I try to create a partition table for the drive in Gparted, GParted hangs. GParted does this repeatedly, every time I try, even after every fresh reboot.

4. What should I do in order to create a partition table for this drive and format it to NTFS? Please help!

---

### Post by ibuclaw on 2009-09-26
What is the output of:
```
sudo fdisk -l
```
Regards
Iain

---

### Post by ibuclaw on 2009-09-26
> **Pipps said:**
> ```
fdisk -l
```
I am told:
> Disk /dev/sdc: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table


Try the following:
```
sudo fdisk /dev/sdc
```

You should see a prompt like so:
> Command (m for help): 
Press the following key sequence:
```

o
w

```
That is, press **o** then **Enter**; then **w** then **Enter**.

And paste any output from the terminal, if it doesn't succeed.

Regards
Iain

---

### Post by Pipps on 2009-09-26
Hi Iain

Thank you for your advice. I did exactly as you instructed. It was unsuccessful. My terminal comprised the following:

> user# ```
sudo fdisk /dev/sdc
```

Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x710c0f33.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 1044.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```
Command (m for help): o
```
Building a new DOS disklabel with disk identifier 0xb140965a.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 1044.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```
Command (m for help): w
```
The partition table has been altered!

Calling ioctl() to re-read partition table.

Error closing file

Was the partition table altered successfully? Is there any way that I can force a closing of the relevant file?

I look forward to your next post.

---

### Post by ibuclaw on 2009-09-26
> **Pipps said:**
> Hi Iain

Thank you for your advice. I did exactly as you instructed. It was unsuccessful. My terminal comprised the following:



Was the partition table altered successfully? Is there any way that I can force a closing of the relevant file?

I look forward to your next post.
There seems to be an error in either syncing changes to the flash card, or closing the drive file.

Try rebooting, and running the above again, just to make sure that no other processes are using the device.

If you get the same message:
1) when did you buy the card?
2) when was it last known to work?

Regards
Iain

---

### Post by Pipps on 2009-09-26
I have now performed a full rebot and attempted the above commands again.

I receive exactly the same error messages in response.

The physical nature of my setup, is the compact flash card, connected to a CF to 2.5" IDE adaptor, which is itself connected to a 2.5" IDE to USB adaptor. This compact flash setup is currently connected to my desktop computer via a front USB port. All power and activity lights on the CF adaptor seem to be in operation.

The card itself was brand new and arrived in the vacuum-formed and sealed plastic retail case.

I would imagine that the chances of a CF card being dead on arrival to be very low. What do you think?

Is it possible that the USB connector, or the IDE to CF adaptor, could present any problems in this situation?

What would you consider to be the most likely 'weak-link' in this chain?

---

### Post by ibuclaw on 2009-09-26
> **Pipps said:**
> I have now performed a full rebot and attempted the above commands again.

I receive exactly the same error messages in response.

The physical nature of my setup, is the compact flash card, connected to a CF to 2.5" IDE adaptor, which is itself connected to a 2.5" IDE to USB adaptor. This compact flash setup is currently connected to my desktop computer via a front USB port. All power and activity lights on the CF adaptor seem to be in operation.

The card itself was brand new and arrived in the vacuum-formed and sealed plastic retail case.

I would imagine that the chances of a CF card being dead on arrival to be very low. What do you think?

Is it possible that the USB connector, or the IDE to CF adaptor, could present any problems in this situation?

What would you consider to be the most likely 'weak-link' in this chain?
Well, to figure that out:

[LIST=1]
[*]Try using the CF card on the same reader, but on another OS (ie: Windows)
This will identify whether it is a Linux fault, or a Physical fault.
If it doesn't work in Windows either, then it is a Physical fault.
[*]Try using the CF in another Machine.
This will identify whether it is a Card fault, or a Reader fault.
If the CF card works on another machine, then it may be the Reader that is faulty.
[*]Try a known working CF Card on the reader
This will confirm that the Reader is indeed faulty.
[/LIST]

Regards
Iain

---

### Post by Pipps on 2009-09-26
I have tried accessing and rewriting the drive in both Windows and Debian. Windows cannot even recognise the drive. Debian sees it, and tries to write a new ext2 partition table to it, but fails to subsequently re-read it. I will try to test the card using another card-reader as soon as I can.

Thank you helping me reach the understanding that it is not a Linux problem.

---

### Post by ibuclaw on 2009-09-26
> **Pipps said:**
> I have tried accessing and rewriting the drive in both Windows and Debian. Windows cannot even recognise the drive. Debian sees it, and tries to write a new ext2 partition table to it, but fails to subsequently re-read it. I will try to test the card using another card-reader as soon as I can.

Thank you helping me reach the understanding that it is not a Linux problem.

In Windows, you would go to **Start -> Run** and type in:
```
compmgmt.msc
```
Then select something named like "**Disk Management**" in the tree view.

Don't look in My Computer, it doesn't tell you anything about drives/etc.

Regards
Iain

---

### Post by Pipps on 2009-09-28
Thank you for this very useful additional advice.

I did exactly as you suggested. Windows XP gave me the following response:
> An unexpected error occurred. Check the System Event Log for more information on the error. Close the Disk Management console, then restart Disk Management or restart the computer.

I checked the system error log, only to see the following:
> System error log: "Unspecified error  (80004005)."

](*,)

---

### Post by ibuclaw on 2009-09-28
> **Pipps said:**
> Thank you for this very useful additional advice.

I did exactly as you suggested. Windows XP gave me the following response:


I checked the system error log, only to see the following:


](*,)

Heh ...


Well, I'm only going off my bad memory here. Try this instead:
Start -> Control Panel -> Administrative -> Disk Management

Are you running Home or Pro? (I only have experience in Pro/Server, so wouldn't know how different Home is).

---

### Post by grturner on 2009-09-28
```
sudo gparted
```
use gparted to do the partitioning for it

---

### Post by wilee-nilee on 2009-09-28
I had some problems with a computer when I shutdown gparted in the middle of it's running, I suspect the hangs you mention have created a similar problem. I don't have any answers for you sorry.

---


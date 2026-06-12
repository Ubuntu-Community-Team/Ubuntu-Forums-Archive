---
title: "broken boot"
date: 2010-01-26
forum: General Help
---

### Post by Jripe on 2010-01-26
On this computer I am using fakeraid with two 500gb hd's. On this I have 3 partitions, 1 is XP, 1 is windows 7, and one is storage. My XP install has been broken for a some time now as I haven't had reason to fix it. I needed to get to it today so I tryed going into the repair console on my XP disk and using the 'fixboot' command. Well, it did nothing except get rid of my windows 7 boot option. Now the only thing I can get to is this ubuntu live cd I have from when I installed ubuntu. My question is how do I get my windows 7 back? Formatting is most definately not an option, I have too many important things right now. Any help would be greatly appreciated, as I am without a computer except for browsing until I get this going again.

---

### Post by rogue_0111 on 2010-01-26
Try this thread:

[http://ubuntuforums.org/showthread.php?t=828862](http://ubuntuforums.org/showthread.php?t=828862)

---

### Post by Jripe on 2010-01-26
The problem there is I tried going through my windows 7 dvd to the repair area, and when I got to where I had to select the OS there was only one there, so I tried to pick but a box popped up saying this version of the recovery tool does not support this version of the operating system. That's the gist of what it said anyways, not exact wording.

---

### Post by djchandler on 2010-01-26
Do you have the Windows 7 install disk?

You can get to the menu and start Startup Repair by using the Windows installation disc. The System Recovery Options menu contains several tools, such as Startup Repair, that can help you recover Windows from a serious error. This set of tools is on your computer's hard disk and on the Windows installation disc.
 
Startup Repair fixes certain problems, such as missing or damaged system files, that might prevent Windows from starting correctly.

There is also an option to rescue your Win 7 by using the upgrade option. Make sure you choose the correct partition. Miscrosoft says this is non-destructive and will preserve your applications, settings and data.

[http://windows.microsoft.com/en-us/windows7/Installing-and-reinstalling-Windows-7#section_7](http://windows.microsoft.com/en-us/windows7/Installing-and-reinstalling-Windows-7#section_7)

Another way to get into your Win 7 is to download the supergrub CD. It should let you boot any healthy partition on the hard drive. There should be two Windows 7 partitions, one of them small, about 100mb, and the other the main volume that normally boots. The smaller 100mb partition contains System Repair as mentioned above, which will let you repair your Win 7 master boot record, and should also let you keep the ability to boot XP. 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Be sure to check supergrub's compatibility against your hardware configuration.

---

### Post by djchandler on 2010-01-26
> **Jripe said:**
> The problem there is I tried going through my windows 7 dvd to the repair area, and when I got to where I had to select the OS there was only one there, so I tried to pick but a box popped up saying this version of the recovery tool does not support this version of the operating system. That's the gist of what it said anyways, not exact wording.

Wow, I think if this was me, I would start thinking about a strategy to rescue my data and reinstall. If you can lay your hands on an external USB hard drive, you can copy the data over to it using the Ubuntu Live CD. I have rescued a friend's data that way before from an unbootable XP installation. Vista or 7 shouldn't be any different unless you have encrypted data. There's a bunch of spare hardware in my basement storage--having spare or replacement hardware is the key to getting a computer rescued.

My guess is the fakeraid isn't supported by the Windows 7 Startup Repair. Can you give us more of an idea what your entire hardware specification is? Did you buy the computer with Win 7 and then retrofit the fakeraid, or was it a custom install by your PC's manufacturer?

See if the supergrub disk will work. The drivers necessary to carry out the repair should be on that smaller partition if it came that way from the manufacturer. Or you may be able to get into the main Win 7 partition and create a system rescue CD there, which should include those drivers for the fakeraid.

---

### Post by Jripe on 2010-01-26
> **djchandler said:**
> Wow, I think if this was me, I would start thinking about a strategy to rescue my data and reinstall. If you can lay your hands on an external USB hard drive, you can copy the data over to it using the Ubuntu Live CD. I have rescued a friend's data that way before with an unbootable XP installation. Vista or 7 shouldn;t be any different unless you have encrypted data. But I also happen to be a nut that has a bunch of spare hardware in my basement storage.

My guess is the fakeraid isn't supported by the Windows 7 Startup Repair. Can you give us more of an idea what your entire hardware specification is? Did you buy the computer with Win 7 and then retrofit the fakeraid, or was it a custom install by your PC's manufacturer?

See if the supergrub disk will work. The drivers necessary to carry out the repair should be on that smaller partition if it came that way from the manufacturer. Or you may be able to get into the main Win 7 partition and create a system rescue CD there, which should include those drivers for the fakeraid.

Yeah I was starting to get scared for a little while here. I'm not sure what I did, I fiddled around in the live CD for a bit and then decided to try the windows 7 boot cd again and when I went to system repair it showed up as having windows 7 instead of a 'Windows Installation'. I followed the other thread using the bootrec command and everything is good now! And the fakeraid is from my mobo, I built my PC myself. This fakeraid is giving me grief, I'm tempted to get rid of it, or buy a real RAID controller.

Anyways, solved (somehow!)

edit: to djc, all windows >= XP can handle fakeraid, and from the research I did for the past couple hours it looks like a couple other linux distro's do too, it sure would be nice if Ubuntu would, it would have a guaranteed spot on my PC if it did.
> The smaller 100mb partition contains System Repair as mentioned above, which will let you repair your Win 7 master boot record, and should also let you keep the ability to boot XP.
My issue with booting XP is not from the bootloader, or mbr, I have a corrupted driver on it that I haven't fixed.

---


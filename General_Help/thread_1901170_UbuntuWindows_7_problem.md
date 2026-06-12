---
title: "Ubuntu/Windows 7 problem"
date: 2011-12-28
forum: General Help
---

### Post by Deltatek on 2011-12-28
Hello everyone! after hours of looking online with no solution I am forced to turn to this community.

So where do I begin, originally we had Debian server installed on a computer I have. After no longer wanting Linux I decided to pop in a windows 7 dvd, which I know works perfectly fine.

For some reason it would not boot the CD, even with the bios settings set properly, and even setting every boot order to the DVD drive. Grub kept booting up anyway. My wife gave me an Ubuntu cd. 10.1 if I remember correctly, thinking I could use Ubuntu to wipe the HD because nothing not even Boot and nuke was loading. Ubuntu worked fine! I was able to delete the Debian installation somehow and install Ubuntu. 

However I still cannot boot up the windows 7 disk. Can someone please walk me through this step by step on how to get Ubuntu off and windows on? Thank you very much!

---

### Post by wolfen69 on 2011-12-28
Is the disk scratched? Will it boot on another machine?

---

### Post by hansdown on 2011-12-28
Welcome to the forum,Deltatek.

You "may" need to reformat the HD, to ntfs first.

---

### Post by Deltatek on 2011-12-28
Thank for replying guys! The disk is not scratched, I keep good care of my disks. I had just used it to wipe my developer machine.

I would love to reformat the disk, but anything I try and do wont work. I tried to use boot and nuke, nothing will load except linux, or another type of linux. Can anyone walk me through getting my hard drive back to ntfs?

---

### Post by Slim Odds on 2011-12-28
Boot with the Ubuntu Live CD

Run gpartd

Delete the old partitions

Create a new NTFS partition

You might need to install ntfs-3g somewhere along the way.

It might be easier to just wipe out the boot sector. Open a terminal window and run this
```
sudo dd if=/dev/null of=/dev/sda bs=512 count=1
```sda might have to be something else depending on your system.

P.S. It's ridiculous that Windows is not smarter about wiping out existing disks.

---

### Post by TroN-0074 on 2011-12-28
If the version of Windows you have is 64BIT is not goint to work in a single core computer.
Make sure you have the right architecture as well.
Good luck to you.

---

### Post by dandnsmith on 2011-12-28
If it appears not to recognise that there is an optical disc present to boot when the Win7 DVD is inserted
a) your optical device reader may not be DVD capable
b) the device may be DVD capable - but the laser for that function has failed (the 2 purposes are different, using different frequencies)

HTH

---

### Post by Deltatek on 2011-12-28
Hey guys. I used the linux CD to turn the hard drive to NTFS and deleted all the old paritions and created then new one. Now when I put the windows cd in I get this "cd rom boot priority 1..00" looked it up on google. No record what so ever.

---

### Post by zero2xiii on 2011-12-29
hay,

Try manualy booting from the CD by hitting either F11 or F12 during start up for the boot device selection dialouge and then selecting the CD/DVD drive.

This sounds more hardware issue than drive/linux issues.

Good luck though.. Don't know why you would want to go back from a debian server to a windows server anyway.

Cherz

---


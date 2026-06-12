---
title: "Help Me - I think I deleted everything!!!"
date: 2012-06-25
forum: General Help
---

### Post by sumpm1 on 2012-06-25
Hey guys. I'm seriously on the verge of tears. I have a spare desktop running Ubuntu Server 10.04 as a NAS. I have the OS installed to and running from a thumb drive, and I am using the attached internal ide hard drive as my storage. I keep all of my stuff on this drive for access from any device in the house....

Well, that hard drive got full while I was accessing it from a windows machine. So I navigated to the ".trash" folder, using windows mind you, and deleted everything in the "files" folder in there. I thought I was just basically emptying the recycle bin for that partition (only one partition on the disk).

And NOW I can't access that drive in any way. I ran a Ubuntu cd install disk and tried to mount that hard drive from gparted and from palimpsest. Both just display that drive as "unknown" as if the partition table was gone.

I am freaking out here. It's not like I just had some downloads on that drive, ALL OF MY FAMILY PICTURES and important stuff are on there!!! That is why I am a freakin mess.

Anyone have a clue wtf I did here? I am already researching TestDisk. What should I be doing first to be the safest?

---

### Post by HermanAB on 2012-06-26
No backup == no data


Buy a new disk drive - larger than old one.  Then copy the whole disk byte for byte to the new one:
# dd if=/dev/sda of=/dev/sdb

Use dmesg, df and ls /dev to confirm the device names - don't get the if and of wrong...

Now you can remove the old drive, replace it with the new one, and work on that.  If you **** it up more, then make another copy and start over.

---

### Post by bcbc on 2012-06-26
The important thing is not to do anything to the disk that could overwrite the data. So booting from the live CD is the correct step.

Testdisk is probably a good bet for recovering the partition table.

It also comes with Photorec which is a time-consuming, but effective way of recovering data. The nice thing about photorec is that it's read only and doesn't even require a valid filesystem to extract data. You'd have to plug in an external drive to recover to. ([http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec))

Here's a link to a recent thread where apparently photorec did the trick... 
[http://ubuntuforums.org/showthread.php?t=2006277](http://ubuntuforums.org/showthread.php?t=2006277)

---

### Post by sumpm1 on 2012-06-27
Alright guys. Thanks so much for the replies. I was freaking out yesterday. Followed your advice. I had another internal hard drive that I was not using the same size as the deleted one; it was a hd I had not used in a while. When I connected this other hd and inspected it, I saw that I had copied all of my family photos onto it about 7 months ago.... So that was a pretty big relief! I have most of my photos.

I did write a new MBR to the broken drive using testdisk, that program is pretty nice. Writing the MBR with testdisk did not recover my files or make them visible; I was hoping I could just undo my mistake and get everything, not so =(

But I cut my losses, and am using photorec to recover the rest of my pics, and any docs I can remember. A pain in the butt... I actually shed tears when I thought it was all gone last night. so manly.

What is the moral of my bs post?

1. Backup your stuff. (This is a reminder to myself =))
2. Careful about deleting from a ".Trash" folder.

I thought the .trash folder was just the recycle bin, guess not; i'll have to research that.

---


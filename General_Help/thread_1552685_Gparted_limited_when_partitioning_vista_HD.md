---
title: "Gparted limited when partitioning vista HD"
date: 2010-08-14
forum: General Help
---

### Post by Gemu on 2010-08-14
Greetings, I have a question someone may help with. Why is it Vista seems to be so off limits to partitioning? I have never seen it where you could not create partitions like  you want until I ran across Vista on a Compaq Presario F 700 Laptop. I finally got The vista partitioning tool too to allow me 12 Gigs but that is it. I seemingly can go no further. I would like to keep Vista on there but take it to the bare minimum HD size, so  I can load other linux OS's. 

 I have 56 gigs of free space after installing ubuntu 9.10 So far I haven't been able to make a swap partition or any other partition for that matter. Is there a way to manipulate Vista partitions?

---

### Post by Gemu on 2010-08-19
No one has a clue on this. This is extremely frustrating to be so limited when partitioning vista. I wonder if I could copy it over to an external USB and then partition my drives like I want?? In fact the installer didn't even give the option to partition the drive. It did give the option to erace Vista and use the entire drive. 

I used the USB installer since I don't have a working CD Drive.

---

### Post by gordintoronto on 2010-08-19
What is the partition setup of the drive? For example, I recently got an HP computer which had FOUR primary partitions on it. Since that is the absolute maximum, I had to remove a partition (well, I actually removed two), make an Extended partition, then make (five, as it turned out) logical partitions within the Extended partition.

Did you attempt to reduce an existing partition?  Did you defrag it first?

---

### Post by Mark Phelps on 2010-08-19
Do NOT use GParted to mess with Vista partitions.  Doing so runs the risk of corrupting the filesystem and rendering Vista unbootable.

Instead, use the Vista builtin Disk Management utility.

And yes, you can use that to make changes to the OS partition.  It will force a reboot and make changes that way.

---

### Post by Herman on 2010-08-19
My recommendation is to run CHKDSK /R on it first to make sure the file system is clean before attempting to resize it with GParted.

After any NTFS partititon has been resized using GParted, a 'dirty' flag will be inserted in the file system to induce another file system check when Windows is booting up.

As with any other partitioning or file system work, you should always make a backup of your files first, and you should be in the habit of doing that regularly anyway.
I have not noticed any particular problems with resizing Vista or NTFS partitions with GParted.

There is the partition editor in the Ubuntu installer, which a lot of people call 'GParted', and there is the standalone, GUI program called GParted in 'System', 'Administration', 'GParted'.

In my website I recommend people to use either, but there is a trick to using the standalone, GUI method.

If you're using stand-alone GParted in the Ubuntu Live CD or some other distro's version of GParted, there is one thing to be careful of.
You need to tell GParted not to 'move' the entire partition because Vista and Windows7 like to start at sector number 2048 instead of sector number 63. If you forget to explicitly tell GParted not to move the entire partition, it will 'helpfully' move it to sector 63 for you, and that will mean a few problems at first with getting it to boot, but nothing that can't usually be easily fixed if you have your Vista CD.

So with GParted, you do this, remove the tick from the checkbox for 'round to cylinders', and you will save yourself a lot of time.
[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]

The Ubuntu installer's inbuilt partitioner doesn't move the Windows partition, so there's nothing to worry about if you use that one, (as opposed to stand-alone GParted, which is a different GUI for the same underlying partitioning program).

If you prefer to use Windows Vista or Windows7's own inbuilt partitioning program, you are welcome to use that.
If you find out that Windows own inbuilt partitioner is not capable of resizing your Windows Vista or Windows7 partition, it might be because the Windows 'page file' is in the way.
Windows uses a thing called a 'page file', in much the same way as Linux uses a swap area (partition).
The page file can easily be disabled and then re-enabled, so that you can shrink your Windows NTFS partition without it interfering.

Here's how to turn off the page file in Windows XP, (and it would be similar for other versions of Windows),
Just turn it off in 'Control Panel' -->'System' --> 'System Properties'-->'Advanced' tab -->'Performance, Settings button' --> 'Advanced' tab, 'Virtual Memory',-->'Change', [COLOR=#ff0000]take note of your settings[/COLOR] (on a piece of paper), and click the radio button for 'no paging file' -->'Set', 'Apply', 'Okay'.

Then you can go back later and do the opposite to turn the page file back on again.

I have also read that the Windows NTFS 'MFT' can stop the resizer from working, but I'm not sure about that, I have never run into that problem personally, but some people say it can be a problem.

It isn't necessary to disable the page file for GParted, only Windows inbuilt partitioner seems to have that disability.
Another thing to watch out for is that Windows should be properly shut  down and not just hibernated, because that would mean the page file  would be occupied.

Regards, Herman :)

---

### Post by Gemu on 2010-08-19
Thanks for the replies folks. 

I did not defrag it. It has a 160 gig hd with a 2nd system restore partition that is 12 gigs and now I have created a 12 gig partition inside the 1st Vista partition with the Vista Partition editor and have installed Ubuntu 9.10 which I have already upgraded to the latest 10.04 LTS and love it. 

 This is my first experience with Vista. The lap top was given to me, left for dead, heavy laden with viruses and wouldn't boot. I finally got it to boot Ubuntu 9.10 on USB from which I scanned the entire computer with Clamav ( Yipee! Finally got to nail some viruses with clamav) and found 14 viruses, removing them enabled me to finally boot Vista, update AVG and find 4 more viruses. 


 It still may have issues possibly with the mother board because I can not always access the bios. When that happens It will not boot until removing the battery, unplugging the power, holding down the power button for thirty seconds and letting it cool a while. Sometimes just letting it cool a while helps.


 I'll try the things you suggest Herman and see what happens. I have found your web site tremendously helpful. I keep a link to it first on my tool bar. I wish I could memorize every thing on there.

---


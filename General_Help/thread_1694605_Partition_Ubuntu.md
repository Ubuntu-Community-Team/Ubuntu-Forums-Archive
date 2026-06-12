---
title: "Partition Ubuntu"
date: 2011-02-24
forum: General Help
---

### Post by Omgpieman on 2011-02-24
Hello.
Well, I'm new here obviously.
But I read one of your topics last night that helped me greatly.
What happened is I deleted a partition of my harddrive that said it was 100% free with absolutely nothing on the partition, but it used 200gig's of my memory, so I deleted it.
Ya, bad idea.
I restarted computer and it went into grub escape.
That is all find, that the easy bit.
I followed the tutorial and it now boots into windows 7 fine.
But now I have the issue, I do want Ubuntu back.

I also don't want it taking up what apparently seemed an empty 200gig drive. A mate of mine said you can just partition a 40gig or less drive, and assign Ubuntu to that?

I also didn't get a CD of it, I got the Ubuntu ISO from the website, put it on a USB and booted of that to install it, but I can't remember how cause it was years ago.

Cheers.

---

### Post by pbw on 2011-02-24
Bootable usb install: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

When installing there is a partition manager, choose advanced and manually select the size of the partition(s).

---

### Post by Omgpieman on 2011-02-24
> **pbw said:**
> Bootable usb install: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

When installing there is a partition manager, choose advanced and manually select the size of the partition(s).

So I download Unetbootin.
And instead of booting of the USB drive, I send to to another partitioned HDD that is like 40 gig (Or less, if I can be less please tell me the minimum :D)

Well, download ISO, use program to assign ISO to the HDD instead of USB.
Then what?
When I restart will it Automatically go into boot options, and select the OS.
Basically I had a good system going last time.
If I got a virus on rare occasion, wouldn't let me run anything, id turn of the computer, turn on, it will give me the option of Windows 7, Memory test, Ubuntu and the old Vista on my PC which changed to windows 7, id use ubuntu to get rid of virus's and ****, and go straight back to windows.

Will that work by doing that?

---

### Post by Omgpieman on 2011-02-25
Anyone?

---

### Post by Omgpieman on 2011-02-27
I would really like an answer to this sorry.
As I don't even know if Ubuntu is even on my computer anymore because I deleted the partition, but it said the partition was 100% available.

I would really like to get Ubuntu back on my computer, but if I already have it installed I would just like to boot off that.
Any help?

---

### Post by sites on 2011-02-27
When installing any linux distro, the best practice is to create three partitions on your drive.  When dual-booting, it's a good idea to give each OS it's own drive if you have enough hard drives in your system.  Here's the way your Ubuntu install should be configured.....

1) swap partition double the size of your system RAM, but no larger than 4GB.

2) root (/) partition for system files, around 10GB should be fine.

3) home (/home) partition for your home directory.

This way, you can re-install Ubuntu as many times as you like. Only format the root partition (ext4). Just set your /home partition to the same file format you used before (ext3 or ext4) without formatting and all of your files & settings will be preserved if you use the same name as your old user account.

This may not help with your present dilemma, but if you follow these instructions it might prevent this from being a problem in the future.

---

### Post by Omgpieman on 2011-02-27
> **sites said:**
> When installing any linux distro, the best practice is to create three partitions on your drive.  When dual-booting, it's a good idea to give each OS it's own drive if you have enough hard drives in your system.  Here's the way your Ubuntu install should be configured.....

1) swap partition double the size of your system RAM, but no larger than 4GB.

2) root (/) partition for system files, around 10GB should be fine.

3) home (/home) partition for your home directory.

This way, you can re-install Ubuntu as many times as you like. Only format the root partition (ext4). Just set your /home partition to the same file format you used before (ext3 or ext4) without formatting and all of your files & settings will be preserved if you use the same name as your old user account.

This may not help with your present dilemma, but if you follow these instructions it might prevent this from being a problem in the future.

Thanks ill take that into account next time.
But I really do need an answer to my question, when I removed the partition did I remove Linux even tho it had 100% free space, and if I make another partition and install Ubuntu onto that using that program, will I have 2 copy's of linux on my computer. Really confused.

---

### Post by sites on 2011-02-27
If YOU don't know what rested on your partitions, or how your disk was partitioned when installing Ubuntu, AND you can't boot into Ubuntu, how are we supposed to know?

Boot into a livecd, use Disk Utility to view your disk and see what formats they have.  If it's not FAT or NTFS then you can be sure it's something for linux.  But in all likelihood, you probably hosed your Ubuntu installation and need to re-install.

Cheers

---

### Post by oldfred on 2011-02-27
I always run this before & after every install to be sure I installed where I wanted to. I always partition in advance.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by yusof125 on 2011-02-27
> **oldfred said:**
> I always run this before & after every install to be sure I installed where I wanted to. I always partition in advance.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
----------------------------------------------

Thanks for guide. 
Before: I'M so lost, try and error.
Now: get lots of new knowledge, new guide and new support.

---


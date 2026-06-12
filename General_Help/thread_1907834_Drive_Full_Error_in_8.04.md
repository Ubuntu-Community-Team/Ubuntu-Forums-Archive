---
title: "Drive Full Error in 8.04"
date: 2012-01-12
forum: General Help
---

### Post by skidave03 on 2012-01-12
Hello, 
 
Total newbie to Ubuntu and Linux (OK, I know a tiny bit about Linux). 
 
My Father-in-law gave me his Dell Mini laptop that is running Ubuntu 8.04. He was having issues with the unit and could not remember his password for me to access anything. I used the recovery disk supplied and re-imaged the system. Everything went well and then I checked for updates. Once the update manager finished checking, I needed 432 :confused: updates. I clicked ok and off it went.
 
I'm obviously on my network, the web browser is running and I was even able to setup my laser printer. So I felt good!
 
Now I am getting an error message saying my drive is 99% full. I looked at the drive info and saw the different folders and yes, the first folder is 99% full. Some other have less and many have none. I apologize, I don't know the proper termininology, but I did do a bunch of web searching and tried a few commands in terminal that I saw about this issue. No luck. I also don't know how to do a screen shot with the software.
 
Any direction on this issue would be appreciated. I plan to use this unit for web browsing and I would like to make sure the space issue is addressed.
 
Thanks in advance,
 
Dave

---

### Post by Topsiho on 2012-01-12
Hello,

First: Ubuntu 8.04 is old, even for an LTS version, so I advise you to install a newer version of Ubuntu: either a newer LTS version, Ubuntu 10.04, or the newest Ubuntu version, which now is Ubuntu 11.10 (year 2011, month October). LTS versions are supported for 3 years, intermediate versions for 18 months. So support for Ubuntu 8.04 has stopped anyway.

You mention a recovery disk, which I presume is a LiveCD, of Ubuntu 8.04, and say "re-imaged" the system. Don't know what you mean with that. The usual thing to do is use a LiveCD (or alternate CD) to install a system completely and cleanly on a computer, if you want next to another operating system (Windows, another Linux), or using all the hard disk for itself. The latter is the most simple thing to do and best for beginners, who install Ubuntu themselves. If you know about partitions, you better do it your own way: a partition for /, a partition for /home, and a swap partition.

Depends on the size of your hard disk:
/ minimum 5GB, better is 10 or even more GB
/swap twice your RAM (working memory, internal memory)
/home the rest of your hard disk. The more the better, as it wil hold all the personal files and configurations of all users of the computer. When you let Ubuntu install itself, then it will not create a separate /home, for which you will be sorry at a next install.

The huge number of updates is what to expect from such an old system, so that is quite "normal".

The rest of your question I can't say anything of. Depends on the size of your hard disk, and of the sizes of your partitions. Only thing is that all those updates have been downloaded and been saved somewhere on the disk, you can remove them with the terminal command:

sudo apt-get clean

You must enter your password, which is the password you entered when installing.

Succes,

Topsiho

---

### Post by skidave03 on 2012-01-12
Thank you for the reply Topsiho.
 
I probably did not use the correct terminology, but I did use the recovery disk that came with the unit to do a complete clean installation.
 
I believe what happened is all of the updates filled the partition.  I'm familiar with partitions in Windows.  If I try to change partitions now, I will probably have issues.
 
I'm not strong with this platform, so updating to a newer version is not for me.
 
I will try running the sudo apt-get clean command in terminal to see if this helps.  I did try something similar last night and got an error back saying command not recognized (or something similar).  I'm kicking myself for not bringing the system to work with me today.
 
Thanks,
 
Dave

---

### Post by gsgleason on 2012-01-12
show me 'df -h' output

---

### Post by Topsiho on 2012-01-12
Hello,

You got that "recovery disk" with the computer from Dell I believe, so it is their nonsensical Windowstalk that was bothering you and me. That means that you used the very first issue of Ubuntu 8.04, now nearly 4 years old, for the install. No wonder you got a huge number of updates. Though: Ubuntu 8.04 is not supported anymore, so now I dó wonder.

If you know partitions in Windows, you know partitions in any other OS, except for the names. To give you a short impression:

/dev/sda1 is the first partition on the first disk
/dev/sda2 is the second partition on the first dis
/dev/sdb1 is the first partition on the second disk

Easy as pi (or pie?)

4 primary partitions allowed (per disk), of which only one may be used as extended partition, which is used as a container for logical partitions (/dev/sda5, /dev/sda6, etc.), and this also applies for /dev/sdb, /dev/sdc etc.)

If you know Partition Magic you can also try gparted, the gnome partition editor, which to me is very similar to PM.
If you partition using PM though you get results which give errors, I think PM treats end of blocks differently. So better (in this case) partition using gparted.

(for the readers of this: if you install alongside Windows, better first create unallocated space within (I mean: by) Windows itself, and only then install Ubuntu (or other) in this unallocated space. Windows can get very nervous if it finds a situation, while booting, it doesn't know of).

Enough for now.

Topsiho

---

### Post by Scott Baker on 2012-01-12
Howdy all, bear with me because I'm going to start with an assumption here. I suspect that the machine in question runs just Ubuntu, based on the information provided. If so, here is a thought. If you have no vital *(irreplaceable)* files on this machine, then start fresh. Grab a copy of Ubuntu 10.04 from the Ubuntu website. Put the provided ISO on a flash drive (flash drives seem to boot faster), then drop the new OS onto your machine. When you install your new OS, make sure that your machines BIOS is set to boot from USB before the hard drive, your comp is plugged into AC power, and plug into ethernet, as opposed to wireless. Once your new OS is loaded, you'll want to run the update manager to install the updates (it will be quite a few. this OS has been out for a couple of years, but is still a great system). And so you know, I've had success installing this on machines with 40gig HDDs and 512m RAM. Make sure to keep us up to date. :popcorn:

---

### Post by Topsiho on 2012-01-12
Sound advice. Plus 1 :)

For Ubuntu a HDD of 40 GB is quite enough, more than quite enough. I run Ubuntu on my Acer Aspire One on a disk of 8 GB (which really is too small, 16 GB would be OK. Depends too on the number and size of your personal files).

512 MB of RAM however is very narrowly enough, and maybe Lubuntu (or Xubuntu) would be better.

Ubuntu 10.04.3 is the newest release of Ubuntu (AFAIK), and not that old yet. You get the newest version automatically when you download Ubuntu 10.04

Topsiho

---

### Post by skidave03 on 2012-01-12
> **gsgleason said:**
> show me 'df -h' output
 
Not sure how to copy and paste the info.  I'll update tonight when I get home.
 
Thanks!

---

### Post by skidave03 on 2012-01-12
> **Scott Baker said:**
> Howdy all, bear with me because I'm going to start with an assumption here. I suspect that the machine in question runs just Ubuntu, based on the information provided. If so, here is a thought. If you have no vital *(irreplaceable)* files on this machine, then start fresh. Grab a copy of Ubuntu 10.04 from the Ubuntu website. Put the provided ISO on a flash drive (flash drives seem to boot faster), then drop the new OS onto your machine. When you install your new OS, make sure that your machines BIOS is set to boot from USB before the hard drive, your comp is plugged into AC power, and plug into ethernet, as opposed to wireless. Once your new OS is loaded, you'll want to run the update manager to install the updates (it will be quite a few. this OS has been out for a couple of years, but is still a great system). And so you know, I've had success installing this on machines with 40gig HDDs and 512m RAM. Make sure to keep us up to date. :popcorn:
 
Thanks Scott.  Yeah, there is nothing on this system and it is Ubuntu only.  I wanted to give it to my wife for web browsing, but I am concerned about the error message that randomly pops up.
 
Topsiho, thanks again for the info.  dev/sda1 is the folder that shows 99% full in the drive analysis.  
 
I thought about getting the newer version of Ubuntu (10.04), but then I am still in an operating system I know little about.  I hate to type this and everyone is going to bite their tongue, but I though about just going to Windows XP and be done (after getting the proper drivers) :(.
 
I do appreciate everyone's help!
 
Dave
 
Dave

---

### Post by snowpine on 2012-01-12
Hi Dave, Welcome to the forums!

First and foremost, if you enjoy using Windows XP, and your wife enjoys Windows XP, then I recommend you gift her a Windows XP computer. If using Ubuntu is scary and aggravating for you, then it is not a good gift for your wife, let's be honest, your father-in-law gave it to you because it was broken and he didn't want it, how will she feel if you turn around and immediately give it to her? ;)

Second Ubuntu 8.04 is dead, it is obsolete abandonware, you are wasting your time. You must use a newer, supported release if you want to use Ubuntu.

Third (and this is most important of all) Dell made several models of Dell Mini. You need to find out which model you have and tell us your system specs, this is very important. Why? Because several models of Dell Mini are **known to be incompatible** with the operating system that shipped with them (4gb SSD too small for updates) and some with current versions of Ubuntu (Intel GMA500 "Poulsbo" graphics). For example mine has a little sticker on the bottom that says "Inspiron 910" and then I can go into System Monitor (Alt-F2, "gnome-system-monitor") to find out how much RAM and hard drive space I have. Please provide us this information so we can give you the best possible advice.

ps If it turns out you do have the exact same 910 model as me with 4gb, then I recommend [Lubuntu ]("http://lubuntu.net/")instead. It is a slimmed-down Ubuntu with a vaguely Windows-XP environment, I think it would be very nice for your wife. :)

---

### Post by skidave03 on 2012-01-12
Snowpine; I think it is the 4 GB model.  I don't have it with me at work, but as I recall looking at the partition info...4 GB sounds correct.  My father-in-law does not have the documentation any longer either.  
 
I took this on as a challenge because I have devices I service at work that use Linux as the operating system...and this is a good way to learn.  I hate seeing electronics go to waste and my F-law was just going to toss it.  I think the updates filled the allocated space and that is where I'm at.
 
I'll post the various information tonight and see where that gets me.
 
Thanks!

---

### Post by snowpine on 2012-01-12
You can buy SSD upgrades (15gb is the recommended minimum for Ubuntu) for the Dell Mini here: [http://www.mydigitaldiscount.com/runcore-pata-mini-pci-e-ssd/](http://www.mydigitaldiscount.com/runcore-pata-mini-pci-e-ssd/)

And here's a great site for how-to's and tips: [http://mydellmini.com/](http://mydellmini.com/)

---

### Post by skidave03 on 2012-01-12
This is a Dell 910.  The system monitor has the following info (summarized) 493MiB, processor 0 is an Intel Atom N270 @ 1..60 GHz, processor 1 is the same.  /dev/sda2 is 3.5G with 2.8 used and gvfs-fuse-daemon is 3.5G with 2.8 used.

The disk usage analyzer shows folder "/" is 2.7G at 100% capacity and 20 items.  Folder "usr"is 2.1G with 78% capacity and 9 items.

Here are the results from df-h

angiedavid@angiedavid:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.5G  2.8G  522M  85% /
varrun                247M  100K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M   36K  247M   1% /dev
devshm                247M   56K  247M   1% /dev/shm
lrm                   247M  1.7M  246M   1% /lib/modules/2.6.24-29-lpia/volatile
overflow              1.0M   16K 1008K   2% /tmp
gvfs-fuse-daemon      3.5G  2.8G  522M  85%

Also, I did run the sudo get-apt clean command.

Thanks!

Dave

---

### Post by Penguinnerd on 2012-01-12
I think, by far, the easiest thing to do now would be to download the lubuntu 11.10 file from online, write it to a flash drive, and install it from that.

You can get lubuntu at: 
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

The procedure to write an image to a flash drive using windows can be found here:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Good luck! :)

---


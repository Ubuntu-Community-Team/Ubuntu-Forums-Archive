---
title: "Virus"
date: 2010-09-04
forum: General Help
---

### Post by cmscott2 on 2010-09-04
Hello, 
I have a friend whos laptop has a virus on it... her virus protection has expired and she received a virus.... everytime she turns on her laptop... a bunch of websites keep popping up... of course me being an ubuntu user always picks on her and keeps telling her to switch over and now i can rub it in her face more :) however, its her computer and she is reluctant to do so... 

I told her I would help her as much as I can.... she has windows vista.... yeah i know.. poor girl.... anyways.... does anyone have any ideas for this? and perhaps if I can fix this I can get her to come to the light side :)

Thank you!!

Christina

---

### Post by terry_gardener on 2010-09-04
you could try and download a free virus protection program and then do full scans (atleast a couple to make sure the virus is gone) 
then use something like ccleaner to clean the computer.

---

### Post by Artemis Fowl on 2010-09-04
Maybe install AVG free edition or something on a USB and rename it something like ""123".
I've seen it work, but I've also seen it fail.

---

### Post by cmscott2 on 2010-09-04
Thats what I was going to do but with all the popups... it becomes damn near impossible to download anything to that computer... I was thinking of burning an iso of a program and seeing if I could install it... its seeming pretty impossible... ill give it a whirl though and see what happens :)

---

### Post by Artemis Fowl on 2010-09-04
This may be what you mean and I read your post wrong, and I'm not even sure if you can do this, but maybe install ubuntu via livecd and run ClamTK? I read somewhere you can use linux to remove Windows viruses, but I'm not sure.

---

### Post by WorMzy on 2010-09-04
You could boot into a LiveCD of Ubuntu, mount her Windows partition, and run clamav on it. Run it with the correct arguments and it'll (hopefully) remove all infected files from the partition.

Something like
```
clamscan -r -i --move=/home/ubuntu/infected /media/windows
```
should do the trick. You'll need to create the infected folder though, or else the scan will fail.

---

### Post by howefield on 2010-09-04
Create a live USB stick with Startup Disk Creator (setting some reserved extra space so you can install applications to it and have them stick) and install anti virus on it, boot the infected computer and cleaning will be easier as the windows disk will not be in use.

I'd recommend Bitdefender for Unices.

Alternatively, load the infected computer up in safe mode with networking, install Malwarebytes and scan.

My money is on it not being a virus as such but rather another form of malware.

---

### Post by Artemis Fowl on 2010-09-04
> **howefield said:**
> Create a live USB stick with Startup Disk Creator (setting some reserved extra space so you can install applications to it and have them stick) and install anti virus on it, boot the infected computer and cleaning will be easier as the windows disk will not be in use.

I'd recommend Bitdefender for Unices.

Alternatively, load the infected computer up in safe mode with networking, install Malwarebytes and scan.

My money is on it not being a virus as such but rather another form of malware.

Technically, you're probably right, it's most likely not a virus, but do not forget that "virus" is also a term that applies to all malware.

---

### Post by jmszr on 2010-09-04
cmscott2,

Here is the link to the AVG Rescue CD: [http://www.avg.com/us-en/avg-rescue-cd#tba1](http://www.avg.com/us-en/avg-rescue-cd#tba1) .

---

### Post by Rubi1200 on 2010-09-04
Here is a link to a bunch of rescue cd's:
[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)

---

### Post by cmscott2 on 2010-09-04
i GOT IT!!! THANKS!!! :)

---

### Post by howefield on 2010-09-04
> **Artemis Fowl said:**
> ...but do not forget that "virus" is also a term that applies to all malware.

Rubbish.

You really think that all malware can correctly be termed as a virus ?

You are free to call malware anything you like, but unfortunately, that doesn't make you accurate.

---

### Post by Chris1274 on 2010-09-04
> **howefield said:**
> Rubbish.

You really think that all malware can correctly be termed as a virus ?

You are free to call malware anything you like, but unfortunately, that doesn't make you accurate.

I think his point was that 'virus' is very often used, whether correctly or not (and particularly by non-specialists), to refer to any form of malware, not just to genuine viruses.

*Nomines significant ad placitum*.

---

### Post by Yoshi-Tron on 2010-10-01
I just installed Ubuntu on my laptop (completely new to Linux, i have my first book on the way), partitioned my hard drive so i can keep vista. I did not really find anything that answered my question, (as far as other threads go) and did not want to start a new one as this thread is close. I can't run antivirus clean sweeps because my laptop overheats and shuts off, Linux is not as strenuous on the system as windows. Is there a way to run an anti-virus program through Ubuntu to scan and possibly clean any infected window files?


and a random question; i have 10.04, but I'm not sure of any version type. Where can i locate that information?

---

### Post by SeijiSensei on 2010-10-01
If you mount the Windows partition under Linux, you can install ClamAV from the repositories ("sudo apt-get install clamav" is the quickest method), then run "clamscan /path/to/the/windows/partition" and see what it turns up.

Your Windows partition may already be mounted at /dos or /windows by the installer.  Type "df" at a prompt (no sudo needed) and see if you find an entry that looks like this:

```

/dev/sda1             20000888  15053584   4947304  76% /windows

```

If it's not already mounted, then follow these steps from a Terminal prompt:

sudo mkdir /mnt/windows
sudo mount /dev/sda1 /mnt/windows

Replace sda1 with the partition that contains Windows.  Usually it's the first partition ("1") on the primary drive ("a") thus denoted as /dev/sda1.  If you're not sure where it's located, you can run "sudo fdisk /dev/sda" then type the "p" command to list the partitions. You should see an entry like this:

```

/dev/sda1   *           1        2490    20000893+   7  HPFS/NTFS

```

You're looking for the HPFS/NTFS partition.  Type "q" to exit fdisk.

---


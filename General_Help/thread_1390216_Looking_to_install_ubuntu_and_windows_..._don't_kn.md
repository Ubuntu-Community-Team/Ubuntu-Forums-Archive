---
title: "Looking to install ubuntu and windows ... don't know my partition number"
date: 2010-01-25
forum: General Help
---

### Post by cscott5288 on 2010-01-25
Hi,

Ok so I have a Ubuntu on one partition and a FAT32 partition set aside for Vista. I know that vista uses NTFS, so I am assuming the windows install will reformat that partition if I choose it for the install? I wasn't given a disc by the manufacturer and I am using a different hard drive from the one that was originally in that laptop (the old one failed). So I found a 32 bit Vista recovery download here: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) I have the pin number so I think that's all I need. 

Another question I have is how do I determine the hard drive and partition number? I need this information because I chose to use the "Recovering GRUB after reinstalling Windows" that is described on [this ubuntu support]("https://help.ubuntu.com/community/WindowsDualBoot") page. 

Aside from that is there anything else I should no before performing this operation? Can I use a Ubuntu 9.04 live disk to recover GRUB even though I have 9.10?

Thanks ahead!

---

### Post by HermanAB on 2010-01-25
How?  Hmmm... You use a combination of 'mount', 'df' and 'ls /dev/sd*' and 'fdisk /dev/sda' 'p', until you are sure what is going on.  This is not something you would want to get wrong!

---

### Post by cscott5288 on 2010-01-25
> **HermanAB said:**
> How?  Hmmm... You use a combination of 'mount', 'df' and 'ls /dev/sd*' and 'fdisk /dev/sda' 'p', until you are sure what is going on.  This is not something you would want to get wrong!
I am sorry, I have absolutely no idea what that means. :confused:

---

### Post by cscott5288 on 2010-01-25
Just a little bump :D.

---

### Post by cscott5288 on 2010-01-25
eh? nobody has any advice for me?

---

### Post by oldfred on 2010-01-25
The neosmart download is not an install disk but just has the files required to do a repair of a failed windows. It is good for repairing windows where the MBR is overwritten and you want to recover it. Or to replace missing boot files where you had two windows installs that were combined and deleted some essential files from the first install and now the second does not work. It will not let you install windows.

---

### Post by cscott5288 on 2010-01-25
> **oldfred said:**
> The neosmart download is not an install disk but just has the files required to do a repair of a failed windows. It is good for repairing windows where the MBR is overwritten and you want to recover it. Or to replace missing boot files where you had two windows installs that were combined and deleted some essential files from the first install and now the second does not work. It will not let you install windows.
Oh, Shucks. That sucks. What about the thousands of people that bought PCs that only had a recovery on a separate partition (EVERY single PC now) and the entire hard drive failed? Did they all go out and buy new operating systems or did they get charged $25 from the manufacturer to  ship the recovery disks out?

Is there anyway I can avoid paying $25 for the recovery disks? Yeah, it's not a joke, that is what HP is asking to ship out recovery disks.. things that cost them 2 cents to make. When I asked the support guy on the phone why I had to pay that, he basically said because I wasn't smart enough to make a DVD backup of the partition ... as if half the people who buy PCs even know what a partition is. 

Is there any place where I can download the operating system? I have the serial number, I purchased the software once, why do I have to purchase it again? I am very pissed off at this whole thing. I would stick with only Ubuntu (I love it, much more than windows) but there are some things you just need windows for. Games and .NET programming for example.

---


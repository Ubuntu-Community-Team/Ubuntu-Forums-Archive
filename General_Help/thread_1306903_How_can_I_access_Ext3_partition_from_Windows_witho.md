---
title: "How can I access Ext3 partition from Windows without rebooting"
date: 2009-10-30
forum: General Help
---

### Post by alex sun on 2009-10-30
Hi,
Sorry if this thread is in incorrect place, but I've found Windows sub forum to be closed for new posts.
Could you please help me to access ext3 partition from Windows without rebooting?
It is actually a long story. I have a problem with my motherboard. It caused my computer to remain dead for half a year, after which the machine magically started again. I decided to load Windows instead of Ubuntu, because in Linux I couldn't access the Internet properly (the only available Internet provider here distributes Windows executables, which have to be run to get full-featured Internet access). After loading Windows I decided to take a risk and install updates. Then I rebooted the computer and had to power it off and on about 200 times before it started. I don't want to ever reboot it again. But I have some valuable information on my ext3 partition.
Some discussions about EXT2IFS and DiskInternals Linux Reader indicate that the system has to be rebooted to use them. Are there any ways to access ext3 from Windows without reboot?
Thank you in advance for any help.

---

### Post by coffeecat on 2009-10-30
First, any 3rd party ext3 driver for Windows, such a [fs-driver]("http://www.fs-driver.org/") will require Windows to be rebooted before it will work. That's just the nature of Windows. Sorry.

Second, you've clearly got a major hardware problem with that machine. It could be the motherboard. It might be a failing hard drive, in which case you need to get that data off pronto. Or it could be the PSU failing, or a lot of other things. Whichever it is, you need to think seriously about using another machine to get at the data reliably.

I suggest you take out the hard drive and put it in a USB enclosure - if you can get hold of one. Then you will be able to plug it into another computer - if you can get access to one. Then you have a choice. Either install fs-driver to a Windows machine. Or run an Ubuntu cd live. You can do everything you need (albeit slowly) from a live CD without needing to touch the internal HD of the machine you are using. This would be a better option because Ubuntu will read ext 3 natively. You could then plug another USB drive or flash drive into the machine and copy your important files from the ext3 partition to the other drive.

There's only one slight complication with using the Ubuntu live CD. The filesystem ext3 supports Unix-type permissions (different from Windows) so that you may get permissions problems as a live user trying to access your own files on the ext3 partition. If you do, simply open a Nautilus file browser window with administrator privileges from a terminal with "gksudo nautilus" and you'll then be OK. So long as you copy **to** a drive with a Windows filesystem (NTFS or FAT) you won't have any further permissions problems.

Last thought - you mention your ISP, internet access and Windows executables. There's often a way around such nonsense. When and if you feel ready to try to get full internet access from Linux, start a thread posting details of your ISP, your country, your modem, router, computer and anything else relevant, and someone might be able to help you.

---

### Post by alex sun on 2009-10-30
2 coffeecat: thank you very much for so detailed answer.
In my case I'm almost sure that the problem is with the motherboard, more particular with the north bridge - it has been reported hundreds of times for these notebooks. Unfortunately, my warranty has already expired.
As for removing the hard drive, for now I would rather have a working computer with incomplete data, than fully available hard drive and no computer :)
As soon as my computer finally dies, I'll do exactly what you advised - remove the hard drive, buy another machine and try resolving the situation with my Internet provider and Linux.

2 ALL: By the way, I have found something interesting. As I understand, [Explore2fs]("http://www.chrysocome.net/explore2fs") does not require rebooting to read ext3. Unfortunately, it seems not to work under my Vista Home Premium. Does anyone know something like Explore2fs working under Vista? Or are there any ideas how to run Explore2fs under Vista Home edition? It shows nothing when I try to run it as it is. When I run it in Win2000 compatibility mode with additional administrator privileges, it detects hda9 with 0 data.

I would very much appreciate any help.

---

### Post by alex sun on 2009-10-30
update:
1. [Explore2fs ]("http://www.chrysocome.net/explore2fs") and [Virtual-Volumes]("http://virtual-volumes.software.informer.com/") still do not work under any conditions.
2. I was able to run [DiskInternals Linux Reader]("http://www.diskinternals.com/linux-reader/") without reboot. It gave me access to Linux SWAP partition, and I was able to get full information (i.e. size, type, number of clusters etc) about my main Ubuntu partition. The data remains inaccessible.

Thank you in advance for any help on the topic.

---


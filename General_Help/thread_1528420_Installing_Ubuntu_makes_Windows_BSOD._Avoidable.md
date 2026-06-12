---
title: "Installing Ubuntu makes Windows BSOD. Avoidable?"
date: 2010-07-10
forum: General Help
---

### Post by fiddler616 on 2010-07-10
Hello,

Last month, I agreed to install Ubuntu on my sisters Toshiba NB 305. Ubuntu was fine, but somehow installing it and GRUB hosed both the XP partition and the recovery partition. The Windows splash screen would appear for a second or too, and then Windows BSOD'ed.

I managed to coax the recovery partition into resetting the netbook, and told my sister to be happy with XP for the moment because I had to study for exams.

But she still wants her Linux. So I was wondering if there was a way to ensure that the installation would be OK.

I've found several threads of people with the same problem, but nobody's posted a solution yet :(

Thanks in advance.

---

### Post by oldfred on 2010-07-10
Both my desktop with multiple drives and my 3 yr old Toshiba dual boot XP and Ubuntu without any issues. 

Did you by any chance install grub to the windows partitions? That seems to be the one largest problem we see. 

I do like setting up partitions in advance and using manual install to have better control over sizes and be able to create a separate /home. When you set up partitions in advance you can also boot windows to make sure it is ok with its new smaller size, it usually wants to run chkdsk. Just be sure to leave 20% free space or windows will slow down or stop working.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)
Alternate install example win 10.04:
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

---

### Post by fiddler616 on 2010-07-10
I've dualbooted successfully on a good 15 or so installations on 7+ machines. It's just that this one throws a fit.

IIRC, for the Toshiba I shrunk the NTFS partition by 20GB or so (I think it was 80% free after that), then used the 20GB to make a 1GB swap and a 19GB ext4 partition, on which I mounted /.

If you really think it'd be a good idea to boot gparted first and shrink the partition before installing Ubuntu, I'll try that though. And this time I'm partimage-ing the drive before any shenanigans ensue :P

---

### Post by WorMzy on 2010-07-10
I can't see any reason for Windows to become unbootable due to the installation of Ubuntu and grub, so I have to assume that resizing the partition damaged some of the files necessary for Windows to boot. So how did you resize the NTFS partition?

I'd recommend that you do it via the native Windows partitioner, and defragment extensively beforehand; don't use gparted unless you have no other choice. If something goes wrong with Windows post-partition editing, then try running chkdsk, or boot the recovery CD and repair the install.

If you still don't have any luck, then leave Ubuntu as it is, reformat the NTFS partition, and reinstall windows to it; then boot the Ubuntu LiveCD and reinstall grub to the MBR.

---

### Post by fiddler616 on 2010-07-11
@WorMzy XP's partitioner doesn't support shrinking partitions. But I defragmented and used gparted to nick off 20GB from the end, then I rebooted, checked Windows (it was fine), and installed Ubuntu (Crunchbang, if you want to be specific). And everything's fine. Thanks!

---

### Post by WorMzy on 2010-07-11
Glad to hear it. Happy to help. :)

---


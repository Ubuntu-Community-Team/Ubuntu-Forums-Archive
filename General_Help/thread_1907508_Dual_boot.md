---
title: "Dual boot"
date: 2012-01-11
forum: General Help
---

### Post by Aleksandar222 on 2012-01-11
I have windows 7 32 bit currently installed on my computer.
I have only one partition (C) and ubuntu installer does not provide an option "install alongside your currrent os" so
I went to manual editing but stopped there because I was afraid not to mess something.
Then I rebooted into windows and when trying to create a new partition I got an error about the volume being corrupted.
So I cannot create new partitions,until I run chkdsk,which I once ran and it messed up windows explorer so I had to system restore from the safe mode.
Anyway,I do not want to do chkdsk but I want a new partition for ubuntu.Any help would be appreciated.

A side note : I had linux mint installed before and i deleted it with partition manager and EasyBCD for the MBR part.I suspect that that is the thing that causes ubuntu installer not to offer me install alongside your current OS option.The installer is for ubuntu 10.10.

Maybe this is the answer to my question : [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

If it solves my problem I will mark this thread as solved from ubuntu.

This link did not help me.The only options I have are change,revert and delete.I will try tommorow what cryptotheslow said.

---

### Post by bluexrider on 2012-01-11
> **Aleksandar222 said:**
> I have windows 7 32 bit currently installed on my computer.
I have only one partition (C) and ubuntu installer does not provide an option "install alongside your currrent os" so
I went to manual editing but stopped there because I was afraid not to mess something.
Then I rebooted into windows and when trying to create a new partition I got an error about the volume being corrupted.
So I cannot create new partitions,until I run chkdsk,which I once ran and it messed up windows explorer so I had to system restore from the safe mode.
Anyway,I do not want to do chkdsk but I want a new partition for ubuntu.Any help would be appreciated.

A side note : I had linux mint installed before and i deleted it with partition manager and EasyBCD for the MBR part.I suspect that that is the thing that causes ubuntu installer not to offer me install alongside your current OS option.The installer is for ubuntu 10.10.

Follow the information in my signature :KS Windows Dual Boot

---

### Post by Aleksandar222 on 2012-01-11
> **bluexrider said:**
> Follow the information in my signature :KS Windows Dual Boot
I have read that already but that says 
"Listed will be your current partitions."
I only have one partition and I have said why I cannot have more.

---

### Post by mörgæs on 2012-01-11
Changed the title to a more informative one.

---

### Post by cryptotheslow on 2012-01-11
With a Windows 7 install it is recommended to only resize the Windows partition(s) with it's own tools (Disk Management) before you install linux alongside - rather than letting the installer do it.

Now your Windows 7 partition is marked as corrupt I am sure Disk Management will refuse to resize it - which is very sane as it is unsure where it's contents actually reside.

My advice would be:
1. Create Windows 7 System Recovery disc (if you don't already have one)
2. Make a Windows 7 system image backup (hopefully you have an external drive big enough to do this too - doing it to DVD+r discs is tedious!)
3. Run chkdsk and let it sort out the Win partition (finger's crossed)
4. Resize Win partition using Windows Disk Management - then reboot into Windows 2 or 3 times to be sure all is well.
5. Proceed with your Ubuntu install into the now empty space on the drive.

---


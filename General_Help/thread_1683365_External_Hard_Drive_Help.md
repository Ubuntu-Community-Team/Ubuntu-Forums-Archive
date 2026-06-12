---
title: "External Hard Drive Help"
date: 2011-02-07
forum: General Help
---

### Post by Devan1337 on 2011-02-07
OK so I admit a lot of the time I have no idea what I'm doing. So I had this corrupted external hdd and so I formatted the main partition on it on windows but messed up in the formatting and ended up having to format the entire thing. I got some weird message about it not being initialized (no not mounted) so I was in compmgmt.msc in windows and right clicked it in device manager and it asked for master boot or GUID I selected the latter and formatted. Worked fine and all for a bit but now it doesn't show up as a drive. I noticed when using compmgmt.msc it showed up that it had installed driver software and was being recognized but in the partition editing area there was nothing on this drive, reinstalling driver software doesn't seem to help. Also GParted wont load up when I have it plugged in and Disk Utility doesn't show it. I am requesting help to fix this problem within Ubuntu 10.10 somehow so I can use it properly.

edit:
Thought I should mention it is a WD

---

### Post by Devan1337 on 2011-02-07
If nobody can provide me help on this topic can somebody tell me where I can?

---

### Post by simonmoon42 on 2011-02-07
Maybe it's just me... but I'm having a hard time understanding exactly what you're trying accomplish. If I understand you correctly, you have an external HDD that's not being detected in 10.10? 

What kind of HDD is it? USB, Firewire, eSata?
What is your ultimate goal? For it to work in Windows or Linux or both?
When you run lshw is it listed?

---

### Post by Devan1337 on 2011-02-07
> **simonmoon42 said:**
> Maybe it's just me... but I'm having a hard time understanding exactly what you're trying accomplish. If I understand you correctly, you have an external HDD that's not being detected in 10.10? 

What kind of HDD is it? USB, Firewire, eSata?
What is your ultimate goal? For it to work in Windows or Linux or both?
When you run lshw is it listed?

I'm sorry I should have been more specific it is USB and yes it doesn't work in either OS now. I am looking for a solution that will fix it on either or both. And lshw... I just put that in the terminal correct?

---

### Post by simonmoon42 on 2011-02-07
> **Devan1337 said:**
> I'm sorry I should have been more specific it is USB and yes it doesn't work in either OS now. I am looking for a solution that will fix it on either or both. And lshw... I just put that in the terminal correct?

That is correct, enter lshw in the terminal and post the results.

---

### Post by clhsharky on 2011-02-07
```
lsusb
```
for USB devices

Sharky

---

### Post by Devan1337 on 2011-02-07
Yep shows up but I can't use it. Like on windows it showed up as a device but nothing about it showed up for storage.

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

This is getting really frustrating I can't seem to find out how to access it on either operating system

---

### Post by Devan1337 on 2011-02-07
Is there a way to use terminal to reformat it or something. None of the GUI disk utility things seem to show it but that last command at least knew it was there.

---

### Post by Devan1337 on 2011-02-07
Sorry for the multiple posts but I'm still at a loss... If anybody could help it would be much appreciated.

---

### Post by simonmoon42 on 2011-02-07
Run 

```
fdisk -l
```

If it shows up then you can use fdisk to create a partion. For fdisk help go...
[here]("http://manpages.ubuntu.com/manpages/lucid/man8/fdisk.8.html")

---

### Post by Devan1337 on 2011-02-07
> **simonmoon42 said:**
> Run 

```
fdisk -l
```

If it shows up then you can use fdisk to create a partion. For fdisk help go...
[here]("http://manpages.ubuntu.com/manpages/lucid/man8/fdisk.8.html")

nope
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58bf6ae5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14191   113989176    7  HPFS/NTFS
/dev/sda2           14192       18106    31447237+   5  Extended
/dev/sda3           18107       19458    10853376    7  HPFS/NTFS
/dev/sda5           14192       17940    30113811   83  Linux
/dev/sda6           17941       18106     1333363+  82  Linux swap / Solaris

```

My HDD would show up as 320gb I do not see it there

---

### Post by simonmoon42 on 2011-02-07
Try Gparted and see if that will find it.

It sounds to me like it was somehow disconnected while Windows was formatting it. If the format in Windows completed successfully... When you unplugged it from Windows, did you "eject" it? If you don't remove it from Windows properly it will keep it open and this can prevent it from being mounted in Linux.

---

### Post by simonmoon42 on 2011-02-07
Also check out Western Digital's [website.]("http://wdc.custhelp.com/app/answers/detail/a_id/3865") Apparently it's an issue with some of their drives. It doesn't list the Passport specifically, but the internals are probably the same.

---

### Post by Devan1337 on 2011-02-07
> **simonmoon42 said:**
> Try Gparted and see if that will find it.

It sounds to me like it was somehow disconnected while Windows was formatting it. If the format in Windows completed successfully... When you unplugged it from Windows, did you "eject" it? If you don't remove it from Windows properly it will keep it open and this can prevent it from being mounted in Linux.

GParted wont finish loading unless I unplug it and yes it was interrupted in windows but it doesn't show it correctly in windows either

---

### Post by Devan1337 on 2011-02-07
I'd also like to point out in windows it doesn't show up under disk management at all not even as unallocated space yet it shows up under device management it seems. It called it WD (model number) at first but then after reinstalling the driver software many times it just started calling it disk drive or something.

---

### Post by Devan1337 on 2011-02-07
Still have gotten nowhere :(

---


---
title: "Change NTFS Partion Size"
date: 2010-06-10
forum: General Help
---

### Post by GOTO_sHELL on 2010-06-10
Good day.

    How can I change NTFS partition size from Linux (not installing any software under Windows)? Is there any software, which can help me on this? It's desirable that this was some Gnome package.

---

### Post by indytim on 2010-06-10
If the NTFS partition is your windows ops partition, you might want to consider re-sizing using the windows utilities while booted to Windows.  Other Linux-friendly options include either booting to your LiveCd or booting to GParted Live and doing the manipulation there.  

An additional note, for Windows partitions it is good general practice to defrag a couple of times beforehand.  And the usual advisory .... backup your critical data before doing any partition changes.

Good Luck,

IndyTim / DataMan

---

### Post by efflandt on 2010-06-10
If you want to shrink or expand a Vista or Win7 partition, it is generally recommended to to that from the admin tools of that OS itself.  Other ntfs partitions can be resized with gparted in Ubuntu (included on install CD, but not on regular system unless you install it with Synaptic or using apt-get).

Simply resizing the end of a partition goes relatively quickly.  Moving a partition (or expanding the beginning of it down) takes much longer (possibly many hours).

You should not attempt to resize a partition on a drive you are running from.  Use a boot CD or system running from another drive or USB.  If your system is using swap on the drive you are modifying, you should **sudo swapoff** that partition.

---

### Post by GOTO_sHELL on 2010-06-10
Thanks for your help.

---


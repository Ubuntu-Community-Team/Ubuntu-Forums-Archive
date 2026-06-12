---
title: "SSD Alignment"
date: 2010-09-02
forum: General Help
---

### Post by dillzz on 2010-09-02
I am looking into purchasing this new SSD drive for my OS.

[http://www.newegg.com/Product/Product.aspx?Item=20-233-124&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=20-233-124&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo)

Do I need to worry about aligning partitioning?  According to 10.04 the release notes: 

By default, Ubuntu 10.04 LTS aligns partitions on disk to 1 MiB (1048576 bytes) boundaries. This ensures maximum performance on many modern disks, particularly solid state drives but also new "Advanced Format" disks with physical sectors larger than the traditional 512 bytes. Very few systems nowadays need the old alignment, used in the days of MS-DOS when it was useful for partitions to start at the beginning of a cylinder. "

What about TRIM? Firmware?  

Thanks!

---

### Post by stege on 2010-09-09
Ubuntu 10.04 (kernel 2.6.32) has partial TRIM support. It will allign the drive at install but will NOT initiate TRIM commands to free up blocks so speed degradation will be an issue.

What you need to do is upgrade the kernel to 2.6.34 so you'll have full TRIM support. Here's how:

Download the following and execute in this order:

1 - [common package 32 / 64 bit]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb")
2 - [32bit header]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb") or [64 bit header]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb")
3 - [32bit kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb") or [64bit kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb")

Then, open a terminal and type:

*sudo update-grub*

Restart your system and enjoy your new kernel :)
PS. i have the exact same SSD (F60) :)

---

### Post by dillzz on 2010-09-09
Stege,

Thank you for the information, I am currently running that kernel so thank you for the information.  I have pretty much the same layout, aka 750gb drive.  Nice improvement.  I have a 10,000 rpm drive for my OS currently (1.5 not 3.0).  Looks like this will be a nice upgrade!  


Another question.  What about the drives firmware version.  Do you have to update it/maintain it?  Is it windows only?

-Dillzz

---

### Post by stege on 2010-09-15
I couldn't tell you anything about firmware versions since I haven't done any updates yet. My F60 runs with stock firmware. However, from what I've read on the net, the Force series do not have any issues except the false SMART reports (regarding bad sectors detection). 

If I ware you, I would wait till 10.10 comes out (running on official 2.6.35 kernel which fully supports TRIM commands) before installing the Corsair. The actual 2.6.34 kernel is not exactly the most stable release if you know what I mean :D (official updates only provide a 2.6.32.24 kernel if I'm not mistaken)

Hope it helps you and sorry for the delay. My new toys kept me from...even breathing really :)

---

### Post by dillzz on 2010-10-11
Finally got my new drive installed.  Here are the performance numbers.  A much needed improvement!

---

### Post by Anubis on 2010-12-03
;)

---


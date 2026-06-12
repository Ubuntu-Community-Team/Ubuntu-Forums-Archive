---
title: "increase ubuntu partition space?"
date: 2009-07-10
forum: General Help
---

### Post by wcasper4 on 2009-07-10
I have installed Ubuntu 9.04 as a dual boot on my Toashiba next to xp so I can still have access to some windows. During install I chose the option of install next to windows. But, this installed a bare minimum of about 2.5gb for Ubuntu. I went back into windows and decreased the size of my windows partition and have two seperate unallocated space of about 12gb I want to add to my Ubuntu partition. However, I boot to Live CD and go to the partitioner. When there, I cannot increase the size of the Ubuntu partitions even though there is the unallocated space. I want to have just the two partitions, one for xp and the other for ubuntu and add my unallocated disk to the ubuntu. I also tried from a windows partitioner I have but to no avail. Any suggestions?? is there 3rd party software for linux that will do this, or am I missing something?

Thanks

---

### Post by drs305 on 2009-07-10
wcasper4,

Welcome to the ubuntu forums.

Can you post a screenshot of the gparted screen (System, Administration, Partition Editor)?

It seems they should be unmounted, so that probably isn't your issue. The free space must be in the same area as your Ubuntu install - either both inside the extended partition (light blue bordered area) or both outside the extended partition. 

Gparted should be able to handle this. If you have to take any more space from your Windows partition make sure you defrag and make back ups of your important data.

---

### Post by Bonzai11 on 2009-07-10
Looked for gparted in synaptic and choose to expand or increase ubuntu partition size add the extra space and your set.

---

### Post by wcasper4 on 2009-07-10
I don't have the option to increase when I click resize/move...

Here's the screenshot

---

### Post by merlinus on 2009-07-10
First you will have to grow sda2, the extended partition, and then you will be able to add the 7.4G to sda5.

Alternatively, or in addition, click on sda6 and select swap off, and then you can add that  and the unallocated area in sda2 to sda5.

Finally you can recreate swap.

I highly recommend that you do this with gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by wcasper4 on 2009-07-10
Excellent. Everything worked, main problem was I needed to turn swap-off. Then I could grow sda2 into the unallocated 7.4gb, delete swap and grow sda5 into the unallocated to the right, and then recreated swap. 
it's my second day on linux, i don't know why I ever used windows... I'm only keeping xp because I need itunes and office..
but props to you guys for helping make ubunto so great.
and for anyone else who struggles with this I've included a screenshot of the finished product. 
and, you may or may not encounter this problem that I also had to resolve. 
Because of the partitions being relocated, grub may have a problem of loading ubuntu. you will get "error 17" and you won't be able to do anything. 
i thought it was the end of the world, but some searching found me a resolution. 
boot from live cd. 
in terminal enter:
"sudo grub"
(you will be on >grub for next 3 commands)
"find /boot/grub/stage1"
(it will return with: example "root (hd?,?)"
"root (hd?,?)"
"setup (hd0)"
"quit"

---

### Post by haitham1 on 2009-09-07
[SIZE=5]Dude thanx a whole lot

i had the exact same problem and you having the courtesy to post up the way you solved yours helped me solve it.  cheers again!!

peace [/SIZE]




):P

---


---
title: "reclaiming unused partitions"
date: 2010-01-09
forum: General Help
---

### Post by sparky2 on 2010-01-09
I've recently installed karmic on my machine that was previously dual booting XP and ubuntu 8.xx

now I'm dual booting XP and karmic, but want to reclaim the old partitions.  

I'm  bit more cautious now snce my first attempt at using gparted led to all sorts of problems involving grub-rescue, and grub/grub2 fightling each other, but all that's been resolved (see previous thread)

attached is my partition map now according to gparted... sda8 is the partition that used to hold ubuntu 8.xx 

1) how do I tell which linux-swap partition is now used by karmic. Is it the one with the key's icon (sda7)

2) assumng sda5 is the old linux-swap parition, can I combine sda5 and sda8 back into sda6? (or alternately into sda1)

TIA

---

### Post by michy99 on 2010-01-09
To see which swap partiton Karmic uses, look at /etc/fstab.

You can't combine partitions, but you can delete the ones you don't want and expand other partitions into the free space. But a partition can only expand into space that is right beside it.

---

### Post by sparky2 on 2010-01-09
Do you determine if they're beside each other by the number?

e.g can I combine sda1 and sda5 (given there's no sda2,3,4) ?

OR can I combine sda5 with sda6 ?

---

### Post by sparky2 on 2010-01-10
> **michy99 said:**
> To see which swap partiton Karmic uses, look at /etc/fstab.

ummm, how do I do that exactly ?

thanks

---

### Post by mjitkop on 2010-01-10
> **sparky2 said:**
> ummm, how do I do that exactly ?

thanks

Open a terminal window:
Applications/Accessories/Terminal

Copy and paste this in the terminal window then press Enter:
```
cat /etc/fstab
```

This will display the content of the file "fstab". Look for a line containing the word "swap".

For example, in mine I have:
# swap was on /dev/sda5 during installation

---

### Post by raymondh on 2010-01-10
***assuming*** sda8 and sda5 are to be removed ... I would, using gparted from the liveCD (or better yet, a live gparted CD);

- delete sda5
- delete sda8
- move sda7 all the way to the right (which would move the unallocated beside sda6
- enlarge sda6

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Regards,

Raymond

---

### Post by sparky2 on 2010-01-10
OK, but here's a screenshot of my fstab ... now I'm really confused, this seems to suggest sda8 is currently my swap partition? but that conflicts with the gparted output I posted earlier ??

BTW is there an easy way to redirect o copy text output in Terminal into a text file ... using a piping command?

---

### Post by sparky2 on 2010-01-10
bump :-|

---

### Post by john newbuntu on 2010-01-11
First run a "swapoff /dev/sda8", which will make Ubuntu not use that swap partition.  Then reformat /dev/sda8 and /dev/sda5 to whatever. So you will have around 10GB that can be used as a logical partition for other purposes.

Finally, get back to Ubuntu and do a swapon /dev/sda7 so that it can be used as the swap partition.  You might want to make a change to /etc/fstab and change that large uuid for swap partition to /dev/sda7.

---

### Post by vinnywright on 2010-01-11
> **sparky2 said:**
> 
BTW is there an easy way to redirect o copy text output in Terminal into a text file ... using a piping command?

yes esey lets say you wanted that cat /etc/fstab output as a text file ...all you half to do is use a rederect like this

> cat /etc/fstab > fstab.txtthe extenshon isent nesesarey but coms in handy and >> would apend to the file spesafyed the file is created in the curent workin directory 

VINNY

---


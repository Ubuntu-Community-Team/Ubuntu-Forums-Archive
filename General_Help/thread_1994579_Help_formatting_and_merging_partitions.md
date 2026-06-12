---
title: "Help formatting and merging partitions?"
date: 2012-06-03
forum: General Help
---

### Post by pablomarusich on 2012-06-03
Well, i'm no computer genius, I need help.
I want to merge all my partitions into 1 and then format, i will be installing ubuntu again, i just need to wipe everything out, i just don't know how to merge these partitions, i dont even know what they are for. I already deleted the 2 windows partitions i had (which are now allocated) but i have absolutely no idea what the others are, heres a picture. any help will be apreciated :D
[[IMG]http://img207.imageshack.us/img207/217/screenshotfrom201206022.png[/IMG]](http://imageshack.us/photo/my-images/207/screenshotfrom201206022.png/)

---

### Post by codemaniac on 2012-06-03
Try deleting all your partitions and the space allocated to that partition will be shown as unallocated .
Then you can start all over and create the partitions you need .
Here is s helpful link for you .
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by carl4926 on 2012-06-03
Highlight swap sda7 > delete
Highlight swap sda5 > delete
Highlight sda6 > delete
Highlight sda3 extended > delete

Now create 
swap = to 2 x your RAM
ext4 Primary for / (root) 30GB is plenty
ext4 Primary for /home (use all the remaining space)

This assumes you have a backup of data?

---

### Post by pablomarusich on 2012-06-03
> **carl4926 said:**
> Highlight swap sda7 > delete
Highlight swap sda5 > delete
Highlight sda6 > delete
Highlight sda3 extended > delete

Now create 
swap = to 2 x your RAM
ext4 Primary for / (root) 30GB is plenty
ext4 Primary for /home (use all the remaining space)

This assumes you have a backup of data?

i cant delete any more partitions... for the 3 partitions having the key icon on the left the delete option is not even available, and on the only one without the key i get this message "Please unmount any logical partitions having a number higher than 5"
and yes, i do have a complete backup, i dont mind having a completely blank drive

---

### Post by codemaniac on 2012-06-03
> **pablomarusich said:**
> i cant delete any more partitions... for the 3 partitions having the key icon on the left the delete option is not even available, and on the only one without the key i get this message "Please unmount any logical partitions having a number higher than 5"
and yes, i do have a complete backup, i dont mind having a completely blank drive

You cannot delete a partition that is mounted , means you have to be in live environment in order to play with your partitions .
Plug in a live cd and launch gparted .

```
sudo gparted
```

---

### Post by carl4926 on 2012-06-03
> **pablomarusich said:**
> i cant delete any more partitions... for the 3 partitions having the key icon on the left the delete option is not even available, and on the only one without the key i get this message "Please unmount any logical partitions having a number higher than 5"
and yes, i do have a complete backup, i dont mind having a completely blank drive
You should be using a live cd of Ubuntu to do this or Parted Magic

The partition setup I gave you is for going the custom route
'Something else' [http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10_go_advanced_partit.png](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10_go_advanced_partit.png)

You could avoid all this by just running the installer and selecting 'Erase Disk and Install Ubuntu' - this will do it all for you.

---

### Post by pablomarusich on 2012-06-03
> **carl4926 said:**
> 
You could avoid all this by just running the installer and selecting 'Erase Disk and Install Ubuntu' - this will do it all for you.

By doing this does it erase or gets rud of partitions? im trully new to this subject

---

### Post by carl4926 on 2012-06-03
> **pablomarusich said:**
> By doing this does it erase or gets rud of partitions? im trully new to this subject

It should yes.

It will setup Ubuntu defaults.

---

### Post by pablomarusich on 2012-06-03
> **carl4926 said:**
> It should yes.

It will setup Ubuntu defaults.

Thank you very much for your time :D

---

### Post by carl4926 on 2012-06-03
> **pablomarusich said:**
> Thank you very much for your time :D
No worries
Come back if you need further help

---

### Post by Shadius on 2012-06-03
After completely deleting all partitions on the hard disk drive, do you plan on installing Windows and Ubuntu?

---

### Post by pablomarusich on 2012-06-03
> **Shadius said:**
> After completely deleting all partitions on the hard disk drive, do you plan on installing Windows and Ubuntu?

well i do need windows, i will try using a virtual machine first though, the problem is, maplestory(game) will not run under a virtual machine, so if i can't bypass this, i will dualboot with windows

---

### Post by wilee-nilee on 2012-06-03
It seems you have not stated your end results wanted, exactly, do that please.

---


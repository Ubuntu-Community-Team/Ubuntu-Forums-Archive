---
title: "Adding more space to my Ubuntu partition"
date: 2012-05-22
forum: General Help
---

### Post by DexyDean on 2012-05-22
Hello all,

Currently I am running my laptop dual-booted with Windows 7 and Ubuntu 12.04.

My desire is simple, but seems to cause an immense problem. I have what I need to keep safe backed up.

I currently have a 720gb hard drive, and when I first installed Ubuntu I allocated about 45gb to Ubuntu. My simple desire is to allocate more space to my Ubuntu OS than I currently have, from Windows 7. I have something around 683gb, last time I checked, on my Windows 7.

Is there a way to even them out? I would like to reallocate/re-partition in order to give more space to Ubuntu. I thought about completely uninstalling Ubuntu to re-install and get to choose how much space i allocate to Ubuntu again.

**_*Basically*_**: Allocate about 300gb of space from my windows 7 partition over and add it to the 45gb on my Ubuntu 12.04 partition.

---

### Post by wilee-nilee on 2012-05-22
> **DexyDean said:**
> Hello all,

Currently I am running my laptop dual-booted with Windows 7 and Ubuntu 12.04.

My desire is simple, but seems to cause an immense problem. I have what I need to keep safe backed up.

I currently have a 720gb hard drive, and when I first installed Ubuntu I allocated about 45gb to Ubuntu. My simple desire is to allocate more space to my Ubuntu OS than I currently have, from Windows 7. I have something around 683gb, last time I checked, on my Windows 7.

Is there a way to even them out? I would like to reallocate/re-partition in order to give more space to Ubuntu. I thought about completely uninstalling Ubuntu to re-install and get to choose how much space i allocate to Ubuntu again.

**_*Basically*_**: Allocate about 300gb of space from my windows 7 partition over and add it to the 45gb on my Ubuntu 12.04 partition.

Use the W7 disk manager in the admin to shrink it.

Use gparted on the live ubuntu cd to fill the space, by expanding ubuntu. If you have a extended around Ubuntu you will have to expand it first make sure nothing is mounted when you do this.

You may have to reload the mbr to get Ubuntu to boot again, if you move the front of its partition, or you can change the fstab to get a boot replacing the UUID with /dev/sdX the X is the HD letter not a partition number.

You would change the fstab before you expand this partition.

---

### Post by ron999 on 2012-05-22
...

---

### Post by MadmanRB on 2012-05-22
Just remember to back up everything, if you dont have an external drive or something please get one as it will solve headaches later and

---

### Post by DexyDean on 2012-05-22
> **wilee-nilee said:**
> Use the W7 disk manager in the admin to shrink it.

Use gparted on the live ubuntu cd to fill the space, by expanding ubuntu. If you have a extended around Ubuntu you will have to expand it first make sure nothing is mounted when you do this.

You may have to reload the mbr to get Ubuntu to boot again, if you move the front of its partition, or you can change the fstab to get a boot replacing the UUID with /dev/sdX the X is the HD letter not a partition number.

You would change the fstab before you expand this partition.
Thank you. I understand the shrink part, and most of the second paragraph... the rest i am utterly confused. mbr? fstab? UUID?
Anyways... I am shrinking the W7 partition now and plan to expand  ubuntu to fill the space.
Hopefully I can get it right in one go. 

What does this part mean,though?

> If you have a extended around Ubuntu you will have to expand it first make sure nothing is mounted when you do this.


---

### Post by wilee-nilee on 2012-05-22
> **DexyDean said:**
> Thank you. I understand the shrink part, and most of the second paragraph... the rest i am utterly confused. mbr? fstab? UUID?
Anyways... I am shrinking the W7 partition now and plan to expand  ubuntu to fill the space.
Hopefully I can get it right in one go. 

What does this part mean,though?

Here is my gparted notice the extended partition.

Basically a extended partition allows you to have more than the limit of 4 primary partitions on a single HD. It is a container if one is around your Ubuntu you will have to expand it first.
[ATTACH]218528[/ATTACH]

---

### Post by DexyDean on 2012-05-22
> **wilee-nilee said:**
> Here is my gparted notice the extended partition.

Basically a extended partition allows you to have more than the limit of 4 primary partitions on a single HD. It is a container if one is around your Ubuntu you will have to expand it first.
[ATTACH]218528[/ATTACH]

So I suppose I am in the wrong menu. Not sure How I get to that, or if that's the same thing...maybe?

Looks like the same thing... sort of. I attached the picture

---

### Post by wilee-nilee on 2012-05-22
> **DexyDean said:**
> So I suppose I am in the wrong menu. Not sure How I get to that, or if that's the same thing...maybe?

Looks like the same thing... sort of. I attached the picture

That is from the install, do not do anything there. Open gparted in the menu

---

### Post by DexyDean on 2012-05-22
Okay I kinda found my problem. I'm in the same menu as in your screenshot. I have an extended around it but not sure how to go from there. Just to the left of my ubuntu partition is the 280gb unallocated space.

---

### Post by wilee-nilee on 2012-05-22
> **DexyDean said:**
> Okay I kinda found my problem. I'm in the same menu as in your screenshot. I have an extended around it but not sure how to go from there. Just to the left of my ubuntu partition is the 280gb unallocated space.

If you have a unallocated space now you would right click the extended in the list and then resize and drag the part next to the unallocated to be up against the windows partition. Then do the same for the Ubuntu.

I suspect you will see this when this grub>  when you reboot after this is done if so let us know.

---

### Post by DexyDean on 2012-05-22
That's what I tried but I believe something you had said earlier is the problem. When I click it says at least one logical partition is mounted. I noticed you said i had to expand it but it wont let me re-size when i right click.


Alright I got it to work. Thanks alot for your help. I just applied the operations and right now it is adding the 300 or so gb.

Your help has been greatly appreciated. Also I had to use this... [http://askubuntu.com/questions/51272/resize-partition-with-gparted](http://askubuntu.com/questions/51272/resize-partition-with-gparted)

It is what made me realize the "swapoff" part.

Again, Thank you.

---

### Post by wilee-nilee on 2012-05-22
> **DexyDean said:**
> That's what I tried but I believe something you had said earlier is the problem. When I click it says at least one logical partition is mounted. I noticed you said i had to expand it but it wont let me re-size when i right click.

give a screen shot of the gparted.

---

### Post by jadtech on 2012-05-22
swap off it is auto mounted  from live disk

---

### Post by wilee-nilee on 2012-05-22
.

---


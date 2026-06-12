---
title: "GRUB possibly?"
date: 2011-02-05
forum: General Help
---

### Post by samishal on 2011-02-05
Hi there.

I currently have duel boot windows 7 and ubuntu on a hard drive.
I no longer use windows and just want full install of ubuntu however, I do not want to have to reinstall because all my web development tools are perfectly set up. is there a way to get rid of the grub loading screen so that it just boots into ubuntu. I already know how to expand the partition so that no problem just want to make it boot straight into Ubuntu.

thanks in advance.

ubuntu 4 ever

sam

---

### Post by TeoBigusGeekus on 2011-02-05
Expand your partitions, then
```
sudo update-grub
```
and you should be ok.

---

### Post by mike555 on 2011-02-05
after making sure it works (after update-grub and a restart  ) you can set the time delay for grub to  0 . that way you won't even see it.

---

### Post by samishal on 2011-02-05
thanks guys, also how do i edit the grub timer to 0 sorry bit a nab when it come to grub.

---

### Post by TeoBigusGeekus on 2011-02-05
```
gksu /etc/default/grub
```
Change GRUB_HIDDEN_TIMEOUT to 0.
Then
```
sudo update-grub
```
again and you're done.

---

### Post by samishal on 2011-02-05
thank you so much

---

### Post by samishal on 2011-02-06
Hi 

again guys, thanks for all the help before, i tried doing what you have said but Gparted dosent seem to let me expand the ubuntu partition sorry about my crappy noobyness.

---

### Post by TeoBigusGeekus on 2011-02-06
You should do it from a live cd, as gparted can't act on partitions that are mounted.

---

### Post by samishal on 2011-02-06
i made a live usb and tried from that but it just dosent give me the option to expand it, is there any prerequisites other than the partition cannot be mounted at the time, that i should know?

---

### Post by TeoBigusGeekus on 2011-02-06
Can you give us a screenshot of gparted, as well as the name of the partition that you want to expand?

---

### Post by samishal on 2011-02-06
heres the screen shot the partition selected is the one i want to expand, and the grey one is the one i want to expand it into.

---

### Post by TeoBigusGeekus on 2011-02-06
You first have to move the unallocated space before or after sdc5.
Right click the unallocated space, format it as ext4 and then move it.
After that, I believe that gparted will let you expand your partition.

---

### Post by samishal on 2011-02-06
where do i move the newly formatted space to?

---

### Post by samishal on 2011-02-06
becuase i have formatted the unallocated partition to Ext4 now

---

### Post by TeoBigusGeekus on 2011-02-06
Before or after sdc5, so that when you attempt to expand your partition, it has some space to expand to.

---

### Post by samishal on 2011-02-06
i think i may have guessed the problem, on the screen shot the partition i want to expand has a dark blue border(ext4). this is surrounded by a ligh blue one (ntfs). is this a problem?

---

### Post by samishal on 2011-02-07
has the thread died? i still cant expand the partition :( thanks any way guys

---

### Post by mike555 on 2011-02-07
you should be able to expand the extended partition into the other one ,but not just the ubuntu partition ,because it is contained in the extended partition .......... after you make the extended partition bigger then you should be able to make the ubuntu partition bigger into the extra room in the extended partition ..

---

### Post by glene77is on 2011-02-07
> **samishal said:**
> heres the screen shot the partition selected is the one i want to expand, and the grey one is the one i want to expand it into.

Regarding the Gparted color scheme, it is just a display scheme.

Looks like your active partition is "bootable", 
defined to be inside the Extended Partition, 
as it is the  only partition.  

Gparted will warn you that 
if you "resize" the Extended Partition, 
then it may become un-bootable.

That would be because the MBR points to a track-sector to start booting. 
The beginning track-sector was originally written into the MBR.  

In my experience, 
when I resized / moved my booting partition, 
it had to be resized / moved WITHIN the current Extended Partition. 

Having an Extended Partition which has internal partitions is confusing. 
I know that does not solve your problem.  
. . . But knowing more about the workings of Partitions 
should remove some of the mystery. 

Had an **idea** !  and it sounds like Mike555's idea:
PERHAPS you are clicking on the Ubuntu partition, 
and **you need to click on the Extended Partition**. 

I'll do some checking. 
You do the same, about "resizing / moving an Extended Partition.

---

### Post by mike555 on 2011-02-07
Of course you need to resize it from a "live " cd , you can't resize a partition when your running it ...

---


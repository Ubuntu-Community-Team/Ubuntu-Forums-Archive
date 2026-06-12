---
title: "Unhappy"
date: 2009-10-11
forum: General Help
---

### Post by even.raghu on 2009-10-11
i have vista install and i shrink the my hdd and make unpartitioned space. try to install but nothing happen and unknown error shows plz help me...
[IMG]http://img203.imageshack.us/img203/7493/image003r.jpg[/IMG]

plz help me...

---

### Post by howefield on 2009-10-11
> **even.raghu said:**
> ..and unknown error shows...

And that error was ?

---

### Post by mac666 on 2009-10-11
Whaaat?
Please, explain again? :|
You should read the guideline on how to make a post, no one could ever understand what you mean

---

### Post by 3rdalbum on 2009-10-11
Can you please be more specific. What exactly happened when you tried to install? Did you get to the partitioning screen, and if so then what did you choose? What error message was given to you?

If you can provide us with as much information as possible, we are much more likely to know what's going on and help you.

---

### Post by even.raghu on 2009-10-11
[IMG]http://img84.imageshack.us/img84/4442/image000x.jpg[/IMG]
[IMG]http://img84.imageshack.us/img84/4936/image001zo.jpg[/IMG]
[IMG]http://img94.imageshack.us/img94/527/image002m.jpg[/IMG]
[IMG]http://img96.imageshack.us/img96/695/image005gb.jpg[/IMG]

---

### Post by MelDJ on 2009-10-11
is the hard disk old? or if there is nothing in the space, format it

---

### Post by howefield on 2009-10-11
Choose "use largest free space" instead of the manual option.

The manual option means you need to tell the installer what to do with the partition, what file format you want to use, and what the mount point is, root would be /


Here is a short video, explaining the partitioning part of installing ubuntu,

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

(fourth video down the page)

---

### Post by even.raghu on 2009-10-11
> **MelDJ said:**
> is the hard disk old? or if there is nothing in the space, format it
my hdd is new 500gb sata and when i select it to nothing appear in below...

same problem with my brother new laptop too

---

### Post by even.raghu on 2009-10-11
> **howefield said:**
> Choose "use largest free space" instead of the manual option.

u see the screenshot no use largest free space appear...

same problem with my brother new laptop too

---

### Post by mcduck on 2009-10-11
Your hard drive already has 4 primary partitions, which means that it's not possible to create any more. That's why the rest of the space on your disk is marked as "unusable" instead of free space.

Hard drives can only have 4 primary partitions, or 3 primary ones plus one extended partition (which can then contain as many logical partitosn as you want.

To use the rest of the available space on the drive you'll need to delete the last partition, and then create extended partition to fill the available space on the drive. Then you could create more partitions inside the extended one. Of course this will destroy all data on that partition so you'll need to back it up somewhere else first.

Also you should use proper screenshots instead of taking photographs of your display. It was pretty hard to figure out your actual partition layout since the text really isn't too easy to read.. Just press the PrtScr-button on your keyboard and ubuntu will make a proper screenshot for you..

---

### Post by even.raghu on 2009-10-11
> **mcduck said:**
> Your hard drive already has 4 primary partitions, which means that it's not possible to create any more. That's why the rest of the space on your disk is marked as "unusable" instead of free space.

Hard drives can only have 4 primary partitions, or 3 primary ones plus one extended partition (which can then contain as many logical partitosn as you want.

To use the rest of the available space on the drive you'll need to delete the last partition, and then create extended partition to fill the available space on the drive. Then you could create more partitions inside the extended one. Of course this will destroy all data on that partition so you'll need to back it up somewhere else first.

Also you should use proper screenshots instead of taking photographs of your display. It was pretty hard to figure out your actual partition layout since the text really isn't too easy to read.. Just press the PrtScr-button on your keyboard and ubuntu will make a proper screenshot for you..
thanks bro.. now i will try it...

---

### Post by ibuclaw on 2009-10-11
> **mcduck said:**
> Your hard drive already has 4 primary partitions, which means that it's not possible to create any more. That's why the rest of the space on your disk is marked as "unusable" instead of free space.

Hard drives can only have 4 primary partitions, or 3 primary ones plus one extended partition (which can then contain as many logical partitosn as you want.

To use the rest of the available space on the drive you'll need to delete the last partition, and then create extended partition to fill the available space on the drive. Then you could create more partitions inside the extended one. Of course this will destroy all data on that partition so you'll need to back it up somewhere else first.

Also you should use proper screenshots instead of taking photographs of your display. It was pretty hard to figure out your actual partition layout since the text really isn't too easy to read.. Just press the PrtScr-button on your keyboard and ubuntu will make a proper screenshot for you..
 

+1


Sorry buddy, but you can only have 4 Primary Partitions on a Hard Drive.

You are going to have to backup all the data on the **sda4** partition (the one that is 64GB big), nuke it, then create an **Extended Partition** to fill up the **entire** free space.

Then you can create the **Logical Partitions** required to restore your backed up data and for Ubuntu to install inside that Extended Partition.

Regards
Iain

---

### Post by The Cog on 2009-10-11
But which partition did you shrink to make that free space? Hopefully it was the third or fourth partition. If not, there is a danger that when you delete the fourth partition, you will be left with two seaparate unused areas of the disk, which cannot then be put into a single extended partition.

---

### Post by mcduck on 2009-10-11
> **The Cog said:**
> But which partition did you shrink to make that free space? Hopefully it was the third or fourth partition. If not, there is a danger that when you delete the fourth partition, you will be left with two seaparate unused areas of the disk, which cannot then be put into a single extended partition.

Since the free space is after the sda4 partition the only possible partition he could have resized to create the space is sda4.

---

### Post by The Cog on 2009-10-11
> **mcduck said:**
> Since the free space is after the sda4 partition the only possible partition he could have resized to create the space is sda4.

Aah you're right. I didn't look at the bar disk layout.

---


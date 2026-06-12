---
title: "Expanding a partition"
date: 2011-10-19
forum: General Help
---

### Post by rmcellig on 2011-10-19
I want to delete sda6 and sda8 so that I can expand sda9 to make it larger. What do I have to do to expand sda9 to take over sda6 and sda8?

---

### Post by Azyx on 2011-10-19
You need first to unmount, before you can rezise partitions. If you place you pointer over /dev/sda2 and right-klick and choise "unmount". i think all partition get unmounted in the logical partition, otherwise you have to unmount all partition and choise 2swap=off. If it now work, boot up the system from a live-CD or live-USB.

---

### Post by rmcellig on 2011-10-19
Hi Azyx,

I was booted in to the live CD. This is the image in my previous post. For some reason I was unable to unmount and of the partitions. Unmount was greyed out when I right mouse clicked on any of the partitions. Any idea what I should do?

---

### Post by Azyx on 2011-10-19
> **rmcellig said:**
> Hi Azyx,

I was booted in to the live CD. This is the image in my previous post. For some reason I was unable to unmount and of the partitions. Unmount was greyed out when I right mouse clicked on any of the partitions. Any idea what I should do?


I don't know.. But have you tried swap-off the the red swap-partitons first?

---

### Post by rmcellig on 2011-10-19
Thanks! I will try that. How to I do swap off? Do I write click on the swap file partitions and turn them off that way. I will try that tomorrow and post back with the results.

---

### Post by Erlander on 2011-10-20
You could also try installing GParted from the repositories.  You will still need to unmount the drive.

---

### Post by Azyx on 2011-10-20
> **rmcellig said:**
> Thanks! I will try that. How to I do swap off? Do I write click on the swap file partitions and turn them off that way. I will try that tomorrow and post back with the results.


Right-click the swap-area and select swapoff, but I'm not shure it help, I  don&#7831; use to use 'extended' partition and don't know how the are connected...

---

### Post by Quackers on 2011-10-20
Turning swap off should do it.
And while you're in there extending things you could lose a swap partition or two :-)

---

### Post by rmcellig on 2011-10-20
> **Erlander said:**
> You could also try installing GParted from the repositories.  You will still need to unmount the drive.

I am using Gparted because I started up with the live cd.

---

### Post by 23dornot23d on 2011-10-20
Using the liveCD for this is best .... as you are doing

Also as Quackers says ..... only one swap space is needed ..... 

I find doing one step at a time is best too using gparted ....

if you delete two of the swap spaces .... you can do in one go

if you then delete the partitions you want after that .... do one at a time

( if there is any data you need on sda9 make sure you Have a Backup too )

Then move sda9 to the left and resize   ...... this takes time ...... ( I personally would leave 20 Gig unallocated at the end)

( I tend to leave 20 Gig free in case I want to put another OS on though .... as shrinking a
partition with lots of data on afterwards to accommodate anything else takes a long time.
also not needed if a space already exists ...... say next time you want to try a new version of linux in there )

---

### Post by rmcellig on 2011-10-20
Hi 23dornot23d

Great advice!

I will take my time and do the steps one at a time. sda9 is my Mint 11 partition. I don't have any data on it. I just installed it yesterday. I'll post back with whether I am successful or not. Thanks again!!

---

### Post by Azyx on 2011-10-20
> **23dornot23d said:**
> 
if you delete two of the swap spaces .... you can do in one go


I think it also good to place the swaparea in the beginning of sda2 (The extended partition) so the swap are on the middle of the disk? In that case the hdd-arm not need to move so long distance.

---

### Post by 23dornot23d on 2011-10-20
Yep I agree swap maybe better nearer the middle ....

__________________________

When you try to move sda9 ..... it will warn you that it may not boot that anymore ......

Let me know if it does  .... ( if it was a DATA partition there is no problem )

If you only installed yesterday its worth trying .... as reinstalling after may not be too much of a pain
with it only being a day old ...... but upto you ...... 

I have no idea how much customizing you can do in a day .

---

### Post by rmcellig on 2011-10-20
The machine I am doing this on is one of my old (3 years old) HP laptops. I use them to learn Linux on because I feel the best way to learn is first hand and actually doing it. If I have to reformat the drive, so be it. It's all part of learning and it is fun. My iMac is my main computer although I spend about 80-90% on the Linux machines because I find them faster and way more fun!

I am going to use Boot Repair to fix the boot loader after all this partition moving is done. I tried it yesterday and it worked great in getting my boot loader to work after I moved a couple of other partitions on the drive. Thanks again for all the help and encouragement I am getting in this thread!! :)

---

### Post by rmcellig on 2011-10-20
I will post a screen shot of what my partition scheme looks like after I am all finished. I will move the swap files to the center. How do I know which swap file belongs to which partition or does it matter?

---

### Post by Azyx on 2011-10-20
> **rmcellig said:**
> I will post a screen shot of what my partition scheme looks like after I am all finished. I will move the swap files to the center. How do I know which swap file belongs to which partition or does it matter?

Swap don't belong to any partition, but to the system. If you have dual-boot you only need one swap-area.

---

### Post by rmcellig on 2011-10-20
Here is where things stand now. How do I move the swap partitions between  sda1 and sda7 as suggested in a previous post?

---

### Post by Azyx on 2011-10-20
> **rmcellig said:**
> Here is where things stand now. How do I move the swap partitions between  sda1 and sda7 as suggested in a previous post?
If you computer are 3 years old you probably don't need any swap during live-session. If you have more than 500MB ram just swapoff your swap and erase them, then move sda7 to the right. After that create a new swap  between sda1 and sda7.

---

### Post by rmcellig on 2011-10-20
OK. Let me try that and I will post back an image so you can tell me if I am doing this right. I have 3GB of RAM in the laptop with a 260GB HD.

---

### Post by rmcellig on 2011-10-20
Finally I am all finished! Check out the image. I created a partition and I called it swap. Is there anything else I need to do to make this a swap file?

---

### Post by 23dornot23d on 2011-10-20
Nope ... you cannot do that..... with swap .... as far as I know ...

There is a separate selection for swap ...... like ext2 ext3 ext4   swap .......

It will appear red on the gparted display as it did before  ........

its easy to do now you are nearly there .....

Delete the one you called swap ..... and replace it with a red swap area by using the type of partition selection box .........  8Gig the same size is good .....

That should do you once you have done that ...... looks tidy ..... and should work well too ...

---

### Post by rmcellig on 2011-10-20
How does this look? If I boot in either partition, will it look for that swap file I just created? How does that work?

Thanks again to everyone in this thread who helped me out!! Being a Mac user, I am really liking Linux more and more!!

---

### Post by Azyx on 2011-10-20
> **rmcellig said:**
> Finally I am all finished! Check out the image. I created a partition and I called it swap. Is there anything else I need to do to make this a swap file?

Look nice. You don't need to name it swap, but it don't hurt ;) It looks right. Now you hade gualboot between ubuntu and mint. Or?
/Cheers

---

### Post by 23dornot23d on 2011-10-20
Sorted ... mark it as solved if you are managing to boot both systems ok now ....

and set yourself another challenge .... thats how it tends to go ..... ;)

Looks good main thing is does it work ..... :o

---


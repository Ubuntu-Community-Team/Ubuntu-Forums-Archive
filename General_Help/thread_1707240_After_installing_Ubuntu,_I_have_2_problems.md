---
title: "After installing Ubuntu, I have 2 problems"
date: 2011-03-15
forum: General Help
---

### Post by Abhi85 on 2011-03-15
Hey,

I have 2 HDD and in my first HDD there is Win XP and in my second HDD there is Ubuntu. Now the confusing part is that, I installed ubuntu in my second HDD and now the whole HDD is gone. I had 3 partitions in it and now none of them are appearing so its making me wonder where my HDD is and where my ubuntu is installed?

Second problem is that I can't connect to internet via ubuntu, how do I go about it?

Please help me with the solution, I don't wanna loose my other partitions. Thanks.

Regards.

---

### Post by baldawat on 2011-03-15
> **Abhi85 said:**
> Hey,

I have 2 HDD and in my first HDD there is Win XP and in my second HDD there is Ubuntu. Now the confusing part is that, I installed ubuntu in my second HDD and now the whole HDD is gone. I had 3 partitions in it and now none of them are appearing so its making me wonder where my HDD is and where my ubuntu is installed?

Second problem is that I can't connect to internet via ubuntu, how do I go about it?

Please help me with the solution, I don't wanna loose my other partitions. Thanks.

Regards.

wat I am getting from your post that you have installed ubuntu with default option..
with check fdisk -l that partion are present in in your hard drive.
there three logical partions there 
windows ntfs
swap linux-bla-bla
root partition..
may be this will help in getting partitions detemination

---

### Post by Abhi85 on 2011-03-15
> **baldawat said:**
> wat I am getting from your post that you have installed ubuntu with default option..
with check fdisk -l that partion are present in in your hard drive.
there three logical partions there 
windows ntfs
swap linux-bla-bla
root partition..
may be this will help in getting partitions detemination

Thanks for the reply but I'm quite newbie. If you can be more clear about what I should do, that would help.

---

### Post by ChipOManiac on 2011-03-15
> **Abhi85 said:**
> Thanks for the reply but I'm quite newbie. If you can be more clear about what I should do, that would help.

Okay, lets make it easier...
1. Alt-F2
2. Type GParted
3. Hit Enter

If you don't see any other partitions on your HDD... Well your worst is confirmed...

As for the internet question... it may help if you post how you're trying to connect to the internet...

---

### Post by Abhi85 on 2011-03-15
> **ChipOManiac said:**
> Okay, lets make it easier...
1. Alt-F2
2. Type GParted
3. Hit Enter

If you don't see any other partitions on your HDD... Well your worst is confirmed...

As for the internet question... it may help if you post how you're trying to connect to the internet...
Okay, I'm on win xp right now so I will switch to test what you told me after this post is completed.

I have a ADSL connection and ofc I connect with the ADSL router. Any other info I'm missing to mention here?

---

### Post by Abhi85 on 2011-03-15
I typed 'gparted' and it gives me an error and says " could not find the file/folder so I guess its screwed up. How do i fix this?

---

### Post by ChipOManiac on 2011-03-15
Okay looks like you don't have gparted installed...

Open a terminal ans type 'cat /proc/partitions/'

---

### Post by Abhi85 on 2011-03-15
Still says... "could not find the file/folder".

---

### Post by ChipOManiac on 2011-03-15
Not to be rude or anything... are you trying these commands on Ubuntu? "could not find the file/folder"? cat program is standard the last time I checked....

---

### Post by Abhi85 on 2011-03-15
> **ChipOManiac said:**
> Not to be rude or anything... are you trying these commands on Ubuntu? "could not find the file/folder"? cat program is standard the last time I checked....

Of course mate. "Could not find the file/folder" was the message I got when I typed it in the terminal.

---

### Post by piquat on 2011-03-15
```
cat /proc/partitions/
```
Doesn't work for me either.

However:
```
cat /proc/partitions
```
does work.

---

### Post by Abhi85 on 2011-03-15
Ok, I will try that... 

But, I just tried fdisk -l and it shows the partitions in the terminal but it can't be seen in "my computer" neither in ubuntu or win xp.

---

### Post by ChipOManiac on 2011-03-15
Okaaayyy... Let me get this straight.... 
You have 3 partitions:
1. With Microsoft Windows XP ©®(TM)
2. Ubuntu
3. And Another Partition

Your XP is okay, but you cannot access any other partitions in your Ubuntu installation...

You tried to execute "gparted" and "cat /proc/partitions" on Ubuntu but got "could not find the file/folder"...

Just as a test try "sudo fdisk -l" in a terminal in ubuntu and post the output... otherwise there is something wrong with your ubuntu installation... <-- :O Dumb Me...

---

### Post by ChipOManiac on 2011-03-15
> **piquat said:**
> ```
cat /proc/partitions/
```Doesn't work for me either.

However:
```
cat /proc/partitions
```does work.

As of now I am jumping around my room holding my ears in the tradidional way of punishment as an apology to Abhi :( Apologies for the confusion and thanks Piquat for poiting that out.

---

### Post by Abhi85 on 2011-03-15
@Chip- It's okay mate... ^_^

Anyway, this is what I got..

---

### Post by 3rdalbum on 2011-03-15
> **Abhi85 said:**
> Ok, I will try that... 

But, I just tried fdisk -l and it shows the partitions in the terminal but it can't be seen in "my computer" neither in ubuntu or win xp.

Windows XP will not read the Linux partitions; it doesn't understand them.

Ubuntu doesn't represent the partitions in the same way that Windows XP might have. Your Ubuntu partition is "Filesystem" or "/". There's an Extended partition too, which isn't a partition per-se but a container that can hold lots more partitions. It's not used directly for file storage, so it won't be shown in "Computer". And then you've got your swap partition - this isn't used for file storage, only for temporary storage - so this isn't shown in "Computer" either.

Does that answer your question, or have I misunderstood the question?

Also, for your internet question, how is your ADSL modem hooked up to your computer? Is it via an Ethernet cable, or through wireless (Wifi)? If it's through Wifi, then you might need to temporarily plug in via Ethernet, run the system updates, and then go to System > Administration > Additional Drivers to see if there's a driver listed for your card.

---

### Post by ChipOManiac on 2011-03-15
Okay... I your screen dump shows that you have three NTFS's And sda1 is obviously your (Microsoft Windows Xp) ©®(TM) partition...

Open up System -> Administration -> Disk Utility and in the application navigate to your disk (left side "Storage Devices" and click it. 

If any of the partitions show up (Right Side)... click one of the NTFS partitions untill it's highlighted and then click mount, once it's mounted, it should appear in the "Places" menu on the desktop... else just click on the blue hyperlink like text next to  "Mount Point:" in the Disk Utility... (I'd make a small backup of the data too)...

---

### Post by Abhi85 on 2011-03-15
> **3rdalbum said:**
> Windows XP will not read the Linux partitions; it doesn't understand them.

Ubuntu doesn't represent the partitions in the same way that Windows XP might have. Your Ubuntu partition is "Filesystem" or "/". There's an Extended partition too, which isn't a partition per-se but a container that can hold lots more partitions. It's not used directly for file storage, so it won't be shown in "Computer". And then you've got your swap partition - this isn't used for file storage, only for temporary storage - so this isn't shown in "Computer" either.

Does that answer your question, or have I misunderstood the question?

Also, for your internet question, how is your ADSL modem hooked up to your computer? Is it via an Ethernet cable, or through wireless (Wifi)? If it's through Wifi, then you might need to temporarily plug in via Ethernet, run the system updates, and then go to System > Administration > Additional Drivers to see if there's a driver listed for your card.

My ADSL modem is connected via Ethernet cable. I checked the additional drivers but it only shows up of my graphics card (NVIDIA) at start. Nothing else popped up when I went to additional drivers.






> **ChipOManiac said:**
> Okay... I your screen dump shows that you have three NTFS's And sda1 is obviously your (Microsoft Windows Xp) ©®(TM) partition...

Open up System -> Administration -> Disk Utility and in the application navigate to your disk (left side "Storage Devices" and click it. 

If any of the partitions show up (Right Side)... click one of the NTFS partitions untill it's highlighted and then click mount, once it's mounted, it should appear in the "Places" menu on the desktop... else just click on the blue hyperlink like text next to  "Mount Point:" in the Disk Utility... (I'd make a small backup of the data too)...

I tried this and the worst has come true here. All the 3 paritions has joined together I think. Though, you can be a better judge of it. Check it out.

---

### Post by pqwoerituytrueiwoq on 2011-03-15
> **ChipOManiac said:**
> Okay looks like you don't have gparted installed...

Open a terminal ans type 'cat /proc/partitions/'
you have a extra slash in the command
cat /proc/partitions
partitions is a file not a folder and you can't cat a folder
as for the internet issue 
```
lspci | grep "Ethernet controller"
```what does that give you in the terminal
also what does this give you
```
ifconfig eth0
```@I tried this and the worst has come true here. All the 3 partitions has  joined together I think. Though, you can be a better judge of it. Check  it out.
they are good
the big gray part is the main install the top white part tell you the size of your extended partition and it has 1 of 4 partition in it your swap partition

---

### Post by ChipOManiac on 2011-03-15
> **pqwoerituytrueiwoq said:**
> you have a extra slash in the command
cat /proc/partitions
partitions is a file not a folder and you can't cat a folder


Yeah I know... :D Back in post 14 or something I apologized... :D Thanks for pointing out anyway... I missed that typo... :D

---

### Post by ChipOManiac on 2011-03-15
> **Abhi85 said:**
> 
All the 3 paritions has joined together I think. Though, you can be a better judge of it. Check it out.


Yes it seems that way, Unfortunatley you have used the default option which erases the whole disk... 

Sorry about your data bhai... :( hope you had any backups somewhere... 

At least you'll be a little more careful next time...

By The Way : Your 160 GiB seems to have some bad blocks, boot through the live CD and get a scan and see if it's really bad by running "sudo badblocks -v /dev/sdb" in a terminal, if it jumps more than a few KiB's, don't save anything important on it or just get rid of it.

---

### Post by Abhi85 on 2011-03-15
> **pqwoerituytrueiwoq said:**
> you have a extra slash in the command
cat /proc/partitions
partitions is a file not a folder and you can't cat a folder
as for the internet issue 
```
lspci | grep "Ethernet controller"
```what does that give you in the terminal
also what does this give you
```
ifconfig eth0
```@I tried this and the worst has come true here. All the 3 partitions has  joined together I think. Though, you can be a better judge of it. Check  it out.
they are good
the big gray part is the main install the top white part tell you the size of your extended partition and it has 1 of 4 partition in it your swap partition
So does that mean my partitions are still there including my data?

---

### Post by Abhi85 on 2011-03-15
> **ChipOManiac said:**
> Yes it seems that way, Unfortunatley you have used the default option which erases the whole disk... 

Sorry about your data bhai... :( hope you had any backups somewhere... 

At least you'll be a little more careful next time...

By The Way : Your 160 GiB seems to have some bad blocks, boot through the live CD and get a scan and see if it's really bad by running "sudo badblocks -v /dev/sdb" in a terminal, if it jumps more than a few KiB's, don't save anything important on it or just get rid of it.

FFS!! That's lame!! Well, I had some important data that's why i was bit worried. I didn't know the entire HDD would be formated wherein I just selected 1 partition for installation. Bad start with ubuntu for me lol.

---

### Post by Abhi85 on 2011-03-16
So, no one can help?

---

### Post by ChipOManiac on 2011-03-16
> **Abhi85 said:**
> So, no one can help?

Other than the internet connection... No... Ubuntu was installed to the whole disk, so it overwrites and destroys any way of getting the data back... Sorry bhai... :(

---

### Post by Abhi85 on 2011-03-16
Okay Bhai, So how I go about fixing my net problem?

---

### Post by ChipOManiac on 2011-03-16
> **Abhi85 said:**
> 
My ADSL modem is connected via Ethernet cable. I checked the additional drivers but it only shows up of my graphics card (NVIDIA) at start. Nothing else popped up when I went to additional drivers.


Actually... Connecting through the ethernet does not require any drivers... You might want to check the Network settings in the System menu..

---


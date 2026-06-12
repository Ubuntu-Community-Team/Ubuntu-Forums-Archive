---
title: "Please help :("
date: 2010-03-21
forum: General Help
---

### Post by tal32123 on 2010-03-21
I tried adding space from a partition I deleted to my windows partition, and it didn't work. So then I unmounted my windows partition. I wanted to restart my computer into windows later on, and it wouldnt work. So I thought it was because it wouldnt permanantly mount, so I messed around with a bunch of settings and I tried ntfs-config but it said that for the mount point windows was already taken so I tried making "windows 7" as a mount point which it allowed me to do, but I still cant boot into windows, please help :( attached is the information from gparted

---

### Post by tal32123 on 2010-03-21
I also tried installing world of padman but it said no write permission to usr/local/games

---

### Post by 2hot6ft2 on 2010-03-21
Don't do anything else to the partitions until one of the partition gurus steps in. You're only showing 91.18 MiB used on the windows partition.

---

### Post by tal32123 on 2010-03-21
omg i didnt see that...........that just adds to my problems :( :( can you help me with the game?

---

### Post by Usabent on 2010-03-21
Well i think you restart your comp then boot in to the gparted thing. Mount it again and restart but this time dont boot in to gparted! Looks like its 91 mb. You messed up the partion. Used cant be 91.1 mb on your windows 7 partion. Looks liek you have to re-install 7 again. This is why you shouldnt mess with your partions! It should be at least used 3-10 gb.

---

### Post by 2hot6ft2 on 2010-03-21
> **tal32123 said:**
> omg i didnt see that...........that just adds to my problems :( :( can you help me with the game?
And you're worried about the game?:confused:
Don't reboot either.
Run
```
fdisk -l
```
and post it so they'll have some more info to start with.

---

### Post by Usabent on 2010-03-21
Tryue you can try that but the used suppose to be at least 600mb-1- 10 gb on your ntfs partion if you alreayd yinstalled windows

---

### Post by tal32123 on 2010-03-21
i know that 90 mb is way too small, and fdisk -l doesnt show anything

---

### Post by 2hot6ft2 on 2010-03-21
> **tal32123 said:**
> I tried adding space from a partition I deleted to my windows partition, and it didn't work. So then I unmounted my windows partition. I wanted to restart my computer into windows later on, and it wouldnt work.
So I'm understanding it as win7 was there (installed) and he was going to give it more space. So big oops, wait for those that know a lot about fixing these types of situations before doing anything.
And running ```
sudo fdisk -l
``` will only show information about the partitions it wont make ANY changes.

Sorry forgot the sudo in the rush to post.

Put the results in a code box using the # at the top of the post box to save the formatting.

---

### Post by Usabent on 2010-03-21
Next tine if you ever try to add more space buy a  2nd internal hd . Your first hd has windows on it and on your second one yo ucan expermint but make sure you dont mess with bootloader!

---

### Post by sailthesea on 2010-03-21
You have 5 primary partitions which is not good. I would suggest using a LiveCD and GParted to expand the sda\5 into the unused part in front of it 
 Before that however you should fix the Windows issue, if you have recovery media use that to get 7 back. Then worry about restoring Grub and recovering your dual boot
 Good Luck1

---

### Post by 2hot6ft2 on 2010-03-21
> **sailthesea said:**
> You have 5 primary partitions which is not good. I would suggest using a LiveCD and GParted to expand the sda\5 into the unused part in front of it 
 Before that however you should fix the Windows issue, if you have recovery media use that to get 7 back. Then worry about restoring Grub and recovering your dual boot
 Good Luck1
There are only 4 partitions there total. I would wait for a guru to step in. You'll know when you see what they tell you to do. It will be detailed and they will most likely want you to provide more info first. Most likely they will have you get and run testdisk to recover things like the windows partition which I suspect is damaged.
If you start doing other things you may damage it further.

---

### Post by tal32123 on 2010-03-21
yes i have to wait for detailed instructions since im a linux noob lol

---

### Post by sailthesea on 2010-03-21
> **2hot6ft2 said:**
> There are only 4 partitions there total. I would wait for a guru to step in. You'll know when you see what they tell you to do. It will be detailed and they will most likely want you to provide more info first. Most likely they will have you get and run testdisk to recover things like the windows partition which I suspect is damaged.
If you start doing other things you may damage it further.

 You are correct, I was misreading the swap for a primary. The issue remains that Win is blown out and must be sorted first.

---

### Post by 2hot6ft2 on 2010-03-21
> **tal32123 said:**
> yes i have to wait for detailed instructions since im a linux noob lol
Meanwhile you could still post the output of
```
sudo fdisk -l
```
And it's not just being a nOOb. I'm not that well versed in recovering from something like that so that's why I said I would wait. I really meant "I would wait". There are some really smart people here and it's not possible for one person to know everything. Some know a lot about partitions and the ins and outs of them.
I couldn't tell you how to create partitions by command line they can.

---

### Post by tal32123 on 2010-03-21
thats true, anyway im uploading the sudo fdisk -l

---

### Post by 2hot6ft2 on 2010-03-21
> **sailthesea said:**
> You are correct, I was misreading the swap for a primary. The issue remains that Win is blown out and must be sorted first.
I agree that the windows partition should be recovered first but does that conflict or will it conflict with the extended partition next to it when recovering it?
If it belongs a little to the right then there is a conflict and I've seen some that to me looked simple like what you're thinking but the partition data said something else.

I used to watch cal something work his magic on partition problems but haven't seen a post from him in a long time.

If I were going to say anything as far as doing something with it right now it would first be to shrink the left side of the extended partition to the right away from the windows partition. But I'm keeping my trap shut to let those that know more step in rather than making it worse.

---

### Post by 2hot6ft2 on 2010-03-21
> **tal32123 said:**
> thats true, anyway im uploading the sudo fdisk -l
Could you copy and paste it? LOL, nice try though.
When you paste it highlight it all and click on the # sign at the top of the post box. That will put it in a Code box which will save the formatting so it will still look the same and wont be all bunched up.

---

### Post by 2hot6ft2 on 2010-03-21
You may want to do one of 2 things.
1. Change the title of the thread to something like Partition Help Needed!!!
or
2. Start a new thread with a title like that and start it off with an explanation of what happened that got you in this mess (just that facts don't make it drag on and on, your first post was good) and include both the pic that is in the first post and the results from the fdisk command in a code box.

Choose either General Help or Installation and Upgrades for the category.

Either one of those will get a lot more attention from the right people since many times they will skip right by a non-descriptive title like this thread has. I usually skip threads that provide no clue as to what it's about myself. Please Help :( is not a good thread title to get good help.

I'm calling it a night. I hope you get it straightened out. Take my suggestion above and more people will respond that know partitioning.

Good night.

---

### Post by tal32123 on 2010-03-21
i just reinstalled ubuntu over everything :(

---

### Post by jsriz on 2010-03-21
> **tal32123 said:**
> i just reinstalled ubuntu over everything :(
This is the best and easiest thing you could have done
erasing any chance of recovery of the data in the windows partition
now you only have to worry about grub2 reinstall when you install  windows (i.e. if you want to)

---

### Post by tal32123 on 2010-03-21
well that didnt help as soon as i tried that it wouldnt even run ubuntu, and then i tried installing windows and ubuntu several times (both x86 and x64) and it still didnt work until right now :( i guess ill just stick to windows until ubuntu gets some good games :( anyway thanks for the help

---

### Post by sailthesea on 2010-03-21
I'm sorry to hear you experienced such problems.:icon_frown:
 If you want to play games then you should stick with Windows, Ubuntu doesn't do well in that area. You could use Wine or Virtualization but it is a  complex thing for an inexperienced user.
 I have been a user for over a year and I've many things still to learn about Linux based systems. 
 You should take what you may have learned from this and try and gain from it.
 Good Luck:)

PS: If you edited the Win7 partition with GParted this is probably where you came unstuck. I believe it is best to use Windows Disk Manager for this type of operation.

---

### Post by tal32123 on 2010-03-22
> **sailthesea said:**
> I'm sorry to hear you experienced such problems.:icon_frown:
 If you want to play games then you should stick with Windows, Ubuntu doesn't do well in that area. You could use Wine or Virtualization but it is a  complex thing for an inexperienced user.
 I have been a user for over a year and I've many things still to learn about Linux based systems. 
 You should take what you may have learned from this and try and gain from it.
 Good Luck:)

PS: If you edited the Win7 partition with GParted this is probably where you came unstuck. I believe it is best to use Windows Disk Manager for this type of operation.

I know how to use wine/playonlinux, but many things still dont work. I guess I'll be back on ubuntu next year lol :D

---


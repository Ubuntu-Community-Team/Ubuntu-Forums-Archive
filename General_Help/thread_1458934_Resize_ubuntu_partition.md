---
title: "Resize ubuntu partition?"
date: 2010-04-20
forum: General Help
---

### Post by milleja46 on 2010-04-20
When i was looking around on my computer i noticed i only had 5.8 gb free, but i still had a drive labeled linux that had nothing on it that i meant for ubuntu. How do i combine it? I already deleted the drive so it's unallocated, but i need to know how to combine it.

Thanks in advance for any help!

---

### Post by milleja46 on 2010-04-20
Sorry for the bump, but i don't think anyone is gonna answer this with how far down the list it is...

---

### Post by d3v1150m471c on 2010-04-20
You'll probably need to use something like gparted. Strongly recommend making a backup first.

---

### Post by Yogotiss on 2010-04-20
> **d3v1150m471c said:**
> You'll probably need to use something like gparted. Strongly recommend making a backup first.

I 2nd that!

---

### Post by milleja46 on 2010-04-20
Umm, i have been trying gpart but it won't let me resize for some reason.....(and there's not anything to backup, i just installed ubuntu recently so not much i'd be missing)

---

### Post by drs305 on 2010-04-20
Take a look at this thread I made about resizing the / partition. The first half concerns a bug in Jaunty but the second half covers what you want to do:
[ Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by arrimapirate on 2010-04-20
GParted wont resize your / partition (assuming thats the one you want to resize) while it is mounted, but you cant unmount it while logged in.
Solution? Boot into your live Ubuntu cd and use GParted from there.

---

### Post by milleja46 on 2010-04-20
Well the problem with that is i can't even select anything at all for some reason!  I can't even resize the windows partition. Which is on the same drive, but still, it's not mounted right now. So i am gonna need another solution.

---

### Post by arrimapirate on 2010-04-20
Do you see a set of keys next to your partition in GParted and when you right click do you see nothing but grayed out text?

---

### Post by milleja46 on 2010-04-20
That's exactly what i see....and i don't think i should since i am the admin user

---

### Post by arrimapirate on 2010-04-20
Resizing an ntfs partition with windows can be hard and sometimes wont let you shrink it by much due to fragmentation and unmovable files.

---

### Post by arrimapirate on 2010-04-20
First you have to have the ntfs partition unmounted to be able to make changes. The / partition can not be edited unless you are in a live system (to the best of my knowledge) I recently had to resize mine when i deleted Windows for good.

---

### Post by milleja46 on 2010-04-20
That doesn't make sense.....i guess i gotta get easus for linux if there is one....

---

### Post by arrimapirate on 2010-04-20
Sorry if i phrased that weird. What part didnt make sense? ill try to explain better.
A step by step of what you want done would help me help you out better.

---

### Post by drs305 on 2010-04-20
Much of this I think is explained in the link I provided. Even from the LiveCD, the partitions, including the swap partition, must be unmounted. Until this is accomplished you won't be able to move/delete/expand partitions.

---

### Post by milleja46 on 2010-04-20
How do i create the livecd?

---

### Post by arrimapirate on 2010-04-20
The cd you installed Ubuntu from can run a live system. Boot your computer from the cd and select "try Ubuntu without making changes to my system"

---

### Post by milleja46 on 2010-04-20
Oh, i feel stupid now....

---

### Post by arrimapirate on 2010-04-20
Dont! It was an easy thing to forget or not notice if you just went with the install choice. 
So what exactly do you want to do?
Shrink an ntfs partition then add that free space to your Ubuntu partition?

---

### Post by milleja46 on 2010-04-20
No, i had space that was supposed to be in my ubuntu installation but for some reason it didn't go there, it went to a seperate installation(because i made the partition for ubuntu in windows partition manager) I deleted my partition i labeled ubuntu.  So now i have 59.64 gb i want put into my ubuntu.

So in gparted(since i am in livecd mode) what do i enter into the free space preceding, new size, and the free space following?

---

### Post by arrimapirate on 2010-04-20
OKay. Boot the live cd -> go to system -> Administration -> GParted
Right click the partition with Ubuntu installed on it and click "Unmount" Then right click it and click "Resize/Move" and drag the handle to take up all the unused space.

---

### Post by drs305 on 2010-04-20
> **milleja46 said:**
> So in gparted(since i am in livecd mode) what do i enter into the free space preceding, new size, and the free space following?

It's actually easier to just drag the partition edges in the top panel to get the sizes you want. If moving the extended partition (light blue border), select the partition in the lower panel and then drag it in the top panel. The reason is that you have to get your mouse exactly on the light blue border to select it in the top - it's just easier to select it in the lower panel first.

To change the size, put the mouse near the edge and drag. To move a partition, place the mouse in the middle, then move it.

---

### Post by arrimapirate on 2010-04-20
Like drs305 said just drag the edge of the partition once in the "Resize/Edit" menu

---


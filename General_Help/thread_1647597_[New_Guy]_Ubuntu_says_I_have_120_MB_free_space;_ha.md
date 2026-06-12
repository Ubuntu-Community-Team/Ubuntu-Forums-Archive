---
title: "[New Guy] Ubuntu says I have 120 MB free space; hard drive says 300 gb"
date: 2010-12-17
forum: General Help
---

### Post by sbrown70 on 2010-12-17
Hey guys,
I'm brand new to Ubuntu so I'm not sure if this is a question y'all get a lot.
I just installed Ubuntu and I went to install updates and it tells me I only have ~120 MB of free space. But, if I go to my hard drive folder and look, it says I have over 300 GB of free space.

What's going on? Did I not partition enough space? 
Any help will be great!

Thanks,
sbrown70

---

### Post by Nath4n on 2010-12-17
Sounds like you gave Ubuntu a very small partition.  Go to System > Administration > Disk Utility > select your hard drive.  This will show you your partitions.  You may be able to install Gparted and modify your partition if that is the case.  terminal > sudo apt-get install gparted.  Hope this helps.

edit:  If you just installed it, it would be easier just reinstall and pay close attention when assigning partitions.  I recommend giving it the whole hard drive :D

---

### Post by dabl on 2010-12-17
Right -- what Nathan said.  Also, you might as well make yourself a Parted Magic Live CD:  [http://sourceforge.net/projects/partedmagic/files/partedmagic/](http://sourceforge.net/projects/partedmagic/files/partedmagic/)

Boot that, and then you can look at your hard drive, change or re-partition it, all without worrying about how to unmount it, or other issues about the Ubuntu installer.

If you repartition and reinstall Ubuntu, I recommend the Alternate Install CD, and use "Manual Partitioning" to just pick the partitions.

---

### Post by sbrown70 on 2010-12-17
I did just install it so I think I'm just going to reinstall it. I have a 500 GB Hard Drive. How much do you recommend I allot for Ubuntu? I would give it all, but I'm in school to be an engineer so I still need Windows to run MatLab and CAD software.

---

### Post by nothingspecial on 2010-12-17
Ubuntu takes about 3 gigs

If you want load of apps and stuff I`d recommend 8-10

---

### Post by Nath4n on 2010-12-17
Personally I would give it about 200 gigs if you have that much space to spare. You'll find you love Ubuntu and you'll wish you would have, trust me!

---

### Post by sbrown70 on 2010-12-17
Alright I think this question will be my last for this.
How do I go about unistalling/reinstalling ubuntu?

Thanks for being patient and helpful with me on this. I'm sure to y'all these are really basic questions, so I appreciate the help.

---

### Post by dabl on 2010-12-17
Just use GParted, and on the partition where Ubuntu was installed, right-click and "format to" ext4.  That cleans it.

---


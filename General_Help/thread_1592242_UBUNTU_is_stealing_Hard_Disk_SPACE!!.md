---
title: "UBUNTU is stealing Hard Disk SPACE!!"
date: 2010-10-10
forum: General Help
---

### Post by petrasflorin on 2010-10-10
I have a 750 GB Hard drive.
I made a 259 GB /home partition
and a 400 GB /data partition in which I keep stuff.

Total for /home is 234
total for /data is 355 

What the hell ?! Where's my space ?
This is a fresh install. Nothing new, nothing installed.

And I thought Windows system restore point reserves were thieves...

---

### Post by Coder543 on 2010-10-10
I wonder... are you certain that isn't the amount of free space? There's no way Ubuntu could take up hundreds of gigs on its own.

---

### Post by petrasflorin on 2010-10-10
Nope... not free space. Total.
The above numbers were from the top of my head, here's the real deal, still HUGE.

[http://img842.imageshack.us/img842/7789/screenshotyaa.png](http://img842.imageshack.us/img842/7789/screenshotyaa.png)

---

### Post by Coder543 on 2010-10-10
Just so you know, you've got it backwards. According to that image, it is free space. If you disagree with me, just go about your day normally and see if your disk somehow runs out of room. You have hundreds of GB of free space, Ubuntu knows what its doing. Relax. haha, and welcome to the forum.

---

### Post by Vaphell on 2010-10-10
1 GB = 1000x1000x1000 B
1 GiB = 1024x1024x1024 B = 1.073 GB

those two are mixed very often and lead to confusion
GB is smaller than GiB so you got more of them

400 GB / 1.073 = 372.5 GiB
add some overhead of the filesystem and suddenly there is no difference

also the difference between free and available exists because the system by default reserves few percent of space so the system won't get unbootable when partitions are 100% full. You can lower that percentage even to 0 (i'd leave it at 1% just to be sure), but i don't remember the command.

edit:
[http://duopetalflower.blogspot.com/2010/04/reclaiming-reserved-space-from-big.html](http://duopetalflower.blogspot.com/2010/04/reclaiming-reserved-space-from-big.html)

---

### Post by petrasflorin on 2010-10-10
It's telling me right there: "TOTAL" "FREE" "AVAILABLE"

The total is the whole size of the partition, if you do that minus free you get what is used. When I created the partitions during the install I made a 400 GiB partition.

I know one gig is 1024 MB. I'm telling you my hard drive is 748 gigs, In windows I had a 48 C , 400 D:/ and 300 E:/ - and I used almost all of it.

This isn't right, from 364 which ubuntu is showing me to 400 is 36 gigs of space that went... were ?

---

### Post by nlsthzn on 2010-10-10
> **petrasflorin said:**
> I have a 750 GB Hard drive.
I made a 259 GB /home partition
and a 400 GB /data partition in which I keep stuff.

Total for /home is 234
total for /data is 355 

What the hell ?! Where's my space ?
This is a fresh install. Nothing new, nothing installed.

And I thought Windows system restore point reserves were thieves...

Nvr mind

---

### Post by Coder543 on 2010-10-10
> **petrasflorin said:**
> It's telling me right there: "TOTAL" "FREE" "AVAILABLE"

The total is the whole size of the partition, if you do that minus free you get what is used. When I created the partitions during the install I made a 400 GiB partition.

I know one gig is 1024 MB. I'm telling you my hard drive is 748 gigs, In windows I had a 48 C , 400 D:/ and 300 E:/ - and I used almost all of it.

This isn't right, from 364 which ubuntu is showing me to 400 is 36 gigs of space that went... were ?
Formatting,  cylinder rounding, among other things, who knows exactly? there are lots of places. When you use multiple partitions you are less likely to be able to use the maximum amount of hard drive space that you possess.

---

### Post by nlsthzn on 2010-10-10
> **petrasflorin said:**
> I have a 750 GB Hard drive.
I made a 259 GB /home partition
and a 400 GB /data partition in which I keep stuff.

Total for /home is 234
total for /data is 355 

What the hell ?! Where's my space ?
This is a fresh install. Nothing new, nothing installed.

And I thought Windows system restore point reserves were thieves...

Could you run "Disk Utility" and make a screen capture of it showing the hard drive and its partitions... (I am sure there are CLI commands to do the same but I am no that well versed yet...)

---

### Post by petrasflorin on 2010-10-10
Here

[http://img232.imageshack.us/img232/6000/screenshotol.png](http://img232.imageshack.us/img232/6000/screenshotol.png)

---

### Post by Vaphell on 2010-10-10
as you can see your partitions are approx 260 and 400 **GB** but also they are approx 240 and 370 **GiB** (1.073 ratio) - substract few gigs for filesystem's own stuff and some other waste and you are pretty much left with the total usable space you got.

---

### Post by petrasflorin on 2010-10-10
Where do you see that ?
I see there 397 GB. That's my data partition mounted on /data. I go there, right click, free space: 336 although there's nothing there. - Where's the space ?

---

### Post by yetiman64 on 2010-10-10
> **petrasflorin said:**
> I have a 750 GB Hard drive.
I made a 259 GB /home partition
and a 400 GB /data partition in which I keep stuff.

Total for /home is 234
total for /data is 355 

What the hell ?! Where's my space ?
This is a fresh install. Nothing new, nothing installed.

And I thought Windows system restore point reserves were thieves...

To change the reserved space in Ubuntu on ext4 partitions you would need to use "tune2fs" command. Check [--here--]("http://ubuntuforums.org/showthread.php?t=1477293") for an example.
Reserved drive space on ext4 is about 5% by default, this would account for about 20 GB on your 400 GB partition.

---

### Post by petrasflorin on 2010-10-10
That was the first thing I did. They are all at 1% reserve. Still huge space missing.

---

### Post by nlsthzn on 2010-10-10
I remember when I switched to EXT4 on my external 320GB HDD that there was a folder called "Lost&Found" if memory serves which took up some space (but I don't know what its for :confused:)

---

### Post by petrasflorin on 2010-10-10
I had one of them in each partition, deleted them both.

---

### Post by maverick555 on 2010-10-10
[COLOR="Red"]Don't worry mate.I had a same question in mind .i have a hdd of 80 GB.I installed ubuntu left 72GB free.Then i installed xp left 75GB free.Its the filesystem of 8Gb for ubuntu and 2Gb for xp.[/COLOR]

---

### Post by Bronto on 2010-10-10
Actually the OP has a point here. Let's do some simple math based on the two reference screenshots:

(13.8 + 364.4 + 237.5) X 1024 = 630,476.80
(15 + 259 + 397) X 1.000 =  671,000.00

That's 40 GB or so missing.

@petrasflorin
Please open System Monitor, go to "File Systems" and check the "Show all filesystems" option. Revisit the "File Systems" report and look for previously unreported used space.

---

### Post by nlsthzn on 2010-10-10
> **petrasflorin said:**
> I had one of them in each partition, deleted them both.

Lol, not sure that is the wisest choice if you don't know the reason for there existence... any change in space?

> **maverick555 said:**
> [COLOR=Red]Don't worry mate.I had a  same question in mind .i have a hdd of 80 GB.I installed ubuntu left  72GB free.Then i installed xp left 75GB free.Its the filesystem of 8Gb  for ubuntu and 2Gb for xp.[/COLOR]

Whats with the red?! (Strains the eyes to read it, so many people will just skip  your posts)...

---

### Post by petrasflorin on 2010-10-10
No change in space, the lost+found were empty.
Checking the "show all filesystems" just shows me some folders of about 1g each (3 or 4 folders) from the root temp, the rest being 0 (empty or unused).

Still wondering where my space is. I mean in total there's like 80GB of space missing. From each partition, even though I set the reserve to 0%.

This isn't right. Look at my screenshots. It's not... I mean I made a 397 GiB partition and end up with 336 Available even though it's empty ?! where's the rest ?! Same goes for the /home partition.

---

### Post by Vaphell on 2010-10-11
once again:
[http://img684.imageshack.us/img684/8025/screenshot2qy.png](http://img684.imageshack.us/img684/8025/screenshot2qy.png)
partition is shown to occupy 397**GB**
397**GB** = 372**GiB**

[http://img842.imageshack.us/img842/7789/screenshotyaa.png](http://img842.imageshack.us/img842/7789/screenshotyaa.png)
your system monitor shows 364GiB total for /data, that's a 8GiB difference from calculated 372GiB, which is not much, considering that extX systems have some overhead (journaling, whatever). Consider that 8GiB reserved for filesystem use and forget about it.

[http://img842.imageshack.us/img842/7789/screenshotyaa.png](http://img842.imageshack.us/img842/7789/screenshotyaa.png)
[http://img801.imageshack.us/img801/855/screenshot1nj.png](http://img801.imageshack.us/img801/855/screenshot1nj.png)
[http://img375.imageshack.us/img375/663/screenshotow.png](http://img375.imageshack.us/img375/663/screenshotow.png)
Nautilus is bullshitting you as it confuses GB and GiB. You can clearly see that GiB value of either free space or available space from sysmonitor is the same as free space in nautilus statusbar measured in GB (though that inconsistency is puzzling, for /data it shows value of 'free', but 'available' for everything else )
bug report indicating that nautilus does in fact have problems with units
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/589217](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/589217)

difference between free and available comes from root having reserved few % of space for its use
in other words:
free = 'normal' usage + root
available = 'normal' usage
free - available = root

i think in another thread you've learned few of these, but i sum it up for greater clarity in 1 post :-)

---


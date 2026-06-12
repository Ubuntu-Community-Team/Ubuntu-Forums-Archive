---
title: "Shrinking/extending partition"
date: 2010-06-24
forum: General Help
---

### Post by bigseb on 2010-06-24
Here is screenshot showing showing my current partition in Gparted.

[ATTACH]161407[/ATTACH]

What I want to do is shrink the one (Ubuntu) and extend the other (XP) so that that they are more or less the same size. How?

Thanks

---

### Post by rickymartin on 2010-06-24
hii this article must be helpful for your problem please check out this [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by warfacegod on 2010-06-24
Make a backup of your Ubuntu *and* Windows first. Especially Windows

You'll need to do this from a LiveCD

Right click sda1> click "Resize/Move"

You'll get a new window with a "bar" image of that partition. Use the arrow on the right and drag it to the left until it's about 70 GB. Click Apply.

Do the same thing for sda2 except this time drag the arrow on the *left* of the "bar" until it fills in the emptied space. Click Apply. This second operation will probably take a good amount of time. Go do something else. Reshingle your roof, get into a fistfight with your brother-in-law, go shopping with the wife... whatever takes a long time.

---

### Post by john newbuntu on 2010-06-24
+1 on what warfacegod said.  What you want can be easily done through gparted (AFTER BOOTING FROM A liveCD).  Please read up on this gparted manual that will help you a great bit:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
Prior to moving, turn off the swap flag from the swap partition(right click swap partition).

But let me ask you this: If you shrink /dev/sda1 (Ubuntu) to say 70GB,  this will free up about 32GB.  Suppose you create an NTFS (XP) partition  on this free space, will you be happy with this setup?  So you will  have your original windows parition (40GB) + the new 32GB that will probably go as your D drive.  The only  reason I mentioned this is that you will save a lot of time in  moving/resizing another partition.

Make sure you take backups of entire Windows and Linux partitions (or at least the data in these) just to be safe as warfacegod mentioned.  Also, you could get rid of the extended partition completely and give that space to Win.  Then create a new 2GB swap primary/logical partition in the empty space that you get after reducing /dev/sda1 if you do not foresee yourself adding any more partitions.

---

### Post by bigseb on 2010-06-24
Thanks for the replies everyone. I totally forgot about booting form the live CD...

Doh!! *faceslap*

---

### Post by warfacegod on 2010-06-24
bigseb is hereby sentenced to thrice pound his face into his keyboard. Please Mark as Solved afterward.

---

### Post by bigseb on 2010-06-24
> **warfacegod said:**
> Please Mark as Solved afterward.
er... how?

---

### Post by warfacegod on 2010-06-24
Assuming, of course, everything worked out? Thread Tools.

---


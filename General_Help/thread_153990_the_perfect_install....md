---
title: "the perfect install..."
date: 2006-04-02
forum: General Help
---

### Post by frizzl on 2006-04-02
well with the impending release of dapper (pfft still 2 months :P) I am trying to plan ahead and I like to KNOW how i am going to install this thing. I currently dual boot x64 and breezy. i have been runnning it for about 1 week, so im still a noob...

when i installed breezy, i installed it to a free 80gb hdd I have. The installer partitioned it to have 1 300mb partition and the rest as root (if i remember corectly). But after reading alot, people recommend having a swap partition also.

How would i go about doing this?

What benefits could i see?

---

### Post by missmoondog on 2006-04-02
ubuntu willl automatically try to create a swap partition for you on that part of the partition. you have to tell it not to, for it not to do that and if you do that, you better have a ton of memory installed otherwise your system will run like crap. you generally want a swap partition 1.5 times bigger than the amount of installed memory. the benfit is a much faster system if you don't have a ton of memory already.

---

### Post by eriefisher on 2006-04-02
I have two hard drive 8gig and 30 gig. This is what I did.

On the 8gig- /  4gig
                  /swap 1gig
                  the rest /fat32
On the 30gig /home

Seems to work well.

eriefisher

---

### Post by sprinkles on 2006-04-02
Will you be able to upgrade from Breezy to Dapper?

---

### Post by PriceChild on 2006-04-02
i think you should be able to by adding the new repositories and doing something like 

apt-get update
apt-get dist-upgrade


I'm a noob too, but i'm almost sure it's something like that :) I wouldn't worry about it till it comes out :)

Pricey

---


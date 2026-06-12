---
title: "sharing home folder"
date: 2009-11-06
forum: General Help
---

### Post by P4man on 2009-11-06
hi,

Im about to install ubuntu moblin remix.  I got a partition ready for it and I have a separate /home partition I already use for my other  installs

Now I would like my new moblin install to use the same home partition (that part I get) but also the same **home folder**. How do I proceed? 

Must I use the same username in the moblin installer as I use in my current install? Or will doing that just create another home folder with a different name (adding a -1 or something). 

I would just try it but could  that wipe my current home folder and/or settings in it? Or should I change my home folder after installing moblin (if so, how? assuming its the same as with a normal ubuntu)

any help appreciated.

---

### Post by SuperSonic4 on 2009-11-06
First of all I've never tried this so I'm going on theory alone

> **P4man said:**
> Im about to install ubuntu moblin remix.  I got a partition ready for it and I have a separate /home partition I already use for my other  installs

Now I would like my new moblin install to use the same home partition (that part I get) but also the same **home folder**. How do I proceed? 

[list=1]
[*]Choose to partition manually
[*]Select / , swap and any others as normal
[*]For /home point it to your /home directory but **do not format** 
[/list]

> Must I use the same username in the moblin installer as I use in my current install? Or will doing that just create another home folder with a different name (adding a -1 or something). 


It shouldn't. If it does a symlink to the /home/user you want may work
```
ln -s /home/user-1 /home/user
```

[quote]I would just try it but could  that wipe my current home folder and/or settings in it? Or should I change my home folder after installing moblin (if so, how? assuming its the same as with a normal ubuntu)

any help appreciated.

Unlikely but I suggest backing up any important data as always. Or you could cp your home directory to the new user

---

### Post by alphaniner on 2009-11-06
It seems risky to me.  Even if it doesn't wipe it seems likely to mangle.  Out of curiosity, what are you hoping to achieve by doing this?

---

### Post by DeMus on 2009-11-06
I think you better start with making a full back-up of the home folder.
Then install the new OS with a separate home partition and point it to your existing home partition, WITHOUT formatting it.
Use the same username and you'll be ready.

I had Jaunty with a separate home folder. I installed Karmic (clean install) and used the same home folder. All my data was there, including flash, bookmarks, e-mail etc.
Then, because I had problems in Karmic, I installed Jaunty again and did the same. No problem what so ever.

---

### Post by P4man on 2009-11-06
> **DeMus said:**
> 
I had Jaunty with a separate home folder. I installed Karmic (clean install) and used the same home folder. All my data was there, including flash, bookmarks, e-mail etc.

You used the same username in the installer and you ended up with shared and non trashed /home/yourusername home folder? If so, thats what I want :)

And yes obviously I have a backup and I wont format it ;) but its still no fun restoring  200+GB over a 100Mbit lan if this goes south.

---

### Post by DeMus on 2009-11-06
> **P4man said:**
> You used the same username in the installer and you ended up with shared and non trashed /home/yourusername home folder? If so, thats what I want :)

And yes obviously I have a backup and I wont format it ;) but its still no fun restoring  200+GB over a 100Mbit lan if this goes south.

All I can say is it worked for me. Both times: Jaunty to Karmic and back.

---

### Post by P4man on 2009-11-06
Ok,ill give it shot tomorrow, thanks for the info.

Ubuntu Moblin remix looks kind of neat btw, at least for its intended target audience. Its unusable slow from the live session without graphics acceleration but it looks very promising for social networking netbooking addicts

---


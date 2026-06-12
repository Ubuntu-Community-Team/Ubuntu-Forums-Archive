---
title: "How to reinstall Ubuntu 10.10 partition install?"
date: 2011-03-23
forum: General Help
---

### Post by ald3n3 on 2011-03-23
How do i do reinstall ubuntu 10.10 without affecting my windows 7 os on the other partition?
I think i broke my ubuntu OS beyond repair from trying to fix my wifi card driver

---

### Post by DanneStrat on 2011-03-23
> **ald3n3 said:**
> How do i do reinstall ubuntu 10.10 without affecting my windows 7 os on the other partition?
I think i broke my ubuntu OS beyond repair from trying to fix my wifi card driver

Hi!

Do you have any important data on your

ubuntu partition? If so back it up first.


For reinstalling:

Since you already have a partition for ubuntu

you could just boot from the live cd and when

you come to the "partitioning" step choose

"manual partitioning". Now reuse your old ubuntu partition(s)

by mounting them as you had them mounted previously and

tick the "format?" box on those partitions. Then proceed

with the install. This should not affect your windows

partition but just to be on the safe side, back up all

the important data from that partition(s) as well or make

an image of it so you can restore it if disaster strikes.

Good luck.

---

### Post by nothingspecial on 2011-03-23
> **ald3n3 said:**
> 
I think i broke my ubuntu OS beyond repair from trying to fix my wifi card driver

Are you sure?

Seems to me you were just trying to install the broadcom drivers without internet access.

Did you understand the how to?

What has happened to your computer other than the wireless doesn't work?

---

### Post by ald3n3 on 2011-03-23
> **nothingspecial said:**
> Are you sure?
 
Seems to me you were just trying to install the broadcom drivers without internet access.
 
Did you understand the how to?
 
What has happened to your computer other than the wireless doesn't work?
 
Ok. i might have exaggerated a little bit. First i was trying to install it without internet access then no luck after following (or tried to) tons of tutorials.
 
Finally remembered that i can use my cellphone as internet source (duh for me) so i followed directions for installing it with internet connections and i kind of figured it out. But i think i did something wrong from trying to install the driver without internet connection because now i cant activated the driver.
 
If i go to System > Administrator > additional driver i can see the STA Broadcom driver but when i click activate it gives me an error saying "fail to check source" something along those lines.
 
So i am thinking i should just start from fresh and try to install it with internet access. Unless i can get a step by step tutorial on how to restore UBUNTU 10.10 to its fresh state.
 
All i did for my other laptop with 9.10 with bcm4312 driver is just installed bcmwl-kernel-source from livecd then DONE! but i did the samething when installed it on my new laptop Inspiron 15r with bcm4313 driver it was giving me a lot of error msg.
 
Do you suggest i should just reinstall? So basically i can't activate the STA broadcom driver

---


---
title: "Where to start"
date: 2010-01-12
forum: General Help
---

### Post by K5END on 2010-01-12
OK, so I have a PC with Ubuntu installed. I think it is 8.04.  I had the PC built with dual boot, Ubuntu and XP.

Without any training I have been able to muddle through some things, with varied success. 

Evolution email on my pc has abruptly become demon possessed and doing weird stuff. I tried to download and install Thunderbird with no success--with no success on the install part. This is frustrating. 

Really, I am just lost. (I can do Windows XP, Office, etc. just fine--when it WORKS, that is.)

I need a boot camp for Linux.

What is a good book or source to read for those like me starting from scratch?

---

### Post by tom.swartz07 on 2010-01-12
> **K5END said:**
> OK, so I have a PC with Ubuntu installed. I think it is 8.04.  I had the PC built with dual boot, Ubuntu and XP.

Without any training I have been able to muddle through some things, with varied success. 

Evolution email on my pc has abruptly become demon possessed and doing weird stuff. I tried to download and install Thunderbird with no success--with no success on the install part. This is frustrating. 

Really, I am just lost. (I can do Windows XP, Office, etc. just fine--when it WORKS, that is.)

I need a boot camp for Linux.

What is a good book or source to read for those like me starting from scratch?

[www.ubuntupocketguide.com/](www.ubuntupocketguide.com/)
perfect for you. it was made for 8.04 and 8.10 but it still works for all of the current versions.

Hope this helps!

---

### Post by zbirdman777 on 2010-01-12
How did you attempt to install thunderbird? 

If you want a gui interface then go to add/remove programs under applications at the top left and install it from there. It should just work.That's how I've installed it ever since 8.04.

or try:

sudo apt-get install thunderbird

---

### Post by K5END on 2010-01-12
> **zbirdman777 said:**
> How did you attempt to install thunderbird? 

If you want a gui interface then go to add/remove programs under applications at the top left and install it from there. It should just work.That's how I've installed it ever since 8.04.

or try:

sudo apt-get install thunderbird

There was an earlier version, but it was corrupted, I guess, and not responding. I tried to download the newer version, but it won't let me uninstall the old one. It gives me an error. 

Maybe a large hammer will help fix it. :evil:

---

### Post by K5END on 2010-01-12
> **tom.swartz07 said:**
> [www.ubuntupocketguide.com/]("http://www.ubuntupocketguide.com/")
perfect for you. it was made for 8.04 and 8.10 but it still works for all of the current versions.

Hope this helps!

Thanks

---

### Post by yoyowazzup on 2010-01-12
Remove the old Thunderbird:

sudo apt-get remove thunderbird

Install the new one:

sudo apt-get install thunderbird

Hope this works for you.

---

### Post by K5END on 2010-01-12
> **yoyowazzup said:**
> Remove the old Thunderbird:

sudo apt-get remove thunderbird

Install the new one:

sudo apt-get install thunderbird

Hope this works for you.

thanks

i get this in the terminal,

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

... whatever the foxtrot that means. 


have downloaded the help guide and reading now.

thanks for the suggestions.

---

### Post by tom.swartz07 on 2010-01-12
> **K5END said:**
> thanks

i get this in the terminal,

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

... whatever the foxtrot that means. 


have downloaded the help guide and reading now.

thanks for the suggestions.

hehe. the great thing about Linux is, if somethings broken- it tells you how to fix it.
in the terminal type what the command was:
```
dpkg --configure -a
```
also, update the system often. This might be what causes the problem here. I update twice a day- once when i turn it on, once before i turn it off. Get into that habit and you'll be problem free!

Then you could run the commands to remove and re-install thunderbird

```
sudo apt-get remove --purge thunderbird
```
Then run ```
sudo apt-get update && sudo apt-get install thunderbird
```

Should leave you high on the hog then!
Good luck!

---


---
title: "ultimate edition of Ubuntu"
date: 2011-07-08
forum: General Help
---

### Post by Dillinger86 on 2011-07-08
can some one tell me where can I find ultimate edition of Ubuntu? 
I have the ubuntu-11.04-desktop-i386 that doesn't come with the wireless drivers, and even after i installed this version on my Acer Aspire 3000 stupid laptop i have no wired or wireless connection, i did have but this lapy only has a 40 gig HDD and it was partitioned and still had XP on it so i was running out of HDD space and i couldn't figure out how to just delete XP and so i just re-installed Ubuntu and now im back to square 1.. so from searching the internet i can see that I need the ultimate edition of Ubuntu.

thanks

---

### Post by kanishkdudeja on 2011-07-08
Since you do not have access to a wired connection, you cant download just the wireless driver for your card..although that would have been the better option..

but i would still say if you could somehow get access to wired internet..that would be much better if you only need the wireless driver..

then you could find the 'additional drivers' in applications..

and install the driver for your card..

but if you cant get access to wired internet..

here are some links to the ultimate edition:

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ultimate-Edition-22863.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ultimate-Edition-22863.shtml)

[http://news.softpedia.com/news/Ubuntu-Ultimate-Edition-45644.shtml](http://news.softpedia.com/news/Ubuntu-Ultimate-Edition-45644.shtml)

---

### Post by etopsirhc on 2011-07-08
yeah ... you'r thinking of Ubuntu like Win7 , theirs one edition ,and a program to download things for it . 
but as you cant use that program to find & download what you need, u'll have to the other way . 

idk where the info for it is on the ubuntu site , but heres one i found that should at least point you in the right direction 
[http://www.planetoss.com/detail.php?id=13](http://www.planetoss.com/detail.php?id=13)

wait , their is an ultimate edition!?!?!

---

### Post by wildmanne39 on 2011-07-08
> **Dillinger86 said:**
> can some one tell me where can I find ultimate edition of Ubuntu? 
I have the ubuntu-11.04-desktop-i386 that doesn't come with the wireless drivers, and even after i installed this version on my Acer Aspire 3000 stupid laptop i have no wired or wireless connection, i did have but this lapy only has a 40 gig HDD and it was partitioned and still had XP on it so i was running out of HDD space and i couldn't figure out how to just delete XP and so i just re-installed Ubuntu and now im back to square 1.. so from searching the internet i can see that I need the ultimate edition of Ubuntu.

thanks
Hi, I found this link for you but I do not think it is the answer.
[http://ultimateedition.info/ultimate-edition-repository/](http://ultimateedition.info/ultimate-edition-repository/)
You should run these commands in terminal so we can help you get your internet working.
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
```
ifconfig
```
post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
If you do not have wired you can copy the out put to a usb drive then post them using the machine you are on now.

---

### Post by Dillinger86 on 2011-07-08
thank you guys i will do this tomorrow as its getting late now. I dont get it I installed Ubuntu last week and had wired internet access and now i don't...rite now i'm installing win 7 so i can watch a movie tonight and i will re-install Ubuntu tomorrow..I really like Ubuntu...oooh i tried debian Damn! i couldn't get it to do anything there doesn't seem to be a GUI just command line. I have to get Ubuntu going Oh and when i install Ubuntu i get this message that says my harware wont take Ubuntu and I have to use classic :(

---

### Post by Dillinger86 on 2011-07-08
> **kanishkdudeja said:**
> Since you do not have access to a wired connection, you cant download just the wireless driver for your card..although that would have been the better option..

but i would still say if you could somehow get access to wired internet..that would be much better if you only need the wireless driver..

then you could find the 'additional drivers' in applications..

and install the driver for your card..

but if you cant get access to wired internet..

here are some links to the ultimate edition:

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ultimate-Edition-22863.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ultimate-Edition-22863.shtml)

[http://news.softpedia.com/news/Ubuntu-Ultimate-Edition-45644.shtml](http://news.softpedia.com/news/Ubuntu-Ultimate-Edition-45644.shtml)you know i already did that once on that laptop and had it all working great wireless and all but i could just delete XP and having less than 3 gigs left on this stupid HDD was slowing my PC down

---


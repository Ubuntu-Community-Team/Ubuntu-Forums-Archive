---
title: "Weird battery discharge rate"
date: 2010-06-23
forum: General Help
---

### Post by Nicolice on 2010-06-23
Hello...

I'm using Ubuntu Netbook Remix 10.04 on my Acer AspireOne D260 netbook. 

One of the weird situation I'm in now is the weird discharge rate of the battery life...

For full charge, I'll get 4hours 20-50minutes remaining on my battery life, and mostly I'm using my netbook to surf the net, using wifi.

So here's some weird rate, when I click on the battery icon, it says I left 4hours 20minutes, after like 5 minutes it drops to 3hours remaining...then for few more minutes, it went back to 4hours...then went back to 4hours 15minutes...and like for few minutes again...I got 4 hours 20 minutes, left, again.

So I opened up the statistic for the battery life, and the char is like this.
[[IMG]http://img84.imageshack.us/img84/650/batterydrop.th.png[/IMG]](http://img84.imageshack.us/i/batterydrop.png/)

Uploaded with [ImageShack.us](http://imageshack.us)


Then I installed powertop, and it says like this
[[IMG]http://img194.imageshack.us/img194/2596/batterylife2.th.png[/IMG]](http://img194.imageshack.us/i/batterylife2.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Anyone know what's the cause of this problem? Is it the kernel problem or?

Also, I found something in the net, and someone stated that Ubuntu 10.04 consumes more power than Windows 7...but I prefer ubuntu as the OS for my netbook as it's lightweight, but at the same time I don't want to sacrifice my battery life...

Current kernel 
> Linux my-netbook 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux


Thanks in advance! :confused:

---

### Post by bhuvi on 2010-06-23
type this in the terminal to see if it temporarily fixes your problem:


> gconftool-2 --type=bool --set /apps/gnome-power-manager/general/use_time_for_policy false

---

### Post by Nicolice on 2010-06-23
Thanks, I'll try the steps once I got my netbook charged.

---

### Post by Nicolice on 2010-06-24
Still the same thing will happen...

---

### Post by Nicolice on 2010-06-24
*bump

even using LAN, disabled wifi...the battery rate also will act like that... from 6 hours, then -2 hours become 4hours...then 6 hours back, and the graph shows the same as in the first post

---

### Post by bhuvi on 2010-06-25
your powertop output seems to be normal, this must be a problem with the gnome-power-manager and its associated software. I think you should file a bug on this, and use any other software available in the repository for battery monitoring

---

### Post by Nicolice on 2010-06-25
Thanks for the reply, I'll try file a bug about it afterward.

And also, is there any other method to know how much time left for my battery? thanks!

---


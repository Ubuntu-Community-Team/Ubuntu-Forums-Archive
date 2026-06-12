---
title: "How do I set up my computer to do this."
date: 2010-10-12
forum: General Help
---

### Post by Cammaaron on 2010-10-12
There would be some kids staying over and I don't want them to use my account.
So I am making accounts for them each on my Linux computer if they wish to use them.
 
However each of them have different times they are allowed to be on the computer and one of them is not allowed to get on the internet.
 
I need to know how I can make a different firewall rules for each person that would get on, and I need to know how I can prevent someone form logging in at a certain time.
 
PS: I am using Ubuntu 10.04.

---

### Post by Cammaaron on 2010-10-13
I bump

---

### Post by nothingspecial on 2010-10-13
In 10.04 there was a time control daemon called timekpr

I can`t seem to find it on 10.10.

There seems to be something called nanny, but I haven`t played with it yet. It is supposed to control both time and internet usage.

Hope that points you in the right direction

---

### Post by JustinR on 2010-10-13
> **nothingspecial said:**
> In 10.04 there was a time control daemon called timekpr

I can`t seem to find it on 10.10.

There seems to be something called nanny, but I haven`t played with it yet. It is supposed to control both time and internet usage.

Hope that points you in the right direction

Try GNOME Nanny.
It works great for me:
[http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)

---

### Post by nothingspecial on 2010-10-13
> **JustinR said:**
> Try GNOME Nanny.
It works great for me:
[http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)


Ha ha ha :evil:

Mean old dad strikes again.

That was easy to set up.

---

### Post by roggenschrotbrot on 2010-10-13
never used gnome-nanny, so i can't really comment on it, but i guess it is the way to go for restricting internet access by filters. for those who aren't allowed to access the net setting the user/group rights would be the nicer way to go though.

for restricting the usage to set times for the ease of use (as i wouldn't want to install or learn additional tools for a single-time use) i'd run a background script on startup which would kill the current session if the current time is not in the allowed timeframe.

edit: should have read the description of gnome-nanny before i posted :p

---


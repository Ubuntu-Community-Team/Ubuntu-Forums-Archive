---
title: "No Laughing Please  ;)"
date: 2009-09-29
forum: General Help
---

### Post by Ghot on 2009-09-29
Does Ubuntu 8.10 (patched up to date) need a Firewall....does it have one built in?  IF it does need one, what recommendations?

---

### Post by misfitpierce on 2009-09-29
They all have IPTables built in which is like a firewall... for easy way to configure it simple get firestarter!

terminal: sudo apt-get install firestarter or find in add/remove programs.

---

### Post by Ghot on 2009-09-29
thx very much...bean to you  :)

---

### Post by jflaker on 2009-09-29
> **Ghot said:**
> Does Ubuntu 8.10 (patched up to date) need a Firewall....does it have one built in?  IF it does need one, what recommendations?

What are your expectations?



The only reason you would need a firewall is because you have known services listening and answering.  Ubuntu and most other Linux distribution, have only the necessary ports open to the outside...so the short answer is no, you don't....

The first line of defense is a hardware firewall (router or an appliance like IPCop) at your head end to the internet...that will stop 99% of the uninvited inbound traffic trying to talk to your systems.

---

### Post by wojox on 2009-09-29
ufw is installed but not on by default. You can use gufw for a gui.

[https://help.ubuntu.com/8.10/serverguide/C/firewall.html](https://help.ubuntu.com/8.10/serverguide/C/firewall.html)

---

### Post by Ghot on 2009-09-29
> **jflaker said:**
> What are your expectations?



The only reason you would need a firewall is because you have known services listening and answering.  Ubuntu and most other Linux distribution, have only the necessary ports open to the outside...so the short answer is no, you don't....

The first line of defense is a hardware firewall (router or an appliance like IPCop) at your head end to the internet...that will stop 99% of the uninvited inbound traffic trying to talk to your systems.

This is not MY laptop I'm installing Ubuntu on...it is for a 29year old crazy woman....who does sort of a willy nilly shop online thing  :/

...and yes  one or two times in my 52 years I've heard of routers  ;)  I'm just new to Linux  bro....I'm not totally daft  :)

---

### Post by jflaker on 2009-09-29
> **Ghot said:**
> This is not MY laptop I'm installing Ubuntu on...it is for a 29year old crazy woman....who does sort of a willy nilly shop online thing  :/

...and yes  one or two times in my 52 years I've heard of routers  ;)  I'm just new to Linux  bro....I'm not totally daft  :)

Actually, I was suggesting you can put a router or an appliance like IPCop (IPCop is more hardened compared to a router) as a firewall...Given the situation you mentioned, a router would do as IPCop would be way overkill.

---

### Post by Ghot on 2009-09-29
I know that bro...Although I normally use Windows  (...ducks quickly) this person I'm fixing the laptop for, shouldn't even be allowed near the internet...that was the gist of my concern...she does have a router already, and I'll slap Firestarter on this install as well.  That should hold her for a while.  ;)

---

### Post by Chriswilkie on 2009-09-29
there Should be one built in my memory is a little fuzzy but go to add/remove software and search for a firewall controller if your build does not already  have one in your prefrences

---

### Post by Ghot on 2009-09-29
> **Chriswilkie said:**
> there Should be one built in my memory is a little fuzzy but go to add/remove software and search for a firewall controller if your build does not already  have one in your prefrences

yea there is as shown at the link in the above post...it's called the ufw....but as i said...although I am willing to learn how to use it properly...the person who owns this laptop isn't  :)

This is probably the 15th time we've "fixed" her comp....so we got smarter and chose Ubuntu this time.

By the way...Ubuntu sure has come a long way since 5.10   ;)

Good work guys and gals  ;)

P.S.  This was soooo easy...I may just start dual booting XP Pro and Ubuntu...then you'll get a chance to fill some coffee cups  ;)


Thx for all your help....consider this topic ....resolved   :)

---


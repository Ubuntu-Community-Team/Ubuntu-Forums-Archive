---
title: "any programs to block all websites except ones i choose?"
date: 2009-10-21
forum: General Help
---

### Post by goosemontana on 2009-10-21
My mom is buying a netbook for christmas for a mentally disabled person she takes care of. I suggested her to buy a dell netbook with an ssd drive(in case it gets dropped)and ubuntu preinstalled because i thought that without root access the person wouldnt be able to mess as much up as he could in windows(i should be able to fix any problems that come up if he does manage to mess something up. Now i need something to block the whole internet except for safe websites that my mom will allow. I've heard of something called privoxy but I've never used it before. i need to know if there is something i can use for this or if someone knows of another distro aimed at keeping children safe online or something. By the way this is on ubuntu 8.04 if that matters 

thanks

---

### Post by diesch on 2009-10-21
Privoxy is more for filtering ads and thinks like that. DansGuardian is often used for blocking web sites, see 
[https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian) and 
[https://help.ubuntu.com/community/Servers/DansGuardian](https://help.ubuntu.com/community/Servers/DansGuardian)

---

### Post by lovinglinux on 2009-10-21
You could use [moblock](http://moblock-deb.sourceforge.net/) for blocking IP addresses. Instead of using a default blocklist, create your own list with the range 0.0.0.0-255.255.255.255, which would block the entire Internet, then add the IP of the sites you want to allow to moblock's allow list.

Your mother will probably find mobloquer gui easier when it comes to adding new allowed addresses.

---

### Post by darco on 2009-10-22
[OpenDNS]("http://www.opendns.com/") is great web filtering program...plus you get a fast dns server....


darco

---

### Post by diesch on 2009-10-22
IP and DNS based filtering have the disadvantage taht you con only filter/allow whole domains, but not single pages, and it's usually a bit difficult the set up a page explaining what's going on for blocked pages.

IP bases filtering doesn't work well with servers hosting multiple domains or pages moving to another server.

---

### Post by darco on 2009-10-22
> **diesch said:**
> IP and DNS based filtering have the disadvantage taht you con only filter/allow whole domains, but not single pages, and it's usually a bit difficult the set up a page explaining what's going on for blocked pages.

IP bases filtering doesn't work well with servers hosting multiple domains or pages moving to another server.

True about DNS filtering only whole domains but I dont understand your comment about "set up a page explaining ....". OpenDNS does that automatically.
And did I mention OpenDNS is free? So the OP can try it himself and see if it works for him. We are not looking for overkill here as he mentions it is for a disabled person.

darco

---

### Post by diesch on 2009-10-22
> **darco said:**
> True about DNS filtering only whole domains but I dont understand your comment about "set up a page explaining ....". OpenDNS does that automatically.


It may be better if you can create a page yourself so you can give your own explanations, or just display some picture, or whatever you want.

[quote=darco;8143980
And did I mention OpenDNS is free? So the OP can try it himself and see if it works for him. We are not looking for overkill here as he mentions it is for a disabled person.
darco[/quote]

I wouldn't make much differences between a disabled person and any other person without technical knowledge here.

---

### Post by goosemontana on 2009-10-24
ok thanks everyone the computer should be coming today so ill try all of these out. thanks again!

---


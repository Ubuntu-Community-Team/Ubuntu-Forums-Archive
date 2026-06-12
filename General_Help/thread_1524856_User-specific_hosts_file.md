---
title: "User-specific hosts file?"
date: 2010-07-05
forum: General Help
---

### Post by ferret man on 2010-07-05
I share a computer with my brother. It runs Lucid Lynx. I want to add an entry to the hosts file that will affect him negatively. Is there a way I can add the entry, without it affecting him, like, is there a user-specific hosts file?

---

### Post by ferret man on 2010-07-06
Bump

---

### Post by pricetech on 2010-07-06
I'm not aware of a user specific hosts, but you could create two copies, one named after you and the other named after your brother, and then a local script to swap them according to who logs in.

Redneck solution, but it would work.

---

### Post by bodhi.zazen on 2010-07-06
What are you wanting to do exactly ? Perhaps there is a better solution.

---

### Post by ferret man on 2010-07-06
I want to add an entry to my hosts file that redirects facebook to my localhost. My brother, however, often uses facebook, so he'll scream if I do this. Right now, I'm running the "redneck solution". ;P

---

### Post by WorMzy on 2010-07-06
You could just make your default index.html page look like a "Sorry, Facebook is down for maintenance. Please check back later." page, then he'll never need to know. ;)

---

### Post by Samulus on 2010-07-06
It would be funnier if the message was: Sorry, Facebook is down for maintence, forever. Or something similar to that extent ;-)

---

### Post by ferret man on 2010-07-06
> **WorMzy said:**
> You could just make your default index.html page look like a "Sorry, Facebook is down for maintenance. Please check back later." page, then he'll never need to know. ;)
Ooh, I like that! hehehe...

EDIT: The forever part IS a lot funnier. :P I'm writing up the web page right now. xD

---

### Post by bodhi.zazen on 2010-07-06
Use iptables

iptables -A OUTPUT -m owner --uid-owner your_user_name -d facebook_ip_address -j DROP

---

### Post by ferret man on 2010-07-06
How does one go about reversing something like this, for future reference?

---

### Post by bodhi.zazen on 2010-07-06
> **ferret man said:**
> How does one go about reversing something like this, for future reference?

To remove that rule:

iptables -D OUTPUT -m owner --uid-owner your_user_name -d  facebook_ip_address -j DROP

You will need to set up iptables after a reboot as well. Either add the appropriate command to /etc/rc.local or use iptables-save

See also : 

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by ferret man on 2010-07-13
By the way, remember that prank? I forgot to upload the html. It's real  ugly code, and probably a little bloated, but I'm happy with my work, as  this is the first time I have EVER used HTML.

---

### Post by WorMzy on 2010-07-13
If you enjoyed making it, then check out [w3schools]("http://www.w3schools.com/"), it's a great place to learn all the basics of (X)HTML, Javascript, Cascading Style Sheets, and other web based stuff. :)

---

### Post by ferret man on 2010-07-13
Thanks so much! I just realized today that HTML is kind of fun, and I was looking for a reference. :D

---


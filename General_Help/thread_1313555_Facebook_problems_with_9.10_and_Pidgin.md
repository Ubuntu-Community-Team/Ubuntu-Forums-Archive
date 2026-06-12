---
title: "Facebook problems with 9.10 and Pidgin"
date: 2009-11-03
forum: General Help
---

### Post by docjohnson on 2009-11-03
I recently upgraded to 9.10 and and opened firefox to try to check Facebook and while loading Facebook, firefox crashed. I tried again, but the same happened. It kept on happening, so I tried uninstalling Firefox and reinstalling, but it's still not working. Also, when I try using Pidgin to use Facebook Chat it says it's unable to connect to the chat server. Is there any way at all I can fix this?

---

### Post by JeSTeR7 on 2009-11-03
I think Facebook must have changed something recently, because I've been using Karmic for a month, yet just today the Facebook plugin will no longer connect.

---

### Post by polki@mac.com on 2009-11-04
Facebook, does anyone remember the name of the company who owns it? :lolflag:

---

### Post by t0p on 2009-11-04
> **polki@mac.com said:**
> Facebook, does anyone remember the name of the company who owns it? :lolflag:
According to [Wikipedia]("http://en.wikipedia.org/wiki/Facebook"):

> **Facebook** is a global [social networking]("http://en.wikipedia.org/wiki/Social_network_service") website that is operated and [privately owned]("http://en.wikipedia.org/wiki/Privately_held_company") by Facebook, Inc.

---

### Post by cpwins on 2009-11-04
> **JeSTeR7 said:**
> I think Facebook must have changed something recently, because I've been using Karmic for a month, yet just today the Facebook plugin will no longer connect.

You can get the latest .deb (1.62) from here:

[http://code.google.com/p/pidgin-facebookchat/downloads/list](http://code.google.com/p/pidgin-facebookchat/downloads/list)

This solved my problem.

---

### Post by guriinii on 2009-11-04
> **cpwins said:**
> You can get the latest .deb (1.62) from here:

[http://code.google.com/p/pidgin-facebookchat/downloads/list](http://code.google.com/p/pidgin-facebookchat/downloads/list)

This solved my problem.

Thank you!! Worked a treat :D

---

### Post by Shpongle on 2009-11-12
thanks man!!!!

---

### Post by kangyu29 on 2009-12-18
> **cpwins said:**
> You can get the latest .deb (1.62) from here:

[http://code.google.com/p/pidgin-facebookchat/downloads/list](http://code.google.com/p/pidgin-facebookchat/downloads/list)

This solved my problem.

works great for me too, thanks.

---

### Post by lukashjanssen on 2010-06-23
> **cpwins said:**
> You can get the latest .deb (1.62) from here:

[http://code.google.com/p/pidgin-facebookchat/downloads/list](http://code.google.com/p/pidgin-facebookchat/downloads/list)

This solved my problem.

I did this and I think it WOULD work, except when I run the .deb, it says: "Error: Dependency is not satisfiable: libjson-glib-1.0-0 (>= 0.7.6)"

So I ```
sudo apt-get install libjson-glib-1.0-0
``` which it DID do, but the message is still coming up when I run the .deb

What am I missing?

---

### Post by lukashjanssen on 2010-06-23
I even downloaded libjson-glib-1.0-0-dbg_0.6.2-3_i386.deb in hopes in hopes that it might actually install that way, but it didn't change anything.

---


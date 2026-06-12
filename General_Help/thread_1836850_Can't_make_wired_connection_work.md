---
title: "Can't make wired connection work"
date: 2011-08-31
forum: General Help
---

### Post by rmeng on 2011-08-31
hey everybody.

I've just installed the 11.04 version and i have a trouble making the wired internet work... The computer is connected to the router in the usual way (with wire).

First it just couldn't connect...

After setting ipv4 settings manually, i've started seeing the computer in the list of connections... but it still didn't work.

I had a similar problem on the same comp when I've installed windows 7... It was solved by setting duplex/speed to 10mbps/full duplex (i am surprised that it what made it work but still)... now i see that my connection is at 100 mbps/full duplex when i play with lshw... I guess that changing speed to 10 would work... however after googling a bit i've learned that i need ethtool to make those changes on ubunto... i am unable to get ethtool on that computer because it's not connected to the internet. :) 

now - does anyone has an idea how to change speed and duplex without ethtool?
or what i need to do install ethtool without internet connection? (it's not included in the ubuntu standard package)

thanks

---

### Post by rmeng on 2011-08-31
to the mods - i've opened this thread on Networking & Wireless... feel free to delete/close this thread. if anyone has an aswer please answer here[http://ubuntuforums.org/showthread.php?p=11206918#post11206918]("http://ubuntuforums.org/showthread.php?p=11206918#post11206918")

---


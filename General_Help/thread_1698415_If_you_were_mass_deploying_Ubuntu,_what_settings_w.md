---
title: "If you were mass deploying Ubuntu, what settings would you change?"
date: 2011-03-02
forum: General Help
---

### Post by Roasted on 2011-03-02
There may be an opportunity in the near future to deploy a handful of Ubuntu systems to see how they do in our environment. I work for a school district, so we're around students who like to click on things they shouldn't. I'm curious if anybody else has or if anybody has any idea on anything in particular to lock or block out.

I'm setting their default profile using the /etc/skel method, by changing the background to something more fitting that symbolizes our school and also changing a few things in the menu. I don't want games listed or software center listed, as I know they cannot install anything I don't want anyone wasting time browsing through the long list of applications that are available.

I'm also making sure I block out usage to network manager, seeing as though network manager has a checkbox for "show key" on the wireless network.

I also made sure I selected "Available To All Users" for all network SSID's. This allows the machine to connect RIGHT away when it comes to the login screen. That allows the machine to connect to our domain and when users log in via their domain name, it can successfully authenticate to our Windows server and then allow them to log in.

I think I'll find more as I run into situations where I need to better manage these desktops, but I'm trying to cover all grounds as much as possible from day one. Does anybody have any suggestions?

---

### Post by Roasted on 2011-03-08
Nadda? Hasn't anybody deployed Ubuntu into a production environment?

---

### Post by Spyderkid on 2011-03-08
look here possibly...

[http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CBoQFjAA&url=https%3A%2F%2Flists.ubuntu.com%2Farchives%2Fubuntu-education%2F2010-October%2F000415.html&ei=wX52TaebCYe3hQfavqT9Bg&usg=AFQjCNGhf43k_HQ-bn7Dtd7kcttdFW1YuA](http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CBoQFjAA&url=https%3A%2F%2Flists.ubuntu.com%2Farchives%2Fubuntu-education%2F2010-October%2F000415.html&ei=wX52TaebCYe3hQfavqT9Bg&usg=AFQjCNGhf43k_HQ-bn7Dtd7kcttdFW1YuA)

---


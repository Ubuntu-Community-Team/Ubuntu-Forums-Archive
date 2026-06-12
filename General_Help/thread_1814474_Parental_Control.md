---
title: "Parental Control"
date: 2011-07-29
forum: General Help
---

### Post by geek2330 on 2011-07-29
with ubuntu 11.04, can you setup a time for my kids account so i can limit their time on the computer and get logged out automatically?

---

### Post by Megaptera on 2011-07-29
Have you had a look at Gnome Nanny?

[http://www.webupd8.org/2010/03/gnome-nanny-parental-control-takes-care.html](http://www.webupd8.org/2010/03/gnome-nanny-parental-control-takes-care.html)

Quote "Gnome Nanny is an easy way to control what your kids are doing in the computer, under Linux. You can limit how much time a day each one of them is browsing the web, chatting or doing email. You can also decide at which times of the day the can do this things. Gnome Nanny filters what web pages are seen by each user, so you can block all undesirable webs and have your kids enjoy the internet with ease of mind, no more worries!"

---

### Post by Habitual on 2011-07-29
[http://forums.linuxmint.com/viewtopic.php?f=188&t=77687](http://forums.linuxmint.com/viewtopic.php?f=188&t=77687)
describes a process you can implement.

---

### Post by geek2330 on 2011-07-29
thanks guys.

---

### Post by nothingspecial on 2011-07-29
Gnome Nanny is buggy and doesn't work.

timekpr does

[https://launchpad.net/timekpr](https://launchpad.net/timekpr)

for the moment.

However, sadly development has ceased. My kids are delighted.

---

### Post by bodhi.zazen on 2011-07-29
iptables will do this as well ;)

Use the OUTPUT table and match according to time and user.

[http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips)

The advantage of iptables, no additional applications required, the disadvantage no graphical interface.

---


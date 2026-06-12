---
title: "ubuntu as a internet gateway router"
date: 2009-12-24
forum: General Help
---

### Post by windows_dummies on 2009-12-24
hy, all...

i have ubuntu 9.10 desktop i386 version that i need to turn my box into an internet gateway router...

i am using old desktop pentium 3 800mhz, a HSPDA usb modem (bandluxe c120)and a wireless router..

configuration: 
internet > hspda usb modem > ubuntu box > lan card > wireless router > other networked pc

i need to connect my ubuntu to the internet and act as a internet gateway so that my other computer will get internet connection thru my wireless router

things shud be done like this, my ubuntu box should be auto-connect to internet once boot up without having to switching ON my monitor and need no requirement to activate hspda modem thru loggin in to user account.. 

if you have any suggestion how to make this working, please let me know... 

Wish You All A Happy Merry Christmas... Have A Nice Weekend and Happy New Year.. :)

---

### Post by sdennie on 2009-12-25
This looks like the general idea: [http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283).  The tutorial is a few years old but, the info looks correct.

---

### Post by spiky001 on 2009-12-25
Hi I have a very similar set up not using wireless tho ( hope to soon but need to find router) ine works fine through wire have set up vnc to access main pc to change things if need be would like to know how u get on

---

### Post by fragos on 2009-12-25
Wireless routers I'm familiar with already do that for you without going through the Ubuntu box. The router will have some wired connectors, usually 4. Any computer connected wired or wireless shares in the Internet connection. If all connect with DCHP, the default, they will be assigned a special local IP address to use.

---


---
title: "Suddenly Slow Boot help"
date: 2009-07-11
forum: General Help
---

### Post by mykrob on 2009-07-11
Running 9.04 on my Compaq CQ602-215 laptop. All of a sudden, my booting is much slower. It boots from cold start to login screen just fine. But after logging in, i now have about a 20+ second delay. I get a black screen with a mouse cursor that I can move, I hear the login sound. After about 20 seconds or more, the desktop renders and I can use the system.

Not too big of a deal, its just it didnt use to do this, and I wonder what is wrong.

How to begin troubleshooting?

---

### Post by mano cazalet on 2009-07-11
install bootchart to see where it hangs

sudo apt-get install bootchart

it will place a png image of all the boot process in /var/log/bootchart

---

### Post by mykrob on 2009-07-11
Doesnt make much sense to me, but here it is:

---

### Post by mykrob on 2009-07-11
Does this show what happens after GDM?

---

### Post by Buttons840 on 2009-09-07
[http://www.youtube.com/watch?v=Az4dQxhtEKs](http://www.youtube.com/watch?v=Az4dQxhtEKs)

I had the same problem at one point.  The frustrating part is there seems to be no reason for it to start.  I have not installed anything new or made any changes.  I have done system updates though.

Having searched a few threads on the forum I have found no solutions except to reinstall Ubuntu.

---


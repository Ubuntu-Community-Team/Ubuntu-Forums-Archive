---
title: "help needed: windows as a virtual machine"
date: 2010-06-23
forum: General Help
---

### Post by yilin on 2010-06-23
I have some software runs only on windows. And I'd like to try install windows as a virtual machine inside of ubuntu.

Can anyone give me some help to start with?
A step by step guide will be very nice but any inputs are appreciated.

Thanks

---

### Post by sanderd17 on 2010-06-23
If you work with vritualbox, everything will be simple (I didn't use another thing so I cant compare, I just know Virtualbox works great)

Install Virtualbox from the software center or repo's
Start it
create a new virtual machine
if you select a windows xp or vista or seven, optimal settings will be chosen
when you start it the first time, you'll have to choose a cd to boot from (this can be a physical drive or an iso)
when it's installed (after a few reboots) you can run windows and install things in it.

Please chose windows xp if you have less than 4GB ram. Vista and 7 use to much ram to run well together with ubuntu.

---

### Post by howefield on 2010-06-23
Go to [http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV) and watch the short instructional videos.

Then come back and ask any questions that you might have.

---

### Post by passonno on 2010-06-23
[Here's]("http://www.knowliz.com/2009/01/install-windows-7-with-ubuntu-using.html") a good start.  Be warned,  though,  the website itself is terrifyingly ugly.

---

### Post by howefield on 2010-06-23
> **sanderd17 said:**
> Install Virtualbox from the software center or repo's...

Just to mention that there are two versions of Virtualbox, the one in the Ubuntu repository is the OSE "Open Source Edition", the other is the PUEL version, Personal and Evaluation Licence and is downloadable from the Virtualbox website, the most significant difference is that the PUEL version has USB support.

So if you want to use USB devices in your virtual machine, you don't want the OSE version.

---


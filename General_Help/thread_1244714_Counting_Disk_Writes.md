---
title: "Counting Disk Writes"
date: 2009-08-19
forum: General Help
---

### Post by adam.ec on 2009-08-19
I'm currently doing some research for my MSc and need to count the number of times a hard drive writes to various specific directories during an average user session. It would be nice to have a simple output such as this:

var   320
tmp  1600
usr   6

I don't know if there is a program that does this already or even just a simple script I can install on the machine. Can anybody help me out here?

Thank you

---

### Post by pizmooz on 2009-08-19
hey, the 'sysstat' package contains a program called 'iostat' which allows you to see these kind of diskstats

also if you are doing this for research you might want to poke around in '/sys' to get raw byte counts

---

### Post by pizmooz on 2009-08-19
sorry I didn't read your post well enough.  if you want to find out how many writes in different branches of the fs.  you should be able to write a script which collates the output of 'lsof'.

---

### Post by adam.ec on 2009-08-19
Thanks man, really quick response too. Looks like what I need pizmooz. Thanks again.

---


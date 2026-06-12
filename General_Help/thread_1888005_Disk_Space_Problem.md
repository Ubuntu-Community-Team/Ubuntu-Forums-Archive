---
title: "Disk Space Problem"
date: 2011-11-28
forum: General Help
---

### Post by madzombie on 2011-11-28
Hello,
I use ubuntu 11.10 x64. But I experience interesting problem.
I don't usually shutdown ubuntu for several days.
I check disk space and available disk space seems 118 GB.
But after than, After I had restarted system, I look available disk space is 266 GB.

I experience two time. 
What is wrong ?

---

### Post by ajgreeny on 2011-11-28
> **madzombie said:**
> Hello,
I use ubuntu 11.10 x64. But I experience interesting problem.
I don't usually shutdown ubuntu for several days.
I check disk space and available disk space seems 118 GB.
But after than, After I had restarted system, I look available disk space is 266 GB.

I experience two time. 
What is wrong ?
There could be some log files in /var that are growing exponentially.  Right click on /var and choose Properties to see how large it has grown.  As an example, mine is about 700MB at the moment, of which 500MB is the /var/cache/apt/archives folder with all downloaded packages in it.  I find it hard to believe that your /var could grow as large as 140GB or more, as suggested by your figures, but something is eating the space.

Try disk-usage-analyser to find out what is taking all that space, but be aware of that DUA shows the top folder of your search, whether home, or root, or even /var, as 100% used, which can confuse people.  It is the size that matters, not the %age use.

---

### Post by madzombie on 2011-11-28
ajgreeny thanks for reply.
When I checked disk space via disk-usage-analyse, I was seeing /home directory is used as  90-99% usage.

---

### Post by ajgreeny on 2011-11-28
If you now click on the "Scan home" button, you should see which, if any of the folders in your home are using all the space, or if it is some file in the root of your home such as **.xsession-errors** which has grown so large.

---

### Post by Bobhuber on 2011-11-28
Take a look in /var/log for a uvcdynctrl file that has gotten out of hand. If so remove the uvcdynctrl and 
uvcdynctrl-data packages via the synaptic package manager. Shouldn't hurt a thing unless you are developing web cam apps.

---

### Post by madzombie on 2011-12-01
My system uptime is 64 hours. And I checked disk usage.
.xession-errors seems as 10 GB

---


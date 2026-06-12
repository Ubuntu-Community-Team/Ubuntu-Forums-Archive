---
title: "How do I UNDERclock my laptop.."
date: 2011-06-16
forum: General Help
---

### Post by robofighter on 2011-06-16
I have a Dell Inspiron Duo and I have a dual core Intel atom N550 with multithreading and speedstep (checked bios, its enabled)

---

### Post by underdog512 on 2011-06-16
So..... What is the question here exactly?

---

### Post by FormatSeize on 2011-06-16
It seems that the user wants to under-clock his processor. Though I can not even begin to dream why someone would want to go about doing this. 
 
I read somewhere about a script out there called xbench that will allow you to over-clock, but I'm not sure whether it will let you go the opposite way. Additionally, the guy that said that it worked for him also mentioned that he had to make some script modifications, and I don't know exactly what that involved.
 
I also read somewhere that you can edit your /etc/init.d/cpufrequtils and set values for the MAX_SPEED and MIN_SPEED. And to find the frequencies:
```
cat /sys/devices/system/cup/cpu0/scaling_available_frequencies
```

---

### Post by robofighter on 2011-06-16
Perhaps I should have explained more.

I am trying to extend my battery life, I noticed that my laptop battery lasts longer in Windows then in Linux.I think it is because in Power Manger in Windows I have my CPU at low when at battery power.

I heard that functionality works because of the speedstep functionality in the CPU that allows you to adjust how fast the CPU is through software.

I also heard that speedstep support has been intergrated in the Linux kernel on version 2.6. But what I don't know is how to access it, so I can slow the processor down.

---

### Post by robofighter on 2011-06-20
bump

---

### Post by pqwoerituytrueiwoq on 2011-06-20
change ondemand to conservative it will help a little
```
gksudo gedit /etc/init.d/ondemand
```line 27
also take a look at the cpu scaling applet (1 applet per core)

---


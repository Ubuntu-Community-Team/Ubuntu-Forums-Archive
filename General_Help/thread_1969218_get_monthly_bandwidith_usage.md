---
title: "get monthly bandwidith usage"
date: 2012-04-29
forum: General Help
---

### Post by Unguidedone on 2012-04-29
I need a program to log my bandwidth in and bandwidth out, as i dont want to go over my isp cap of 250 gig
I tryed using screenlets and it failed to keep accurate records.
any advice?

---

### Post by CharlesA on 2012-04-29
If you don't reboot that often, you can always use ifconfig to check how much traffic in/out, but that will count LAN traffic in addition to WAN traffic.

Check here:
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by matt_symes on 2012-04-29
Hi CharlesA,

@OP. I use vnstat. It's a command line utility.

```
sudo apt-get install vnstat
```You can get daily, weekly and monthly usage.
```

matthew@matthew-Aspire-7540 ~ % vnstat -m 

 eth0  /  monthly

       month        rx      |     tx      |    total    |   avg. rate
    ------------------------+-------------+-------------+---------------
      Mar '12     76.75 GiB |   72.19 GiB |  148.95 GiB |  466.49 kbit/s
      Apr '12     34.97 GiB |   20.68 GiB |   55.65 GiB |  186.05 kbit/s
    ------------------------+-------------+-------------+---------------
    estimated     36.12 GiB |   21.36 GiB |   57.49 GiB |
matthew@matthew-Aspire-7540 ~ % 
```
> 
but that will count LAN traffic in addition to WAN traffic.

This may be your problem and may also affect vnstat. Does you router display traffic over the WAN ?

Kind regards

---

### Post by pqwoerituytrueiwoq on 2012-04-29
if you can do this with your router you should do it that way so you can get a total for all devices (my router has tomato firmware on it)
[http://i.imgur.com/82Vjg.png](http://i.imgur.com/82Vjg.png)

if you need to do it in ubuntu you could make a shutdown script to save get the usage from a log file (that you would create) and add the current sessions usage to than save it in the log file and have a cron job check the file every 10 min or so and have it alter you if you are getting close
this will include local net usage also like your file server full of movies you watch, for example

---

### Post by CharlesA on 2012-04-29
Hey Matt,

Thanks for the info on vnstat. I might have to take a look at that to see how much bandwidth my server is using each month.

Thanks!

---

### Post by kostkon on 2012-04-29
For a user friendly application, check [NTM]("http://www.webupd8.org/2011/10/network-traffic-monitor-ntm-for.html").

---

### Post by Unguidedone on 2012-04-29
thanks for all the help with this monster of a problem :D
[FONT=monospace]The install of vnstat failed on my system.

Getting total network traffic from the router is a great idea but I have no idea how to add [/FONT]tomato firmware to a cisco router.  So thanks for the idea ill need to continue my research :D

*added ntm, but it does not save data when the computer is restarted

oddly enough I found the answer in the comments here:
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)   "knemo"  is just sooo awesome

I have to start next month right so i don't blow my cap (850 gig on a 250 gig plan) 
But on the bright side i will be getting "business internet" aka uncapped awesome-sauce.  Why should file torrenting be so scary lol  living in the usa is scary sometimes. 
This is what i want to think of :   [https://www.youtube.com/watch?v=2I1FfJ9TPTY](https://www.youtube.com/watch?v=2I1FfJ9TPTY)
 One of the few things that makes me happy is filling my 5 2tb drives with movies/shows/music/ebooks/audiobooks lol....

(mark as "solved")

---

### Post by lisati on 2012-04-29
> **Unguidedone said:**
> (mark as "solved")
To do that you can use the "Thread tools" drop-down menu near the top of the page.

---

### Post by CharlesA on 2012-04-29
Did you get any errors when you tried to install vnstat?

---

### Post by pqwoerituytrueiwoq on 2012-04-29
it really depends on the router on if you can put tomato on it there are not many that can use it, yours may be able to use dd-rwt on yours which i have read is alot more powerful but a bit more advanced they way i see it tomato works for my router and it has everything i need (though ipv6 would be nice)

---


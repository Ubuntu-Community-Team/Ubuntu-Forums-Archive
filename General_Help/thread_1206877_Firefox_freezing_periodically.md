---
title: "Firefox freezing periodically"
date: 2009-07-07
forum: General Help
---

### Post by allspiritseve on 2009-07-07
I've looked around a little, but nobody seems to be having the same issue. Basically, every once in a while firefox will completely freeze for a minute or so, and then return to normal. I have started it in safe mode and the same thing happens. Can somebody help me isolate the problem? I'm running intrepid on a Dell Inspiron 6400 with Firefox 3.0.11.

---

### Post by lovinglinux on 2009-07-07
I still have the same problem on another machine running Intrepid. I thought it was a problem with pulseaudio, but while completely removing it reduced the problem, it didn't fix it.

I recommend reading the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by allspiritseve on 2009-07-10
Hmm... I'm actually wondering if this is actually an issue with Ubuntu rather than firefox. Once in a while the whole computer will freeze for a minute or so. What can I do to figure out what's causing it? I've tried to get the System Monitor open in time, it generally seems like memory usage is pretty high (1.8GB/2GB) but no single program is using an extraordinary amount.

---

### Post by philinux on 2009-07-10
Use the command 

```
top
```

see whats using cpu and mem.

---

### Post by lovinglinux on 2009-07-10
> **allspiritseve said:**
> Hmm... I'm actually wondering if this is actually an issue with Ubuntu rather than firefox. 

If you can't find anything using too much CPU by using the top command, than disable Remote Desktop. It is usually the culprit of mysterious  CPU usage.

---

### Post by allspiritseve on 2009-07-11
I don't believe Remote Desktop is enabled. However, I have noticed Xorg CPU usage in the range of 60-70% a couple of times when it freezes. Any idea what that's about?

---

### Post by Bradj47 on 2009-07-11
I had this problem when I was using Hardy before I switched to Jaunty. Now in Jaunty Firefox just slows down my whole system and I don't use it anymore. I switched to Epiphany.

---

### Post by powertower on 2009-07-23
OK so I've been fighting this problem for several weeks. No one seemed to know why firefox would freeze in Ubuntu 8 and 9. I figured it out by running firefox in debug mode. "NSPR_LOG_MODULES=all:5 firefox"

Every time firefox froze I would see "resolving safebrowsing-cache.google.com". So I tried the usual ping, nslookup and the results were very inconsistent. Sometimes it would resolve but mostly just time out.


After a little googling I found out that firefox has built in Google Safe Search that frequently communicates with safebrowsing-cache.google.com.

So I disabled this safe search feature and NO MORE LOCK UPS!!

You can disable This safe search feature by going to Edit - Preferences -  Security, uncheck "Block reported attack sites" and "Block reported web forgeries" .

---

### Post by lovinglinux on 2009-07-23
> **powertower said:**
> OK so I've been fighting this problem for several weeks. No one seemed to know why firefox would freeze in Ubuntu 8 and 9. I figured it out by running firefox in debug mode. "NSPR_LOG_MODULES=all:5 firefox"

Every time firefox froze I would see "resolving safebrowsing-cache.google.com". So I tried the usual ping, nslookup and the results were very inconsistent. Sometimes it would resolve but mostly just time out.


After a little googling I found out that firefox has built in Google Safe Search that frequently communicates with safebrowsing-cache.google.com.

So I disabled this safe search feature and NO MORE LOCK UPS!!

You can disable This safe search feature by going to Edit - Preferences -  Security, uncheck "Block reported attack sites" and "Block reported web forgeries" .

Great finding! I will try it. I don't have it enabled on my desktop, but I will check the notebook, which is the one having issues.

---

### Post by powertower on 2009-07-23
> **lovinglinux said:**
> Great finding! I will try it. I don't have it enabled on my desktop, but I will check the notebook, which is the one having issues.

Do you use a proxy? I use one at work but not at home and both have troubles. I would love to know if this resolved your issue so I can post this solution on other threads. Seems to be affecting lots and lots of people...

My firefox would go gray every few minutes and then just start working again.

---

### Post by lovinglinux on 2009-07-23
> **powertower said:**
> Do you use a proxy? I use one at work but not at home and both have troubles. I would love to know if this resolved your issue so I can post this solution on other threads. Seems to be affecting lots and lots of people...

My firefox would go gray every few minutes and then just start working again.

It was enabled on the notebook. I have disabled it now, but I will only report back tomorrow.

---

### Post by lovinglinux on 2009-07-25
> **powertower said:**
> Do you use a proxy? I use one at work but not at home and both have troubles. I would love to know if this resolved your issue so I can post this solution on other threads. Seems to be affecting lots and lots of people...

My firefox would go gray every few minutes and then just start working again.

I don't use a proxy.

The computer with issues is not actually mine, so I can't confirm with confidence yet that this solved the issue, but apparently it does. I recall a similar situation when I used Firefox on Windows a while ago and this service was causing trouble too. So, I have included your solution, with the proper credits, in my tutorial for now. I will leave it there if the problem do not persist after a week or so.

See **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT010).

---

### Post by expatCM on 2009-07-25
well this IS an interesting thread.  I have put through the settings suggested by PowerTower and this has really really helped me out a lot.

Apart from the freezing which I have been experiencing I have had one other problem.  Pages have been slow to load on many sites.  I had thought that was totally due to my ISP but I did notice a number of references of waiting for google pages .....  Now having unchecked these two items I do not get the same delays at all ....  it is a big improvement.  Thank you for the post.

---

### Post by powertower on 2009-10-24
Upgraded to Ubuntu 9.04 Jaunty Jakalope yesterday.

Problem still exists with this new distribution.

---


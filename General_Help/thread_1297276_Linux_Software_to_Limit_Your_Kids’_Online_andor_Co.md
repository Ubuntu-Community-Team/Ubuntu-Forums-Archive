---
title: "Linux Software to Limit Your Kids’ Online and/or Computer Time"
date: 2009-10-21
forum: General Help
---

### Post by GrzegorzJZD on 2009-10-21
Hi,

I'm looking for Linux software that can limit time on computer and being online under Ubuntu. Is there any?

---

### Post by daevski on 2009-10-21
PAM is built in to ubuntu, but it's kind of complicated to use... There is a lot of configuring. 

BUT, if you are interested, you can google "PAM (pluggable authentication modules)" and read up on it.

I imagine it works excellently, but haven't found the time to configure things yet :-\

---

### Post by osomphane on 2009-10-21
Kids spending too much time on a computer can indicate social problems. You may want to consider spending more time with them, either introducing them to sports and other activities that are interesting for them or meeting them with friends...

---

### Post by StuartN on 2009-10-21
> **GrzegorzJZD said:**
> I'm looking for Linux software that can limit time on computer and being online under Ubuntu. Is there any?

One way is to configure the router with access rules. Some routers have rules that can control access to individual services (smtp, ftp, http, etc) by time of day and by day of week and apply the rules to an IP address or a MAC address.

One of my children was quite unable to moderate internet time, and we agreed (err...) a schedule that had email all the time and fixed web access sessions. And then there was the Grounded rule that was switched on for any kind of infraction, like looking at me funny.

---

### Post by jmszr on 2009-10-21
GrzegorzJZD,

This looks like it might work for you: [http://ubuntuforums.org/showthread.php?t=887769](http://ubuntuforums.org/showthread.php?t=887769).

---

### Post by GrzegorzJZD on 2009-11-14
@jmszr: Timekeepr looks nice, I will definitely check it. Thanks. 

@osomphane: Thanks for psychological bµllshit. This is Ubuntu Forum and I was asking for a program name, not advices how to raise kids.

@all: Parental Controls Tools are very popular and there are special build-in software or features in Windows and Mac. It's very surprising (in a bad way) that there is now such a program for Linux users, neither in GNOME nor in KDE.

---

### Post by lykwydchykyn on 2009-11-14
I used timekeepr and it's not nearly as flexible as I'd like but it does the job.  'Course if you dual-boot it just encourages them to go back to Windows. ](*,)

Also, Ubuntu Christian Edition contains a parental controls system; it should be installable on any any Ubuntu system, though I'm not sure how (I don't think the graphical front end is in the repos -- I use a centralized web filter on my home server personally.)

---

### Post by SuperSonic4 on 2009-11-14
It's called a timer. You set the timer and when it reaches bam goes the power/internet.

You could use shutdown for one period of time

```
sudo shutdown -hP HH:MM
```

---

### Post by GrzegorzJZD on 2009-11-14
@SuperSonic4: If I use shutdown anyone will be just force to shutdown computer after a specified time, after that will be able to start computer for another period of time. That sucks. 

@lykwydchykyn: Thanks for information, but for now I don't now any other software to setup time limits in useing computer. Better this than nothing. But I'm sill opened for other tips ;)

---

### Post by Bucky Ball on 2009-11-14
If you are looking to limit content, Dan's Guardian is supposed to be good. I am going to set it up for some friends soon but from research that is the one. Don't know if it has a timer though.

---

### Post by GrzegorzJZD on 2009-11-14
What I'm looking for is a **tool to limit time spend on computer or time spend on being online, not a content blocking tool**, but thanks anyway.

For example: I'd like to limit daily time which can be spend on computer by user "David" to 4 hours and a time which can be spend online to half of this.

---

### Post by Bucky Ball on 2009-11-14
Sorry, I misunderstood this:

Re: Linux Software to **Limit Your Kids&#8217; Online** and/or Computer Time

What's the 'limit your kids online' bit about? I thought you were addressing two separate issues. :)

---

### Post by GrzegorzJZD on 2009-11-14
@Bucky Ball: I'm not sure if this is my original thread title and talking about it is useless, don't You think so?

Look up [#11](http://ubuntuforums.org/showpost.php?p=8315891&postcount=11), I think I did explain issue well.

---

### Post by lykwydchykyn on 2009-11-14
> **GrzegorzJZD said:**
> What I'm looking for is a **tool to limit time spend on computer or time spend on being online, not a content blocking tool**, but thanks anyway.

For example: I'd like to limit daily time which can be spend on computer by user "David" to 4 hours and a time which can be spend online to half of this.

Well, timekeepr can do the first half (limit the amount of time logged in daily), but as far as getting granular about what's done while logged in I doubt you'll find anything.

From a programming perspective, I'm not even sure how you'd define "online time" on a system like Ubuntu.  Does that mean "time that an application capable of web browsing is running", or "time from the first http request", or "time that a web-browsing application is in focus on the desktop", or something else entirely?  What do you do with programs like Konqueror, which can be a file manager or a web browser?  

Anyway, that's going on a tangent.  What you might find useful is a program that logs http requests so you can go back and see how much time is being spent online and where its being spent.  I know Dansguardian logs all http requests, but probably there are programs with less overhead that do as well (probably any of the web proxies like squid or tinyproxy).

---

### Post by GrzegorzJZD on 2009-11-14
@lykwydchykyn: In most Windows application there is a customizable list of programs allowed to use internet connection (usually Web browsers, IM, e-mail clinets etc). If user uses them more than limit time he or she gets an information box, that online time is over for today.

---

### Post by bluelamp999 on 2009-11-14
> **GrzegorzJZD said:**
> @osomphane: Thanks for psychological bµllshit. This is Ubuntu Forum and I was asking for a program name, not advices how to raise kids.

Well said Grzegorz!

---

### Post by bruno9779 on 2009-11-14
> **GrzegorzJZD said:**
> @osomphane: Thanks for psychological bµllshit. This is Ubuntu Forum and I was asking for a program name, not advices how to raise kids.

I agree with osomphane. You asked about a computer issue, and the answer is [PEBCAK]("http://www.webopedia.com/TERM/P/PEBCAK.html").

---


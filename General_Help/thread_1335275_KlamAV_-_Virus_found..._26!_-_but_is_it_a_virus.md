---
title: "KlamAV - Virus found... 26! - but is it a virus?"
date: 2009-11-23
forum: General Help
---

### Post by WRCLiam on 2009-11-23
[IMG]http://img338.imageshack.us/img338/9477/screenshotgv.png[/IMG]


What should i do ?

---

### Post by Grenage on 2009-11-23
Are they files you recognise? If in doubt, run them through an online scanner:

[http://www.virustotal.com/](http://www.virustotal.com/)

---

### Post by WRCLiam on 2009-11-23
heres a problem when i quarantine the lot

[IMG]http://img256.imageshack.us/img256/9325/screenshot1rw.png[/IMG]

---

### Post by Grenage on 2009-11-23
I haven't used klamav, but are the files in: /home/$USER/.klamav/quarantine ?

---

### Post by WRCLiam on 2009-11-23
no mate none of them i know :s

---

### Post by NoaHall on 2009-11-23
No, they aren't viruses. This is exactly the reason why you shouldn't use virus scanners on Linux, and why you should certainly not run them as root. They are core package files which the scanner could not scan, so called them "viruses".

---

### Post by WRCLiam on 2009-11-23
nope

---

### Post by reeboker on 2009-11-23
I have browsed Klamav FAQ section, and did not found what this is supose to detect. And since linux doesn't use registry I see no point in using this, maybe in the future there could be implemented some av (thingie) in ubuntu, but since it's around 5yrs or so in developement, and noone suggests to use some kind of these software packages I STILL see no point why to bother.

---

### Post by gdonwallace on 2009-11-23
Any file that starts with lib is a library file that could potentially be associated with a program that you already have installed.  It just may not be running at the time you are scanning for viruses.

From a personally note, I have Ubuntu installed on my personal laptop and my computer at work.  I do not have any virus software installed on either and have never had a problem. In over a year and a half.  Although I have tried virus scanners in the past, and they always found lib files.  Mainly because they don't know what they are and therefore assume that they are a virus.  Unless you have some sensitive information or personal financial information, which in my case I don't have either; I would not worry about it.  

Now, a lot of people are going to say that Linux is much more secure than windows when it comes to virus / maleware attacks.  And to a point they are correct, but that truth needs to be taken with a grain of salt.  1.  If Linux was 1/2 a popular as Apple / MS then yes, there would be news of a lot more attacks.  The fact that Linux currently has less than 5% of the PC market, shows that it is of no interest to those that write viruses currently. (however; 3  months ago the first ever Linux botnet was discovered.....Linux has been around for over 2 decades and the first botnet was just found)  2.  Goes back to number 1 in a way.  Most viruses are written to take advantage of the windows file / directory structure.  The reason is, that is what the little hackers no.  Understanding that most hackers a teens early 20's proves this.  They now windows.  3.  Security.  There are certain things in Linux that must be run with increased permissions. (i.e. sudo)  Without those increased permissions, it just can't be done.  

So yes, Linux is in a way more secure than Windows, but if Linux kicks up in popularity, then that may change in the near future.

---

### Post by t0p on 2009-11-23
> **gdonwallace said:**
> Now, a lot of people are going to say that Linux is much more secure than windows when it comes to virus / maleware attacks.  And to a point they are correct, but that truth needs to be taken with a grain of salt.  1.  If Linux was 1/2 a popular as Apple / MS then yes, there would be news of a lot more attacks.  The fact that Linux currently has less than 5% of the PC market, shows that it is of no interest to those that write viruses currently. (however; 3  months ago the first ever Linux botnet was discovered.....Linux has been around for over 2 decades and the first botnet was just found)  2.  Goes back to number 1 in a way.  Most viruses are written to take advantage of the windows file / directory structure.  The reason is, that is what the little hackers no.  Understanding that most hackers a teens early 20's proves this.  They now windows.  3.  Security.  There are certain things in Linux that must be run with increased permissions. (i.e. sudo)  Without those increased permissions, it just can't be done.  

So yes, Linux is in a way more secure than Windows, but if Linux kicks up in popularity, then that may change in the near future.

1.  Okay, let's assume that you're right about "hackers" being in their teens and early twenties: why would this mean that they don't know much?  What about the fact that there are plenty of clueless users in their 30s and 40s?  What about the fact that users in their teens and early 20s are generally more informed on IT subjects than older users?

2.  If the relatively low popularity of Linux explains the almost non-existent number of viruses: how come there are so few Mac OSX viruses?  I thought it was because OSX, like Linux, has the very secure Unix-type file structure and security model.  But if it's down to popularity, shouldn't there be quite a lot of OSX viruses out there?  (IF anyone is in any doubt as to the prevalence of OSX viruses, read [this very informative article on the subject]("http://reviews.cnet.com/8301-13727_7-10331147-263.html").)

---


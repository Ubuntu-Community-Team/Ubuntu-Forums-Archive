---
title: "dansguardian filtering problem"
date: 2012-06-06
forum: General Help
---

### Post by Rakeshvijayan on 2012-06-06
Hi friends 

I got a  new message which shows the time is not correct .previous week this filtering work and i was satisfied with that ..I enclosed the screen shot of the message please help me if you have to resolve this issure

---

### Post by dino99 on 2012-06-06
what can we understand from this screenshot ?:confused:
which way is used to run dansguardian ? from which release ?

---

### Post by Rakeshvijayan on 2012-06-06
> **dino99 said:**
> 
which way is used to run dansguardian ? from which release ?
I am using dansguardian 2.10.1.1-4 .It installed on ubuntu12.04 server edition and i configure webmin to take log file of dansguardian .i can see the log on previous week i dont know what happen now

---

### Post by dino99 on 2012-06-06
i'm not a dansguardian user, i prefer pgl (which is very close too), but there are lots of related threads here about it:

[http://ubuntuforums.org/tags.php?tag=dansguardian](http://ubuntuforums.org/tags.php?tag=dansguardian)

---

### Post by Rakeshvijayan on 2012-06-06
[FONT=arial,helvetica,sans-serif][SIZE=3][B]


"Invalid date detected - 2012.52012.5.29"[FONT=Arial]
[SIZE=1][SIZE=2]

This is the problem show when i try to get log.is there any time settings on dansguardian configuration file ...
[/SIZE][/SIZE][/FONT][/B][/SIZE][/FONT]

---

### Post by Rakeshvijayan on 2012-06-07
any know the solution

---

### Post by Rakeshvijayan on 2012-06-11
This is because of module configuration access.log .I find the solution by remove access log.1

---

### Post by pcalligaris on 2013-05-27
Hello Dino99,
you wrote "i prefer pgl" please can you tell me the complete name of this software?
thanks
Paolo

---

### Post by mikeym on 2013-05-28
Hi Paolo,

*pgl* is Peer Guardian Linux. [http://sourceforge.net/projects/peerguardian/](http://sourceforge.net/projects/peerguardian/)

---


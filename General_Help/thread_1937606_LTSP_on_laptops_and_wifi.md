---
title: "LTSP on laptops and wifi"
date: 2012-03-08
forum: General Help
---

### Post by Exonimus on 2012-03-08
Esteemed fellow Ubuntu-users,

For a long time, I&#8217;ve dreamed of having some kind of centralized way of sharing and managing the computers and accounts at my parents&#8217; home. We have an -ever increasing, it seems!-  number of computers there, to which a (file/media) server has recently been added, the server being an old (p4) laptop of mine with rather low power usage running ubuntu.

Anyway, the issue: I have recently come across LTSP and I absolutely love it. It gives me a way to have not only a centralized way of logging in users, but a way of having exactly the same desktop on whichever place at the house one happens to be at. The feature I love most is that I can, in fact, make some apps run locally, thus also play videos smoothly. Now, some of the pc&#8217;s at my parents house are connected through a wired network, but we also have some laptops connecting through wifi that are taken out of the home rather often. I have done some research and found there should be a way to turn them into what essentially are a variation on fat clients, storing some stuff on the local hard disk and loading the rest from the server.

However, there are several factors I&#8217;m still wondering about:
 
-From what I&#8217;ve read, I know a pc with a full ubuntu install (so working locally out of home is possible) can still connect to the remote server on login, but would there be a similar way to have some apps run locally, and some on the server? (I&#8217;m not sure where the specifics of connecting such a pc to the server in comparison to a semi-thin client are concerned)

-is there a way to make an exact copy of the server files onto a backup pc? I&#8217;ve heard of rsync and I&#8217;m pretty sure it&#8217;s able to do such a job, but which directories are most important in this regard? 

-provided I can get it to work, to which extent is ltsp over (a 300n) wireless network a workable alternative to wired connections?

---


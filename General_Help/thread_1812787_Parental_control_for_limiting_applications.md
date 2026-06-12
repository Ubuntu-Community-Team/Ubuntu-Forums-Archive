---
title: "Parental control for limiting applications?"
date: 2011-07-26
forum: General Help
---

### Post by Isaacgallegos on 2011-07-26
I want to be able to limit the amount of time per day my computer can run certain applications, like games, sound, and graphics programs. 

For example, I'd like to have a total of an hour per day be allowed for a user between all allowed apps. 

Gnome Nanny seems to only be able to limit "browsing the web, chatting or doing email". They mention nothing about limiting other applications. 

My guess is there's something like this outside the repos? I looked and found only applications that limit web use. 

This application would make life better. If there's nothing like it, I'm also a python newb; this could be an interesting thing for me to make.

---

### Post by jerrrys on 2011-07-26
i do not use anything like this, but got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=limit+computer+time&sa=Search&cof=FORID:9#986](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=limit+computer+time&sa=Search&cof=FORID:9#986)

---

### Post by Isaacgallegos on 2011-07-26
I'd remove the applications completely before resorting to that. 

But thanks for looking!

---

### Post by nothingspecial on 2011-07-27
[https://launchpad.net/timekpr](https://launchpad.net/timekpr)

timrkpr limits total computer usage. It is nolonger developed but still works. Perhaps you could modify it to your needs.

---

### Post by Isaacgallegos on 2011-07-27
Thanks. Question: Wouldn't an application that locks someone out of a computer, after a time limit, work completely differently than one that counts time spent on specific applications and only locks you out of those applications?

---

### Post by Guido Tabbernuk on 2012-01-22
> **Isaacgallegos said:**
> Gnome Nanny seems to only be able to limit "browsing the web, chatting or doing email". They mention nothing about limiting other applications. 

My guess is there's something like this outside the repos? I looked and found only applications that limit web use. 

This application would make life better. If there's nothing like it, I'm also a python newb; this could be an interesting thing for me to make.
If you wan't to get your hands dirty, I think Nanny can block any applications, not just the ones mentioned. It just has 4 categories for apps, first of them watches basically for *gnome-session*, second one watches for *thunderbird, evolution*, third one for *firefox, epiphany, konqueror* and fourth one for *pidgin, xchat, amsn*. You can add any applications if you edit files under */etc/nanny/applists*. Just add the names of the processes involved.

The thing is that the functionality may just not work in Nanny now, because it's not updated for latest Ubuntus. I myself did some updating for Oneiric and published my changes for testing at [https://launchpad.net/~boamaod/+archive/nanny-test](https://launchpad.net/~boamaod/+archive/nanny-test). You may wan't to fix the application blocking part... If you say, it would be interesting thing to make.

For further implementation, it would be smart to add any amount of apps categories to block besides session and web which should be built in, I believe, since they involve some extra settings. E-mail and IM can be replaced or additioned with any categories, because they are generic. It can be implemented in UI level, it just takes couple of days of hacking to do it properly.

---


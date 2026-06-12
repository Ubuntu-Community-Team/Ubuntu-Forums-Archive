---
title: "Faster Download Speeds?"
date: 2011-06-24
forum: General Help
---

### Post by Kocrachon on 2011-06-24
So not really much of a tech support question, but a general question.

So I switch between Ubuntu and Windows alot, because some games I can only get to run smoothly in the windows environment. Anyways, one thing I have been noticing ever since I got Ubuntu but never really questioned, was about my download speeds.

When downloading a torrent in Windows, I topped out out about 2.0 mb/s. Where as in my Ubuntu install, running the same torrent program (utorrent) and downloading the same file, I was getting 3.0 mb/s. I was wondering, what is it about Ubuntu that is utilizing my internet connection better? Only a hand ful of times have I ever reached 3.0 in my windows install (such as right now while I am downloading a game through steam).

---

### Post by LordNeo on 2011-06-24
It's called QoS (Quality of Service) in Windows, that saves up some bandwidth if you need to open a second program that needs internet. Then it uses the QoS quota meanwhile the system balance the internet load and saves again the QoS quota for future programs.
By default is configured in 20% (IIRC) and you can't go lower than 5% (again, IIRC).
In Linux in general, it's made at kernel/connection level, so is not really needed.

PS: Not to mention the "ninja connections" in Windows.

---

### Post by Kocrachon on 2011-06-24
So is there a way for me to adjust it in windows? It would make my life much easier. I run windows 7 at the moment.

---

### Post by LordNeo on 2011-06-24
I don't remember the entire steps to adjust it.

From a quick google search i found:

Run: gpedit.msc -> Network -> QoS -> Limit the reserved bandwidth.

Sorry if i'm in a mistake, try getting some info in Windows forums or something alike, they should be a little more specific.

---


---
title: "Difficulty connecting to Internet"
date: 2010-06-16
forum: General Help
---

### Post by Paul2795 on 2010-06-16
A few months back my previous computer went west and I've only just got a replacement, and having had enough of Windoze to last me a lifetime, I decided on Linux and and selected Ubuntu, keeping the Internet account current in the interim with a couple of topups done from Internet cafes. Problem. I'm on mobile broadband, Virgin to be exact. The machine recognizes the modem; the Virgin icon is plainly visible on the desktop, but that's as far as it goes, I simply can't connect, though I think the machine is trying to.
I set up a mobile broadband connection and I've edited it every whichaway, but to no avail. It's only Basic though, I haven't tried Advanced. Should I try Advanced, and while I'm at it, what else could causing my problems?

---

### Post by rjcalifornia on 2010-06-16
hey there! does your connection requires username and password?

---

### Post by Paul2795 on 2010-06-16
Yes, I did make sure to enter my username and password.

---

### Post by cneha on 2010-06-16
i also have the same problem..someone help...

---

### Post by rjcalifornia on 2010-06-16
here is the problem guys... That thing doesnt work. It happened to me too... Anyways, here is how to solve this..

open Terminal type this

> sudo pppconf

or

> sudo pppoeoconf


Fill it with your username and password, click OK to everything and done. When you restart the computer, it will automatically connect to the internet, but it will ask for your kwallet pass... cheers!!

---


---
title: "not connecting to DeaDBeeF server"
date: 2011-10-15
forum: General Help
---

### Post by Apolyonn on 2011-10-15
Hey all,

I love DeaDBeeF, but for some reason, after upgrading to 11.10, Synaptic gives me an error whenever it tried to load from ppa:alexey-smirnov/deadbeef.  It will not connect to his database and, thus, I can't get Deadbeef.  I've tried sudo apt-get update in a terminal, and I've tried refreshing the Synaptic list, but both say that they cannot connect.  

I find it odd since I downloaded it onto my PC two nights ago and everything worked fine. 

I'm running Xubuntu, but I'm wondering if this is an issue with Oneric in general.

---

### Post by Apolyonn on 2011-10-15
Looks like I solved it myself.  Solution was kinda weird tho.  When I re-tried apt-get upgrade, I noticed that it was looking for deadbeef in an "oneric" folder in alexey's server.  I went in Synaptic > Settings > Repositories, then Edit on alexey's ppa, and noticed "oneric".  Naturally, I changed it to "natty".  Re-tried upgrade, install deadbeef, and now it's there and running well.

On the other hand, how can I predict or know if I should, at any point, change that back to "oneric"

---

### Post by rojaasensei on 2011-10-15
Thanks for posting.  I'll be upgrading to 11.10 myself next week.  And I can't live without DeadBeef.  If I have a problem I'll try what you did.

---

### Post by Apolyonn on 2011-10-15
Awesome, let me know if it does work without having to tamper with any settings.

---

### Post by rojaasensei on 2011-10-15
will do
Long live DeadBeef

---

### Post by earwig1 on 2011-10-16
Just had the same problem, same solution worked for me.

---

### Post by rojaasensei on 2011-10-20
yep, same problem, same solution.

Thanks for the heads up.  Otherwise I'd be going crazy trying to get Deadbeef reinstalled.:p

---


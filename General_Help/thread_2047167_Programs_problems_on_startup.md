---
title: "Programs problems on startup"
date: 2012-08-24
forum: General Help
---

### Post by stefve on 2012-08-24
Hi

Sometimes when I start Ubuntu Desktop, it doesn't start the Couchpotato daemon, other times it starts perfectly. Als some of my hard drives temperatures won't show. And other times they are shown perfectly.

How is it possible that this happens now and then and not always? And how can I fix this?

Thanks in advance!

[IMG]http://i50.tinypic.com/24l9e7c.png[/IMG]

---

### Post by Rexilion on 2012-08-24
My first guess would be a race condition, perhaps you could delay the starting of these programs?

---

### Post by stefve on 2012-08-24
Thanks for your answer.

That could be the problem. But al my programs that start on boot are controlled by /etc/init.d, so is it possible to create a delay in between?
I don't know much about it, I just followed the tutorial of the programs.

Couchpotato Example:

Ubuntu (init.d script):

Copy "initd.ubuntu" to /etc/init.d/couchpotato - > "sudo cp initd.ubuntu /etc/init.d/couchpotato"
Copy "default.ubuntu" to /etc/default/couchpotato - > "sudo cp default.ubuntu /etc/default/couchpotato"
Edit the required daemon settings in /etc/default/couchpotato - > editor /etc/default/couchpotato
If your CP installation isn't in "/opt/couchpotato/", make sure to change the path there also!
Make executable "sudo chmod a+x /etc/init.d/couchpotato"
Add it to the startup items: "sudo update-rc.d couchpotato defaults"
Start with "sudo service couchpotato start"


and I did the same for sabnzbd, sickbeard, Autosub,...
By the way, AutoSub has the same problem as couchpotato of not starting up..

Thanks in advance!

---

### Post by Rexilion on 2012-08-24
I don't know about these daemons, but if they are dependent on each other then you should write that down in the init files.

Is that a solution?

---

### Post by stefve on 2012-09-03
Still having these problems, is there someone that can help me?

---


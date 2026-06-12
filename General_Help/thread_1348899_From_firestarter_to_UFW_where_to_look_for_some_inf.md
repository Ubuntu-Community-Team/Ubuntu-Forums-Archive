---
title: "From firestarter to UFW where to look for some info."
date: 2009-12-07
forum: General Help
---

### Post by Sorwen on 2009-12-07
So I have been reading about firestarter and the suggestion to drop it for UFW.  Since what I want to use my system that has ubuntu nr for is is really limited just using the UFW option seems fine.  The one thing I do like is being able to see real time what programs are accessing which ports when.  From what else I've seen it seems likely that the information would still be logged some where the question is where would I look for it?

---

### Post by pbrane on 2009-12-07
ufw logs output to kern.log. Also shows up in messages and syslog too. ufw is a great host level firewall. you can also use gufw to configure ufw. It's a nice GUI. And you can see log messages too.

---

### Post by doas777 on 2009-12-07
my big beef with gufw is that there are no monitoring components. 
I've checked my kern log and have never seen a message yet, which i find a little disconcerting.

the best app for tracking bandwidth for applications, is iftop. you can find it in the repos. just run it in a terminal.

---

### Post by pbrane on 2009-12-07
when I **sudo ufw logging <level>** I see output from ufw in kern.log, messages, and syslog. iftop and iptraf are two good real time monitoring apps. iptraf will log as well. I was just suggesting gufw as a way to easily configure ufw, some people don't like the command line.

---

### Post by Sorwen on 2009-12-07
Thank you both for the posts. :)

---


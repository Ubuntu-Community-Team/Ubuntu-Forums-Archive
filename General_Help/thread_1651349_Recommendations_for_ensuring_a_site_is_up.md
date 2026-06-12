---
title: "Recommendations for ensuring a site is up?"
date: 2010-12-23
forum: General Help
---

### Post by tarahmarie on 2010-12-23
Hi, all:

I have a site that is currently on an unreliable server. Yes, we're fixing that; suffice to say the situation isn't permanent. 

I would like to know how to set up a fail check on the site.  There are plenty of services out there, but I've got a server that I can add scripts to in the crontab.  

What elements would you recommend I have in the script? I think:

Ping
   If no packet return,
      Log the time and error
      Email me
   Else
      Log the time

Sound about right?

---

### Post by Wtower on 2010-12-23
Sounds good to me. You could also use wget to download an actual web page from the site instead of ping in case you want to disable ping responses from your server.

---


---
title: "Run shortcut as Admin"
date: 2011-02-20
forum: General Help
---

### Post by MrRichard on 2011-02-20
I've tried Googling this question with no luck. I'm trying to get a program called Aptana to run as admin so I can edit my website under /opt/lampp/htdocs. Here's the link to Aptana:
/home/richard/.Aptana Studio 3/.AptanaStudio3

What would I have to put into the shortcut command to run as admin?

---

### Post by Syed75 on 2011-02-20
> **MrRichard said:**
> I've tried Googling this question with no luck. I'm trying to get a program called Aptana to run as admin so I can edit my website under /opt/lampp/htdocs. Here's the link to Aptana:
/home/richard/.Aptana Studio 3/.AptanaStudio3

What would I have to put into the shortcut command to run as admin?

sudo -u condor /home/richard/.Aptana Studio 3/.AptanaStudio3

Try that.

---

### Post by MrRichard on 2011-02-20
> **Syed75 said:**
> sudo -u condor /home/richard/.Aptana Studio 3/.AptanaStudio3

Try that.

*sudo: unknown user: condor*

I tried replacing condor with my username. Aptana then started up just fine, but it didn't seem like I had root privileges because I couldn't edit the files in /opt.

---

### Post by Syed75 on 2011-02-20
> **MrRichard said:**
> *sudo: unknown user: condor*

I tried replacing condor with my username. Aptana then started up just fine, but it didn't seem like I had root privileges because I couldn't edit the files in /opt.

sudo chown username /opt/lampp/htdocs


[http://ubuntuforums.org/showthread.php?t=1365274](http://ubuntuforums.org/showthread.php?t=1365274)

---

### Post by MrRichard on 2011-02-20
> **Syed75 said:**
> sudo chown username /opt/lampp/htdocs


[http://ubuntuforums.org/showthread.php?t=1365274](http://ubuntuforums.org/showthread.php?t=1365274)

Yes! Thank you so much! I can't believe I forgot about that :rolleyes:

---

### Post by Syed75 on 2011-02-20
> **MrRichard said:**
> Yes! Thank you so much! I can't believe I forgot about that :rolleyes:

No sweat.

---


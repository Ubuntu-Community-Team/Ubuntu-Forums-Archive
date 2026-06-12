---
title: "Winbind stops working during domain authentication"
date: 2006-03-23
forum: General Help
---

### Post by mcanada on 2006-03-23
I have Kubuntu 5.10 with samba joined to a NT 4 domain (Slackware 10.1 running Samba). I have set up my Kubuntu as per a HOWTO found in the Warty forum.

I am able to authenticate my users from the domain and login to my Kubuntu.

The problems is when I mis-type the password! As soon as a password is mis-typed, winbind stops working and I have to log in as a "local" user to restart winbind. Once winbind is restarted, my domain users can login to Kubuntu again.

Generally it isn't a problem if I don't mis-type my password, but it happens from time to time and it gets annoying!

Has anybody else had this problem? I haven't found anything in the forums for this specific problem.

---

### Post by mcanada on 2006-03-29
I figured out my problem.

The problem was in my PDC. I was running Samba 3.0.20 on Slackware 10.1. After verifying on a REAL Windows NT domain that the winbind didn't stop working after an invalid authentication, I decided to upgrade my Samba.

I downloaded Samba 3.0.21c and compiled it on the same Slackware 10.1 server. Everything is fine now and winbind doesn't need to be restarted after an invalid authentication attempt.

---


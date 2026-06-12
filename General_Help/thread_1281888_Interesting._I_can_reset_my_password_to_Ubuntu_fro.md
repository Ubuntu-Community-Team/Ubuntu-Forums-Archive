---
title: "Interesting. I can reset my password to Ubuntu from an XP machine via Samba....."
date: 2009-10-03
forum: General Help
---

### Post by Roasted on 2009-10-03
So, I did a little digging and I realized something. Within XP, I can edit the saved credentials I've put in before. Meaning if you go to start - run - \\server and you get a login box, you know that remember this checkbox there? You can edit that under control panel - user accounts - manage my network passwords.

So, just messing around, I did just that. In XP the password comes up blank, so I just typed in one. To try and see what errors I would get, I typed in the wrong password intentionally. It asked me if I wanted to change this on the domain, I said yes. Sure enough, it changed my Ubuntu system password. No, not just my samba account password, my actual SYSTEM password.

So on my Ubuntu machine, I have jason as a user that I'm logged into now. I also have jason as a samba user. I have two different passwords for each account for security reasons. But when I changed the password from within XP, it changed them both to the new password I put in. I realized this when I tried to go into synaptic and it kept saying my password was wrong. On a hunch, I typed in the new one I changed in XP on the "domain" and presto - synaptic worked.

This here... is a very big problem. How do I prevent this from happening? It's frustrating because I specifically wanted my samba user and my system user to have two very different passwords, and unfortunately if my actual system password can be reset just like that, it won't work here. It's one thing to reset a samba password, but I don't want something so simple to effect my samba machine from actually logging in.

EDIT - On the other hand, maybe it's not that big of a problem. I was worried at first because I was suspecting all XP users on the network could force change my password for my account. But they have their own accounts. So at best, they change their own passwords. So realistically, the only way I'd have a problem on my hands is if someone hacks my XP machine and knows what they're doing enough to screw up my samba password for my account, which in turn effects my login password. 

QUESTION - Say this happens. How can I reset my password? Can I boot to failsafe mode and log in to root in terminal? I know root is disabled or whatever, but how would I reset my password from failsafe terminal if I can't even log into MY account?

---

### Post by SoftwareExplorer on 2009-10-04
> **Roasted said:**
> QUESTION - Say this happens. How can I reset my password? Can I boot to failsafe mode and log in to root in terminal? I know root is disabled or whatever, but how would I reset my password from failsafe terminal if I can't even log into MY account?

Well, once you are in the failsafe mode you can get a root prompt without the password (yes, it will let you in if you boot in recovery mode), and then you can run 'passwd <username>', and change it to what you want.

---

### Post by Roasted on 2009-10-04
> **SoftwareExplorer said:**
> Well, once you are in the failsafe mode you can get a root prompt without the password (yes, it will let you in if you boot in recovery mode), and then you can run 'passwd <username>', and change it to what you want.

Brilliant. Thank you!

---

### Post by SoftwareExplorer on 2009-10-04
> **Roasted said:**
> Brilliant. Thank you!

Your welcome. :) 

Not so sure I like the idea of LAN users being able to change my password.

---

### Post by HermanAB on 2009-10-04
It is a feature of Samba that it will keep your account passwords in synch between Windows and Linux.

---

### Post by danwood76 on 2009-10-04
You can change whether the passwords can be changed or not in the samba config.
And also if they are synced.

Checkout the samba config online and change as necessary.

---

### Post by Roasted on 2009-10-04
> **SoftwareExplorer said:**
> Your welcome. :) 

Not so sure I like the idea of LAN users being able to change my password.

That's where I was confused at first. I was thinking that ANY user could change MY password, but each user has their own user account that they are linked to, so nobody is working off of my account to begin with. If they change any password - it's their own password. I only realized that after I made this thread and I was like, oh, duhhhh. :lolflag:

---


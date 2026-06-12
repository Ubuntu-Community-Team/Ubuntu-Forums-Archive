---
title: "How to be root all the time - I just wanna have a choice to do so"
date: 2010-02-03
forum: General Help
---

### Post by Martin McFly on 2010-02-03
> Users shouldn't run as administrators, it's better to use su/sudo

Yes, I know the risks. But if I seriously want to run as an administrator, what should I do ? Yes, I heard/read dozens of times about how bad it is, how unsafe and really, I know which risks I'm facing here.
We, who ascended to Linux from Windows were doing this for years, right ? I mean back there, we had all the rights to change most of the things (including erase hard-drive, delete important system files) and we're here, safe and sound. I for example have been running Windows for 9 years (98-XP) and except few viruses (which are rare in Linux), I've never encountered anything bad.

If you simply can give me guide how to become root, it's can't be truth that it's not possible to do so. Common, with proper backup and some basic safety rules, risk of losing everything (backups guys, backups, I have them) is far lower than this eternal asking for root password that's driving me mad. I'll lose data, OK, that's my choice.


But guys, newbies, users and experts, I know that there can be excuses, bypasses, things to do to avoid this, but. I want to have this choice. I want to freely decide that I want to be root.

And I'm decided.

---

### Post by skymera on 2010-02-03
> **Martin McFly said:**
> Yes, I know the risks. But if I seriously want to run as an administrator, what should I do ? Yes, I heard/read dozens of times about how bad it is, how unsafe and really, I know which risks I'm facing here.
We, who ascended to Linux from Windows were doing this for years, right ? I mean back there, we had all the rights to change most of the things (including erase hard-drive, delete important system files) and we're here, safe and sound. I for example have been running Windows for 9 years (98-XP) and except few viruses (which are rare in Linux), I've never encountered anything bad.

If you simply can give me guide how to become root, it's can't be truth that it's not possible to do so. Common, with proper backup and some basic safety rules, risk of losing everything (backups guys, backups, I have them) is far lower than this eternal asking for root password that's driving me mad. I'll lose data, OK, that's my choice.


But guys, newbies, users and experts, I know that there can be excuses, bypasses, things to do to avoid this, but. I want to have this choice. I want to freely decide that I want to be root.

And I'm decided.

sudo su

---

### Post by McNils on 2010-02-03
sudo -i

---

### Post by Joeb454 on 2010-02-03
> **McNils said:**
> sudo -i

This is generally how I'll become root for extended periods of time.

If you're asking how to login as root - you're asking in the wrong place, as it isn't something we'll support on these forums.

---

### Post by nothingspecial on 2010-02-03
Install a different distro that defaults to root.

****off topic****

By the way, check out the music player in my sig, you might like it.

---

### Post by mkvnmtr on 2010-02-03
I have a security distro that is normally run as foot. It is not any easier or faster. You still have to enter the commands. Four letters does not change much. If you are dead set on running as root maybe you should get a different distro.

---

### Post by louieb on 2010-02-03
> **Martin McFly said:**
> ....I want to be root. And I'm decided.

Forums have rules - some don't allow posting password cracks. This one - read on [forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201") 

Like cracking passwords - logging in as root is out there - if you really want to -

---

### Post by Martin McFly on 2010-02-03
Thank you for your opinions. However, I really didn't intend to cause disturbance. Maybe you're right, it would be better to "let" something be root from time to time, but not at the all times. Anyway, I can just leave terminal run in background, logged as root if I need something, file commander I use (gnome / krusader) also are able to be "as root".

I also don't want to do any cracking, or breaking rules, I just thought it's normal thing. Maybe it is, maybe it's not, that's different question.

Anyway, fine by me, thanks for your contribution guys.

---

### Post by blur xc on 2010-02-03
> **Joeb454 said:**
> This is generally how I'll become root for extended periods of time.

If you're asking how to login as root - you're asking in the wrong place, as it isn't something we'll support on these forums.

I don't know if it comes standard, but my Ubuntu install, under applications -> accessories, has a root terminal launcher.  I don't know if I created it or not- it's been there a while and when I first started playing with ubuntu, I did a lot of stuff not knowing what it was I was doing.  You have to learn somehow...

BM

---

### Post by AlanR8 on 2010-02-03
One of the key reasons Linux is more secure than other operating systems is that you're NOT given root privileges by default. 

That's one of the major issues in the Doze community and why viruses are so malicious.

How much effort is it to "assume" root to do something specific? How many times during the day do you think you'd have to do this?

Your choice, but the system PROTECTS you!!!!

---

### Post by Iowan on 2010-02-03
[http://ubuntuforums.org/showthread.php?t=1397619]("http://ubuntuforums.org/showthread.php?t=1397619")

---


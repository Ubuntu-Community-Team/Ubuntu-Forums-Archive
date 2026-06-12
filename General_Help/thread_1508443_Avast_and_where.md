---
title: "Avast and where?"
date: 2010-06-13
forum: General Help
---

### Post by Dn4mycrownj on 2010-06-13
I have installed avast because it can pull viruses out of wine if necessary. I run this command #sudo sysctl -w kernel.shmmax+1280000000
this will get avast to load no problem. Now, can I put this in a file somewhere,  so i do not have to run the command before i run Avast. If i do not run the command i get some engine error. If i do add this command into a file permanently will it change my performance.

---

### Post by PsychoDevon on 2010-06-13
> **Dn4mycrownj said:**
> I have installed avast because it can pull viruses out of wine if necessary. I run this command #sudo sysctl -w kernel.shmmax+1280000000
this will get avast to load no problem. Now, can I put this in a file somewhere,  so i do not have to run the command before i run Avast. If i do not run the command i get some engine error. If i do add this command into a file permanently will it change my performance.

Go to system>preferences>startup applications, click "add" and put that command into the command input box.

---

### Post by Dn4mycrownj on 2010-06-13
do i have to put sudo in front of it?

---

### Post by Smart Viking on 2010-06-13
> **Dn4mycrownj said:**
> do i have to put sudo in front of it?


If you have to put sudo in front of it when you do it from the terminal, then you need to put sudo there too. :)

---

### Post by Dn4mycrownj on 2010-06-13
thank you

---

### Post by WorMzy on 2010-06-13
That won't work.

If you substitute the sudo for gksu, then it has more of a chance of working, as it'll give you a graphical prompt for your password.

A better solution would be to add the task to root's crontab:
```
sudo -i
crontab -e
```

I'm not familiar with cron myself, so I can't tell you what you'd need to add to crontab to get this command to run. However, someone else may be able to tell you, or [this link]("http://www.pantz.org/software/cron/croninfo.html") may help you figure out what needs to be written.

My guess is ```
@reboot sysctl -w kernel.shmmax+1280000000
```

---

### Post by Dn4mycrownj on 2010-06-17
The first way didnt work. I looked at cron does it run all the time before I set it up. I would rather not have something that is always running an extra process. 

I havnt tried wormzys way yet.

---


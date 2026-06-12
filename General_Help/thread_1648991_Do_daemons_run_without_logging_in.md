---
title: "Do daemons run without logging in?"
date: 2010-12-19
forum: General Help
---

### Post by Pithikos on 2010-12-19
I turned my old computer into a web server and I control it via SSH. 
What I noticed is that if I reboot the system then the server works(you can browse on the web pages etc) without even logging in. Is that normal? I googled a bit around but couldn't find any answer.

I also noticed that I can connect via SSH even if noone is logged in the system. Is that normal?

---

### Post by noah++ on 2010-12-19
Yes, this is normal for Linux and every other operating system I can think of. Although it is possible to launch programs like web servers and FTP servers as a logged-in user, it is most common for such programs to run as "services" or "daemons" detached from any particular user session. It is also common for such services to be automatically launched at boot time. What gets launched at boot time is configurable.

---

### Post by pfnorris on 2010-12-19
Both of the things you describe are normal behaviour on a Unix (or Unix like) system. A daemon on Unix/Linux is roughly parallel to a service in windows. These are functions that it is desirable to have running whenever the system is up, and are quite independent of any user activity, so it is not necessary for a user to be logged in for them to run.

SSH is a server daemon that allows you to connect to a system from a remote machine running an ssh client. Unless a system has been completely locked down you can normally connect to it either locally using a screen and keyboard, if you are sat in front of it; or remotely using a tool such as SSH if you are remote from it. In either case you will be required to log in. However you would be unable to log in remotely if the ssh daemon was not already running in the background on the server.

---


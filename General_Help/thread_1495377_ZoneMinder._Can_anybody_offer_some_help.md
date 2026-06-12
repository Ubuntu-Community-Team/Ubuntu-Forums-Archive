---
title: "ZoneMinder. Can anybody offer some help?"
date: 2010-05-28
forum: General Help
---

### Post by Roasted on 2010-05-28
I wanted to check out ZoneMinder so I installed it from the repos on my 10.04 64 bit desktop. At first nothing worked, but I found a thread: 

[http://ubuntuforums.org/showthread.php?t=1379559&highlight=zoneminder](http://ubuntuforums.org/showthread.php?t=1379559&highlight=zoneminder)

Which got things rolling properly. Okay fine, I can get in the web interface now. The problem is, I don't get prompted to log in. Ever. Every guide I read says "log in and then..." I'm not sure if I'm doing something wrong, but I have no idea why it aint working.

On top of that, I get right to the main screen. Okay, fine. According to a YouTube video regarding ZoneMinder, they made the comment that you can click "Options" on the right side and a popup window comes up with additional settings. One of the tabs is "users" to create users. I don't have that tab.

Certain things like that are coming up making me wonder what's going on. Can anybody offer some insight?

---

### Post by Roasted on 2010-05-28
up. :(

---

### Post by Roasted on 2010-05-31
Anybody?

---

### Post by Roasted on 2010-06-04
:confused::confused::confused:

---

### Post by SteveTPearce on 2010-06-04
Hi,

Just stumbled upon this topic when looking to solve another problem with ZoneMinder (now fixed)...

Anyhow, I think you'll need to check the "OPT_USE_AUTH" box (second from the top) on the "System" tab, otherwise ZM runs in an unauthenticated mode.

To login, use "admin" as the username and "admin" as the password (without quotes, naturally). From there you can create your normal users...

Hope that helps,

Steve

---


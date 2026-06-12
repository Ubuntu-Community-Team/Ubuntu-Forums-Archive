---
title: "FreeNX problem with opening programs"
date: 2010-09-23
forum: General Help
---

### Post by fenderlvr on 2010-09-23
I have Ubuntu 10.04 and I've set up FreeNX server on it. I use the Nomachine client for Windows to log into my home computer while I'm at work.
 
The other day I tried opening Chrome browser and nothing happened. So I clicked it a few more times and nothing. So I went ahead and just used Firefox.
 
When I got home that day I physically went to the computer and woke it up and about 20 Chrome windows were open.
 
So it looks like Chrome is launching in the wrong session. I'm logged in locally and through NX with the same user. Should I create a different user to log into the machine locally? Is there some way to bring these open windows over to my remote session?
 
A couple more things... the first time this happened I had opened Chrome locally and left it open. Also Dropbox does this as well. And locally there is an icon in the top notifications for Dropbox but not on my remote session. So I'm thinking if an app is already running locally can I not open a new instance on my remote session?
 
Please help, I'm pretty new to all of this and don't really understand how the different gnome sessions and logins work.

---

### Post by fenderlvr on 2010-09-23
I just found this and tried it out.  It didn't work.
 
[http://ubuntuforums.org/showthread.php?t=1513241&highlight=freenx](http://ubuntuforums.org/showthread.php?t=1513241&highlight=freenx)

---

### Post by fenderlvr on 2010-09-23
So I'm trying to figure this out and it looks like it was because Chrome is opened on my machine at home.
 
What I did was ps -A | grep chrome and the killed the process
 
Then Chrome launches fine in my remote terminal.
 
Is there some way to make it not behave like this?  Like I want it to always launch in my current window no matter what is open on my local machine.

---


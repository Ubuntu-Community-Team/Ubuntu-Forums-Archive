---
title: "Skype Crashes on UBUNTU"
date: 2012-09-28
forum: General Help
---

### Post by anspectrum on 2012-09-28
Hello All,

Ive got ubuntu precise pangolin and i feel like in heaven. :p

Ive observed a problem with Skype (Multiple versions including the latest one 4.0.0.8 ) on ubuntu. Audio / Video / Text / chat works smoothly and almost flawlessly. But the problem is I'm unable to send files while using Skype through Ubuntu. As soon as I select a file to send Skype simply crashes.

Has anyone else encountered the same problem..???

Second portion of the query is ; Since Skype has been acquired by Microsoft for quite a while now, its a possibility that support for Skype on Linux / Ubuntu ends after a while. Is there any equally good application..???

Ive tested Google video chat. But its laggy. Although audio was good and crispy. But video had jitter and delay. I must add this that Skype uses point to point (or IP to IP) conversation and does not route traffic through Skype servers (except at the time of Call Setup and some call control signalling). So what it means is that if you are on a LAN / Corporate Network and send big files using Skype, your files would transfer at LAN speed. Any ideas are welcomed....??

---

### Post by daslinkard on 2012-10-01
> **anspectrum said:**
> Hello All,

Ive got ubuntu precise pangolin and i feel like in heaven. :p

Ive observed a problem with Skype (Multiple versions including the latest one 4.0.0.8 ) on ubuntu. Audio / Video / Text / chat works smoothly and almost flawlessly. But the problem is I'm unable to send files while using Skype through Ubuntu. As soon as I select a file to send Skype simply crashes.

Has anyone else encountered the same problem..???

Second portion of the query is ; Since Skype has been acquired by Microsoft for quite a while now, its a possibility that support for Skype on Linux / Ubuntu ends after a while. Is there any equally good application..???

Ive tested Google video chat. But its laggy. Although audio was good and crispy. But video had jitter and delay. I must add this that Skype uses point to point (or IP to IP) conversation and does not route traffic through Skype servers (except at the time of Call Setup and some call control signalling). So what it means is that if you are on a LAN / Corporate Network and send big files using Skype, your files would transfer at LAN speed. Any ideas are welcomed....??

I saw on a Skype forum that someone made a new account and after doing so actually fixed the crashing issue.

Maybe this [link]("http://community.skype.com/t5/Linux/Skype-4-0-on-Ubuntu-12-04-crashes-and-logs-me-out/td-p/818438") will be useful for you.

---

### Post by anspectrum on 2013-02-02
Interesting facts. I stumbled upon the following thread 

[http://community.skype.com/t5/Linux/Skype-crashed-if-I-try-send-files/m-p/1275036/highlight/true#M3172](http://community.skype.com/t5/Linux/Skype-crashed-if-I-try-send-files/m-p/1275036/highlight/true#M3172)

and using some rational found that if skype is launched with root like "gksudo skype" or "sudo skype", then not only interface is more elegant but file transfer function works as well. Now I can send the file no matter how big is the size. :p

However, I don't want to run the skype with root privileges. Can someone find out any alternative to it.????

---


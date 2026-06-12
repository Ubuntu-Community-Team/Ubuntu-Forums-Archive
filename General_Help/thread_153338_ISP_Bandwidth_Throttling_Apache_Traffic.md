---
title: "ISP Bandwidth Throttling Apache Traffic?"
date: 2006-03-31
forum: General Help
---

### Post by eltaito on 2006-03-31
Haha...sorry if the thread title makes me look dyslexic or something....I typed it really fast without thinking about it

Hi, I have apache2 running on a Breezy Server install.  I am using the server to store files so I can access them when I'm not at home, but I am having some "bandwidth problems".  I used to have the same setup and was able to download files from my server at about 25-30 k/sec but after re-installing everything I can only get a max of maybe 6 or 7 k/sec.  I am on a cable internet connection (evil TimeWarner) so I should have more upload bandwidth than this.  Is there anyting in Apache that would be causing this slow down.  I thought maybe my ISP was throttling port 80 so I configured Apache to listen to another port (40000) and connected to my server via: "http://myserverIP:40000" and the speed was still the same. 

I guess what I'm asking is: Are there any settings that I should be aware of that would be causing this slow down? or is there a way to test if my bandwidth is being blocked/throttled by TimeWarner?  This speed is way too slow to make this server even remotely effective.

Edit: I guess I'll add in here that I do in fact have the router/NAT ports forwarded to my server box....I even went as far as enabling DMZ (all ports open to the server) in an attempt to fix this problem

---


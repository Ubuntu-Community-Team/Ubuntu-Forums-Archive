---
title: "reset PPPoE when modem looses connection"
date: 2009-08-19
forum: General Help
---

### Post by xgm541 on 2009-08-19
I am having an issue with my PPPoE connection.

Basically, I cant figure out how to do port forwarding on this modem. Whatever I try -- it doesnt work. So I'd like this to not be a suggestion. My bypass is to use PPPoE (pppoeconf) to get a separate IP from my modem, so i can open various ports. 

however, when my DSL disconnects (when it rains, etc), my linux box doesnt stop the pppoe connection and reconnect it. So basically I am stuck without internet. I am going away to school once again this year and I will be far away, and the only thing that seems to fix the  issue is running the command "sudo /etc/init.d/networking restart". But i cannot be at the computer to do that at all times.

so is there any way I can run the networking restart command whenever my linux box wont connect to the internet? My solution would be to have my machine ping google every 5 minutes, and if it doesnt receive a reply, to reset the network. Is that possible?

---


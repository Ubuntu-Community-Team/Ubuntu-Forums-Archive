---
title: "Got some problems with HLDS"
date: 2011-03-18
forum: General Help
---

### Post by Alexzzdagreat on 2011-03-18
Hello. Well i got some problem with my HLDS ( CS 1.6 server). Everytime i close my ssh panel, after closing it. The server dies. So if i want the server to be online, i have to have the SSH client on. This is the command i use to start the server.
> 
./hlds_run -game cstrike +ip 85.25.162.100 -port 27015 +map awp_rooftops +maxplayers 15 -autoupdate 

I have looked around on other forums. But no anwers. So i decided to post on this forum. I am using ubuntu 10.10. VPS is hosted by ServerFFS. 

I dont understands what the problem?

Someone posted to try using screen. He gave me this tutorial: [http://www.go2linux.org/linux/2010/04/linux-screen-command-tutorial-740](http://www.go2linux.org/linux/2010/04/linux-screen-command-tutorial-740)

But i dont get it either. So how can i fix this?

Thanks, Alex

---

### Post by tredegar on 2011-03-18
If screen is too complicated for you, you could try **nohup**```
[COLOR="Red"]nohup[/COLOR]  ./hlds_run -game cstrike +ip 85.25.162.100 -port 27015 +map awp_rooftops +maxplayers 15 -autoupdate 
```
But screen is worth learning, and the link you were given explains it clearly.

---

### Post by Alexzzdagreat on 2011-03-18
I have tried nohup. Still same problem. And i dont understand what to do with screens :S

Server dosent even start with nohup.

---


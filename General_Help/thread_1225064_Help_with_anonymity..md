---
title: "Help with anonymity."
date: 2009-07-28
forum: General Help
---

### Post by Linux_Nick on 2009-07-28
I'm new to Linux - Ubuntu and I'm having enormous amounts of trouble grasping some basic things.

I want to install Tor and Privoxy and I have followed some instructions to do so but have only been met with frustration. I have used the Add/Remove programs and I have also tried to install it using the terminal.

Install SEEMS to go fine and I have edited the config file but upon testing it does not seem to work.

I have experience with Tor and Privoxy, just sketchy on Linux. 

If Tor and Privoxy are running, is it supposed to put an Icon in the system tray? Does it even start up when you install it? How do you run it once it's installed?

Help.

---

### Post by Chronon on 2009-07-28
They should both start automatically.  You can check whether or not they are running with the System Monitor.  You can start/stop them with 
```
sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start
sudo /etc/init.d/tor stop
sudo /etc/init.d/privoxy stop
```

I prefer to not automatically start them but manage them with Vidalia.  I use FoxyProxy in Firefox to utilize TOR.

---

### Post by Soul-Sing on 2009-07-28
Yep manage them wth the TOR-button in firefox, foxyproxy or vidalia.
vidalia is the repos. of jaunty I believe.

---

### Post by Linux_Nick on 2009-07-28
> **Chronon said:**
> They should both start automatically.  You can check whether or not they are running with the System Monitor.  You can start/stop them with 
```
sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start
sudo /etc/init.d/tor stop
sudo /etc/init.d/privoxy stop
```I prefer to not automatically start them but manage them with Vidalia.  I use FoxyProxy in Firefox to utilize TOR.

Yeaaaaaaaah-no. Im going back to Microsoft I think. Cheers.

---


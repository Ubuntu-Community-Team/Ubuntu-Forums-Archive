---
title: "ssh for remote support"
date: 2011-02-28
forum: General Help
---

### Post by Hippytaff on 2011-02-28
I've got a laptop for the missus's mother and I'm going to install ubuntu on it. They are getting wireless next weekend. Travelling for two hours to fix something or whatever isn't an option so I was thinking of setting up a ssh effort to be able to do anything that needs to be done remotely...however, neither of us have static IPs. I know little to nothing about this, so any help and previous experience with similar endeavours would be greatly appreciated.

---

### Post by spiky001 on 2011-02-28
See if this helps with static ip [http://www.dyndns.com/about/home_solutions.html](http://www.dyndns.com/about/home_solutions.html)

---

### Post by Mickser_52 on 2011-02-28
look at dyndns.com they will give you a domain name and an updater which changes the domains ip when it is changed by the service provider. Also Remote Desktop Viewer which comes with Ubuntu allows you to see and remotely control another laptop if you know its ip (or dyndns name) and, if necessary, password. Not sure if you need to set up something on the remote computer first. Not as secure as ssh if that is important

---

### Post by spiky001 on 2011-02-28
I have used ssh to a non static ip but it means knowing what the ip is when you wanna connect

---

### Post by wd5gnr on 2011-02-28
Here's what I do for my mom. 

I have a single icon on her desktop drug over to one side that says "GIVE AL CONTROL". 

That icon starts her VNC server in reverse mode where it reaches out to a client viewer. How you do this depends on your VNC server of choice but you do not need to know her IP address and her firewall can be restrictive inbound. What you do need is an IP yourself. Go to [www.dyndns.org](www.dyndns.org) and get one. So say you are someip.dyndns.org your command line might look like:

x11vnc -connect someip.dyndns.org

That's the set up on her side.

On your side, you need to keep dyndns apprised of your IP (your router probably does this or there are free tools) and you need to keep your VNC ports open on your router. But presumably YOU know how to do all this (unlike mom). Then you run:

vncviewer -listen

Nothing will happen until you tell her to click the icon you've already setup.

Boom. You have control of her desktop.

Easy. Not ssh, but easy and then you can open a terminal or do anything else you want to do.

---

### Post by Hippytaff on 2011-02-28
Thanks all...very helpful. Security isn't that important so VNC with the Give the Hippy Control link looks like the easiest option. Just got to do the dyndns thing.

Spikey, trying to even begin to get an IP from the mother in law is a whole world of confusion :-D

Thank you all :-)

---


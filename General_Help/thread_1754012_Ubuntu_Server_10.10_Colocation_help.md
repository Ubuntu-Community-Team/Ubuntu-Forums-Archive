---
title: "Ubuntu Server 10.10 Colocation help"
date: 2011-05-09
forum: General Help
---

### Post by vapid2323 on 2011-05-09
[COLOR=black][FONT=Verdana]Total noob here,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have worked with SSH on a VPS and Ubuntu 10.10 but because of my needs I need to upgrade the server. I plan on doing a collocation but I keep getting concerned about the things that might go wrong, like if I shutdown the server.... how do I make sure it starts back up? [/FONT][/COLOR][COLOR=black][FONT=Verdana]I have done lots of Google searches but I am still a little concerned as most things I find don’t clearly state what I need to do :)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I guess the things I would like are the ability to see my cpu and network usage over 24h periods, I know about the "top" command but a graph on a website would be nice.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]How do I make sure my server can be started if for some reason its shut off?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I should have the server built later this week, so I can hopefully act on any advice next weekend :)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I searched but if you have a good site I should be looking at please let me know. I am tech savvy, but this topic is new to me.[/FONT][/COLOR]

---

### Post by bodhi.zazen on 2011-05-09
Build the server and make sure it boots. You can connect and test ssh and reboot via ssh.

If everything is working, the last thing you do is set a static ip , then you ship it off.

Your CoLoco will offer tech support, usually at a decent rate if you have problems.

In terms of monitoring, google search. I usually use top and I do not monitor cpu use/load 24/7/365.

---

### Post by vapid2323 on 2011-05-09
> **bodhi.zazen said:**
> Build the server and make sure it boots. You can connect and test ssh and reboot via ssh.
 
If everything is working, the last thing you do is set a static ip , then you ship it off.
 
Your CoLoco will offer tech support, usually at a decent rate if you have problems.
 
In terms of monitoring, google search. I usually use top and I do not monitor cpu use/load 24/7/365.
 
Thanks for your help, 
 
You make it sound simple :) Hopefully thats going to be the case for me!

---

### Post by collisionystm on 2011-05-09
> **vapid2323 said:**
> [COLOR=black][FONT=Verdana]Total noob here,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have worked with SSH on a VPS and Ubuntu 10.10 but because of my needs I need to upgrade the server. I plan on doing a collocation but I keep getting concerned about the things that might go wrong, like if I shutdown the server.... how do I make sure it starts back up? [/FONT][/COLOR][COLOR=black][FONT=Verdana]I have done lots of Google searches but I am still a little concerned as most things I find don’t clearly state what I need to do :)[/FONT][/COLOR]


> Just avoid typing shutdown ;)

```
shutdown -r 0
``` Restarts server
```
shutdown -P 0
``` Powers it off
 [COLOR=black][FONT=Verdana]I guess the things I would like are the ability to see my cpu and network usage over 24h periods, I know about the "top" command but a graph on a website would be nice.[/FONT][/COLOR]
[QUOTE][URL="http://www.zentyal.com/"]
http://www.zentyal.com/ [/URL]
Built on Ubuntu 10.04. Free and magical. I use it as a PDC file server for 100 users.

[http://www.nagios.org/](http://www.nagios.org/)

Already In software center I believe.....


[COLOR=black][FONT=Verdana]How do I make sure my server can be started if for some reason its shut off?[/FONT][/COLOR]
 
> First thing you do, Go into the Bios and change the Powersettings. It will say something like, Recovery after power failure. You can choose, STAY OFF, LAST, OR POWER ON

You obviously want, POWER ON[COLOR=black][FONT=Verdana]I should have the server built later this week, so I can hopefully act on any advice next weekend :)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I searched but if you have a good site I should be looking at please let me know. I am tech savvy, but this topic is new to me.[/FONT][/COLOR][/QUOTE]

Hope that helps!

---

### Post by vapid2323 on 2011-05-09
> **collisionystm said:**
> Hope that helps!
 
THANK YOU! That was great!
 
I will follow up and let you know how it works out!

---

### Post by bodhi.zazen on 2011-05-09
On a public server like this I would advise two things:

1. Do not install additional software / applications unless absolutely necessary as each additional application introduces vulnerabilities.

You can determine if the host is up but connecting to the web page, ping, or ssh, do you really need nagios ?

This extends to graphical apps/ desktops. Use ssh and if you MUST have a graphical interface look at the web based options (webmin or similar).

2. Set up a local mirror of the server, running in Virtualbox / VMWare / KVM. Always test new applications / upgrades on the test server first, then if all goes well the production server. You do not want to find that upgrading package foo breaks the server, you want to discover that on your test server.

While it is not perfect, it prevents a lot of problems.

3. Learn to do backups and copy the backups from remote to a local location.

Also know how to restore from backup from remote.

4. Use keys, and disable password authentication for ssh. Keep at least two copies of the key in at least two locations locally.

5. Time how long it takes the server to reboot. One minute ? Two minutes ? How long does the process normally take ?

OK, so five things =)

---

### Post by vapid2323 on 2011-05-09
> **bodhi.zazen said:**
> On a public server like this I would advise two things:
 
1. Do not install additional software / applications unless absolutely necessary as each additional application introduces vulnerabilities.
 
You can determine if the host is up but connecting to the web page, ping, or ssh, do you really need nagios ?
 
This extends to graphical apps/ desktops. Use ssh and if you MUST have a graphical interface look at the web based options (webmin or similar).
 
2. Set up a local mirror of the server, running in Virtualbox / VMWare / KVM. Always test new applications / upgrades on the test server first, then if all goes well the production server. You do not want to find that upgrading package foo breaks the server, you want to discover that on your test server.
 
While it is not perfect, it prevents a lot of problems.
 
3. Learn to do backups and copy the backups from remote to a local location.
 
Also know how to restore from backup from remote.
 
4. Use keys, and disable password authentication for ssh. Keep at least two copies of the key in at least two locations locally.
 
5. Time how long it takes the server to reboot. One minute ? Two minutes ? How long does the process normally take ?
 
OK, so five things =)
 
All VERY good things, thank you! I might work on #2 tonight, I dont really need the hardware for that one
 
Yah I am going to try and limit the software to the basics. apache2, MySQL, phpmyadmin (because I am horable with command line SQL statments) and some others.

---


---
title: "Ubuntu desktop with virtual machines"
date: 2011-07-15
forum: General Help
---

### Post by Crazybonze on 2011-07-15
My friend and i built an AMD desktop to host stuff on the internet. Mostly a Minecraft server and a website for our freelance business that we are starting up in the next couple months and then a few other things we may need like a cloud and our own email. With all of the different roles that this desktop will be filling i was thinking it would be a good idea to have Ubuntu desktop installed and then use Virtualbox to install MineOS+ (the server built for the Minecraft game) and Ubuntu server to handle the website and another one for the cloud. Also we will be hosting other small personal websites for a few other people.

I would like to have Ubuntu desktop on the computer because my friend is not as involved in computers as i am and he will have to work on it when i can not get to it (he would be completely lost if he did not have a GUI). Are there any issues with this configuration that i may have or are there any better alternatives that i could use?

---

### Post by seawolf167 on 2011-07-15
> **Crazybonze said:**
> he would be completely lost if he did not have a GUI

I see this as being an issue with the server-related items you mention.

Here is the [Virtual Box article]("https://help.ubuntu.com/community/VirtualBox") to get that up and running - its pretty easy, just download and install Virtual Box, then run through the prompts to setup a new machine.

As for running a server for server roles (instead of a desktop), Webmin is a great graphical tool for that which lets you manage your server via a web browser. The Webmin homepage is [here]("http://www.webmin.com/"), and their wiki page is [here]("http://doxfer.webmin.com/Webmin"). You might want to take a look at those.

I suggest running the server version (10.04 LTS) and ifffff you cannot get by without a desktop you can always install that later, but the reason servers usually don't have a GUI is because you don't need the GUI processes eating CPU cycles (*especially *on a headless server). The 10.04 ubuntu server guide is located [here]("https://help.ubuntu.com/10.04/serverguide/C/index.html").

See if those give you some more to think about or point you in workable direction.

---

### Post by bodhi.zazen on 2011-07-15
> **seawolf167 said:**
> but the reason servers usually don't have a GUI is because you don't need the GUI processes eating CPU cycles (*especially *on a headless server).

Actually, IMO, it is for security reasons. Less packages == less vulnerabilities.

Desktop GUI such as gnome , xfce, fluxbox add very little to managing a server as most of server management is editing text files , updating, installing, or configuring services.

You can use any number of web based graphical interfaces, webmin, phpmyadmin, etc.

---


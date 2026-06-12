---
title: "Newbe ? on Ubuntu Server"
date: 2012-01-30
forum: General Help
---

### Post by raxhunter on 2012-01-30
Sorry if this is too long, but I think the more info availible the better :popcorn:.
Ill start off with my server. Currently I have 1 of 2 servers up and running (well kinda). The srever I am currently working on is a Dell Poweredge 1800. I have a Raid Array curently up and going. My ultimate goal was to use this server to serve media (I.E. files, pictures, movies, music and possibly games ) to my ps3 and family members. I downloaded the Ubuntu server iso and installed it on my make shift home server. When the server boots up I get a log on line and once I log on suedo screen pops.. I am unsure if this is how Ubuntu works. I dont no anything about suedo commands. I was wanting to know if the Ubuntu server that I installed is stand alone. I was under the impression that it would kinda look like a Windows version of server software.. Do I need to install something else with it? :confused:

---

### Post by Dangertux on 2012-01-30
Ubuntu server does not include a graphical user interface. If you want one you will need to install x server and your desktop environment of choice. This is not recommended for a server as it wastes resources. 

Might be time to delve into the CLI

---

### Post by shri19 on 2012-01-31
do,
sudo apt-get install ubuntu-desktop
which will install GUI on the server. But you can also use standard  desktop edition as it will serve most of the needs in your case.


--
He who saves one soul saves the world entire

---


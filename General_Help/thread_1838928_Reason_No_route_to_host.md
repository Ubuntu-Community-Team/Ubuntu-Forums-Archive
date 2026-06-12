---
title: "Reason: No route to host"
date: 2011-09-04
forum: General Help
---

### Post by Nucleus1 on 2011-09-04
[COLOR=red]Error:[/COLOR] I could **not** see your service on **70.59.39.175** on port (**25565**)
Reason: No route to host

i get this error when i check the open port on my unbuntu server. i use lynx a text based browser. does anyone know what could be the cause of this problem? i have searched for a couple hours on the internet but have gotten almost no where. thank you for the help in advance.

also i can connect via openSSH, and this box is set as DMZ.

//nucleus

---

### Post by zero2xiii on 2011-09-04
Wow, lacks some detail.

What are you trying to do? What site are you trying to connect to? Why are you using a text based browser? Can you connect using a normal web browser? Can you connect from another computer? Can you access other site? etc.

Please give more detail

Also post the output of "route" of both the client and the server (please indicate clearly). Also tell us about any networking hardware between you and the host, eg FIREWALLS, ROUTERS, etc..

---

### Post by Nucleus1 on 2011-09-04
Sorry for the lack of detail.

first off i am trying to host a server for a game called Minecraft so people are connecting on the port 25565. I forwarded all my ports on my router, or better yet set the box as DMZ. i used a text based browser to view whether or not the ports were open at Canyouseeme.org. 

[COLOR=red]Error:[/COLOR] I could **not** see your service on **70.59.39.175** on port (**25565**)
Reason: No route to host

as far as i am concerned there are no firewalls on my unbuntu server unless one came with the installation. I can connect to port 22 fine but not 25565. i am using a Q1000 router also btw.

---

### Post by zero2xiii on 2011-09-04
> first off i am trying to host a server for a game called Minecraft so people are connecting on the port 25565. I forwarded all my ports on my router, or better yet set the box as DMZ. i used a text based browser to view whether or not the ports were open at Canyouseeme.org.

Oka. Just hosting a sever for local people is easy. For the internet, is harder.

Just setting the pc as the DMZ wont help, is the server setup correctly to be a DMZ? You cant just point the router to the computer, as a dmz server.

Please view [http://portforward.com/](http://portforward.com/) for how to setup your NAT on your router to correctly translate internet traffic to the local minecraft serer.

Good luck

---

### Post by zero2xiii on 2011-09-04
[http://portforward.com/english/routers/port_forwarding/Actiontec/Q1000/Minecraft_Server.htm](http://portforward.com/english/routers/port_forwarding/Actiontec/Q1000/Minecraft_Server.htm)

Just to save you some time..

---

### Post by Nucleus1 on 2011-09-04
Ok i know how to port forward. i have already ran a minecraft server off windows and it worked fine. not a problem in the world. but when i switch to unbuntu it wont work.

---

### Post by Iowan on 2011-09-04
Bumping no more than once/day (24 hours) is generally adequate/polite. Thanks.

---


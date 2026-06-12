---
title: "Help please - Apache webserver and motion ..... how to!"
date: 2010-04-10
forum: General Help
---

### Post by mxgeldar on 2010-04-10
I am new to ubuntu, motion and apache .... all in all a perfect start!
 
I have ubuntu 9 which is working fine.  Apache 2.2 which again is in default format and works fine (can connect to localhost and it all works!).  I have motion installed with two webcams and all is working perfectly with motion and the capture files are created.  The webcams can be seen on ports 8081 and 8082 so basically everything is working 100%.
 
What I now want to do is to connect to the webcams across the internet.  How do I do this?  I dont understand how to and wonder if anyone can assist with the apache configuration that I need to do........
 
Hopefully someone will be able to help ....... I'm loving this ubuntu project and every day is another learning opportunity at the moment!

---

### Post by wbar2 on 2010-06-29
You need to do three things:

1. If you have a firewall setup, you need to allow ports 8081 and 8082. If you are using ufw you would type this in the terminal:

```
sudo ufw allow 8081
```

Do the same thing for port 8082.

2. If you have a router, you need to setup port forwarding from those two ports to your server. Find out the ip address of your server (where the cameras are connected). Type "ifconfig" in the Terminal, and the line that says "inet addr:" will give it to you. Then go to your router's local ip (something like 192.168.1.1) and go the options where it says something like "applications and gaming." Choose the ports you want to forward and forward them to the ip of your server.

3. Figure out the external ip address of your system. Just Google "what is my ip" and plenty of sites will tell you what they are. After that just type in that ip with the ports and see it work!

---


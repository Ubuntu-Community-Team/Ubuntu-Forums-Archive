---
title: "Remote ssh/web access with Internet Connection Sharing"
date: 2011-01-23
forum: General Help
---

### Post by snizzapple on 2011-01-23
Hello all,

If anyone can help me with that, that would be awesome. 
Here is the situation. 

I have a computer running an ubuntu server connected to a laptop running xp with ICS (internet connection sharing) enabled so i can access the internet on the server. 

ubuntu --> xp laptop (ics) ----> Internet. 

My question is i would like to remote ssh to the sever, or view a webpage on the websever but when i type in the ip address on a diff computer over the network i cant connect. 

How do i set it up so i can connect to the server from an outside computer?

And i rather not buy a wireless card for the server, its somewhat of an old computer.

Any help would be great, thanks.

---

### Post by sandy8925 on 2011-01-23
First, make sure openssh-server is installed on the Ubuntu Server. Then try to ssh into the server.

---

### Post by snizzapple on 2011-01-23
yeah i set up all that, i can access all from the laptop connected to the server, just not from a computer thats not directly connected, but connected to the wireless network. I can connect to the laptop thru the wireless network too. 

Will i need to do any forwarding, if so how? if not then what do you think a fix would be.

---


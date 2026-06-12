---
title: "Cloud Computing with UEC..?"
date: 2010-02-05
forum: General Help
---

### Post by ShinHadoken on 2010-02-05
Alright, I'm interested in the idea of a private cloud that UEC can supposedly create. How do I do this, I mean, how does it work practically? I make the "cloud controller" whatever, and then a node. What's a node, and what is its function? Is my goal to run virtual machines on one (or more) computers, and then log into them remotely? How does this occur? Once I have an image running, how would a client access it? These are some very big practical application holes that I have not been able to answer after searching through days of online stuff. Can someone help me understand this? I would very much appreciate it.

---

### Post by cariboo on 2010-02-06
> I make the "cloud controller" whatever, and then a node. 

A cloud computing system is usually a cluster of computers, one is the controller and the rest of the computers are the nodes, in the case of cloud computing the nodes are more for redundancy then for distributed processing.

A cloud computing system is usually accessible form the internet, so you will have to setup some sort of secure web server.

For starters, have a look at the [Server Guide]("help.ubuntu.com/8.04/serverguide/C/index.html") on how to set up a server, and also covers Virtualization.

---

### Post by ShinHadoken on 2010-02-06
So let's see here. I'm going to have at least two computers--one cloud controller, and at least one node. The only purpose for the nodes is redundant disk storage(?). After this is set up, I install an image, Ubuntu for example, on the cloud controller. People can then log into the website and run programs through this Ubuntu image in their... browser?

---

### Post by ShinHadoken on 2010-02-06
Or do they use virt-viewer?

---

### Post by ShinHadoken on 2010-02-07
Bump please

---

### Post by ShinHadoken on 2010-02-07
I just don't understand *_exactly_* how UEC is supposed to work. I understand it conceptually, but I don't see how to implement it.

---

### Post by ShinHadoken on 2010-02-07
The only documentation I can find only shows me how to install cloud controllers/nodes, not how to use them. Can anyone help me out?

---

### Post by ShinHadoken on 2010-02-15
Any update on this?

---

### Post by pazsion on 2010-02-15
right, i'mthinking thesamething..i dont'want idle storage...=c
backup and v Iraid is awesome... if this is possible..
but i'm gonna want to  know, what machine is idle/working and on what task,how much of what resource, and are they shareing and completeing this flawlessly..if there is something that needs tweaking i wanna be able to do it

If friends could log in? to my cloud and also share resources that be nice.. if it doesnt lag etc..


i'm d/ling 8.04 lts server nowfor some old p3's and a socket370..

i wantto makethesedo some combined+cloud computeing :p

---

### Post by ShinHadoken on 2010-02-17
Hey pazsion, how did your Cloud experience go? Find out anything?

---

### Post by padecio_may_rende on 2010-03-19
we had already install the UEC..the problem is that we don't know how to run images or files using UEC..what will be the commands to do this pls help....

---

### Post by duanedesign on 2010-03-20
Had these marked for research, thought I would share them in hopes they would be helpful.

Ubuntu Wiki
[https://help.ubuntu.com/community/Eucalyptus](https://help.ubuntu.com/community/Eucalyptus)

This site has Discussion Forums, Community Papers and Guides.
[http://open.eucalyptus.com/](http://open.eucalyptus.com/)

Here is an overview of the Documentation on the Eucalyptus site
[http://open.eucalyptus.com/wiki/EucalyptusOverview](http://open.eucalyptus.com/wiki/EucalyptusOverview)

You can also find help in the #ubuntu-virt, #eucalyptus, and #ubuntu-server IRC channels on Freenode.

---

### Post by kiranmurari on 2010-03-31
@ ShinHadoken
@ padecio_may_rende

Please take a look at the following links which might help in bundling images and starting instances of these images:
[http://kiranmurari.wordpress.com/2010/03/29/uec-bundling-windows-image/](http://kiranmurari.wordpress.com/2010/03/29/uec-bundling-windows-image/)
[http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec/](http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec/)

Hope that helps.

---


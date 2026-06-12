---
title: "Help requested setting up remote access"
date: 2010-10-30
forum: General Help
---

### Post by bouncingwilf on 2010-10-30
As the title implies, I'm try to assess the viability of of setting up remote administration on a distant machine. Just for background, the computer I wish to administer is located on a boat in Southern Ireland while I'm in SE England. Sadly, the the boat operator is a far better fisherman than computer user and every now and then some rogue sensor numbers get captured by the boat's computer and these eventually need operator intervention. Anyone who has tried to talk a non PC literate user through correction routines over a dodgy mobile telephone while the said user is trying to operate mouse/keyboard in an Atlantic swell will appreciate the problem.

However, there is a fairly good mobile phone broadband signal available in the area so I was wondering if there was anyway I could set up a point to point connection with the boat over this medium. That would allow me to administer the machine remotely.  If this is at all feasible, I would be grateful is someone could point me in the direction of the appropriate tutorials to read.



Bouncingwilf

---

### Post by matt_symes on 2010-10-30
Hi

You have an unusual job i think. What is the speed of the connection to the boat? How reliable is it? What is the QOS like? These will be the main factors that determine the feasibility of what you are trying to do. I would run tests to determine this before i did anything

Can you use the command line? If so try SSH as it uses minimal bandwidth (without X11 forwarding anyhow). This is a basic set up guide but read around. I use openSSH.

[http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/](http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/)

If the connection is quite good you could try VNC (maybe tightVNC in the repos). This will take more bandwidth but after a full screen push only screen changes are pushed. This will give an overview.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Both methods are encrypted.

BTW What are the specs of both your and the boats PC.

---

### Post by bouncingwilf on 2010-10-30
Thanks for your response, In answer to your questions

a) Speed and QOS are as yet undetermined but allegedly circa 1mbs and goodish. 

b) As a former sysadmin on a unix system from the days before such luxuries as GUI shells, I should be able to cope with the cli (although my memory has faded somewhat over 20+ years!)

c) Realistically, 95% of the maintenance can be accomplished by just pulling copies of files off the target machine, "massaging" them and the stuffing them back where they came from. i.e. a dropped connection should not be catastrophic! (why not use email? I hear you say - well there are a few other minor adjustments needed from time to time)

d) My desktop is AMD-64bit with a couple of gig of ram while the target machine uses the IntelDM510 dual atom board, also with 2gb. Both machines are running 10.04 but I may set the Intel box up with Lubuntu just to lighten things up a bit.


I am in the fortunate position of having a "spare" Intel box and 3Mobile modem which I can set up locally as a test machine and if I can get some sort of system working, well, I'll pop over to Ireland for a few days fishing and swap the boxes over!

Bouncingwilf

---


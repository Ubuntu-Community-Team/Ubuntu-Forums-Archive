---
title: "Go to 64bit or 32bit server w/ Nvidia?"
date: 2009-07-25
forum: General Help
---

### Post by hambone79 on 2009-07-25
I have a processor that supports 64 bit but I am currently running the 32 bit version of Ubuntu 9.04. The main reason for this is that I currently do contract engineering work from home and I run Pro/Engineer Wildfire 2.0 and 3.0 which are only available in 32bit. Recently I have been running into some issues with memory (large models - entire pieces of construction equipment) and I decided to go ahead and upgrade my workstation from 2GB to 4GB of RAM. Unfortunately Ubuntu 32bit only recognizes the first 2.5GB of RAM.

I'm trying to decide if I want to take the plunge and try to get Pro/E up and running on Ubuntu 64 bit, but I have heard alot of horror stories. I have also tried to install the 32-bit server kernel to give me access to all of the RAM, but I was unable to get the NVidia drivers working. 

Is there anyone that can give me some advice on this? Will my 32bit applications run ok on 64bit?

---

### Post by SuperSonic4 on 2009-07-25
For the most part yes, they will work although the 32 bit libs will be needed (Synaptic handles them)

As for nvidia I've never had any problems with their driver in 64bit - indeed nvidia make a special 64 bit driver rather than a patched 32 bit one so if the repo version does not work you can still manually install

---

### Post by theremper on 2009-07-25
I use the 64bit version of jaunty without any problems and I have a nvidia card. Everything went flawless. untill I used the 64bit version I was stuck using windows becuase I use a web app that for some reason ran slow in the 32bit version. after I switched to the 64bit version it ran faster than it ever did in the 32bit version or in windows. I have noticed massive improvement in areas dealing with graphics processing and 3d rendering over the 32bit. 

The only down side is getting the 64bit version of non free flash to work is a pain but it can be done in under five minutes if you need any help write me [email]theremper@gmail.com[/email]

---

### Post by SuperSonic4 on 2009-07-25
> **theremper said:**
> I use the 64bit version of jaunty without any problems and I have a nvidia card. Everything went flawless. untill I used the 64bit version I was stuck using windows becuase I use a web app that for some reason ran slow in the 32bit version. after I switched to the 64bit version it ran faster than it ever did in the 32bit version or in windows. I have noticed massive improvement in areas dealing with graphics processing and 3d rendering over the 32bit. 

The only down side is getting the 64bit version of non free flash to work is a pain but it can be done in under five minutes if you need any help write me [email]theremper@gmail.com[/email]

```
sudo apt-get install flashplugin-nonfree
``` is very hard :p

---

### Post by colin-m on 2009-08-07
There is an excellent how-to at [http://www.youtube.com/watch?v=W6VTnBrbNSs](http://www.youtube.com/watch?v=W6VTnBrbNSs) It shows how to install flash player 10 64 bit without using the command line. Just follow the installation procedure, then restart firefox and enter "about:plugins" (without the ") as the web address. You should find that shockwave flash 10 has been installed.
It worked for me!

---

### Post by colin-m on 2009-08-07
Somehow an emeticon got installed. The command should be "aboutplugins", with a colon between about and plugins.

---


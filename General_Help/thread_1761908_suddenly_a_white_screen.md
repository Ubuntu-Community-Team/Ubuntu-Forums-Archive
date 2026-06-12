---
title: "suddenly a white screen"
date: 2011-05-18
forum: General Help
---

### Post by waddleone on 2011-05-18
Dear all

I have Ubuntu 9.10 installed as a dual boot on my Dell Vostro 1310 (nVidia graphics card).  After a year of successful use of Ubuntu, one day after entering my login details I was greeted by a white screen with a line down the middle.  I don't know why this suddenly happened, although I suspect I may have accidentally hit the upgrade button and then switched off the laptop mid-install or something.  I can access the recovery mode and have copied off the important data onto an external drive.  I would like to repair the installation, rather than reinstall, as there is some software that took some work to make operational on there and I also don't want to risk messing up the windows partition.

I'd be grateful for any help.  Thanks in advance.

Sam

---

### Post by jerrrys on 2011-05-19
in terminal enter 
**cat /etc/lsb-release** to see if you updated or upgraded

---

### Post by waddleone on 2011-05-19
It just says:

distrib_id=Ubuntu
distrib_release=9.10
distrib_codename=kermic
distrib_description="ubuntu 9.10"

I am pretty sure I've always run 9.10.

Any further ideas would be really appreciated.

Thanks for your help.

Sam

---

### Post by jerrrys on 2011-05-19
try

sudo apt-get -f install

this will repair broken packages; if you have any

---

### Post by waddleone on 2011-05-19
Thanks for your help.

I tried this and it ran ok and asked me to run autoremove as well - which I did.  Unfortunately I've still got the same problem.

I realised during this process that the disk was full and I made some space on the hard drive.  

I also tried to run sudo apt-get update && sudo apt-get upgrade and got lots of messages saying failed to fetch "......"

Any more ideas - thanks for your continued help.

Sam

---

### Post by jerrrys on 2011-05-19
is this what you seen?

[ATTACH]192660[/ATTACH]

404...not connecting with server or not finding packages, something like that

lets make sure that you still have the right ones;  in terminal

sudo nano /etc/apt/sources.list

and check to be sure all sources say karmic somewhere in them

---

### Post by waddleone on 2011-05-21
Thanks again for your help.

Everything seems to be karmic....

One thing I did wonder about, is that the battery life is very bad and I wondered whether it might not be getting enough power to run the graphics card?....

Any further ideas would be appreciated.

Sam

---

### Post by jerrrys on 2011-05-21
sorry for the delay in getting back to you.  weekends get a bit busy

lets eliminate the hardware.  still got your live cd laying around?  or for that matter any iso, just to check your laptop with.

---


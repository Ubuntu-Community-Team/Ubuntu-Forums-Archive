---
title: "Best Selection.. Desktop or Server?"
date: 2009-06-29
forum: General Help
---

### Post by Beaumeri on 2009-06-29
Hi everyone,
 
I'm a network secialist that heve been working with the MS environment for years. 
 
Lately I got a Dell Peweredge 2600 server and I'm now looking to make it my personal files server and also a backup for my main computer in regards of accessing emails, paying bills online and quick web research. It would also be nice to be able to stream video from it and connect my PS3 as well.
 
The system is a Dual Xeon 3.2 with 5 GB of RAM. It has 2 SCSI 36gb HDD in mirror connected to a PERC4/Di card for the OS. I'm currently in the process of buying a 3Ware 9550SXU-8LP and will be installing 6 SATA II (2 TB) drives the 6 bays of the PE2600 server. At the same time I'll be relocating the 2 SCSI drives to the upper bays and will be removing the SCSI backplane to make room for the SATA cables. 
 
I want to use RAID to protect my data.
 
I've installed the server release of Ubuntu but working from the command line seem a bit challenging for now as I have limited time to research / trial and errors.
 
Here's the to option I was thinking of:
 
1- Install the desktop release and configure it also for file sharing.
 
or
 
2- Install the server release and load the GUI for on it for my occational mail/web needs when my PC experiments goes bad and I need acces to the web.
 
Any help / recommendation is more then welcome as I'm trying to build something solid (software side) with this server.
 
Best Regards
 
Beaumeri

---

### Post by Celauran on 2009-06-29
The end result will be basically the same. You can add in the GUI now since you've already got the base install up, running, and configured. It can always be removed later.

---

### Post by AINTEZ86 on 2009-06-29
As far as setting it up to share files I found this tutorial extremely helpful... 
[http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)
 
You ought to have a file server up and running in no time (and if you want a web server as well)
 
As far as sharing for your PS3 running a Media Tomb Server works for me. Search google for a tutorial...it took some tweeking to make that work for me but now it works great.

---


---
title: "General server / user setup"
date: 2011-07-30
forum: General Help
---

### Post by navbor on 2011-07-30
[FONT=Calibri][SIZE=3]Hi All[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]We have a system of 6 PC's (all windows - 2 XP, 4 Win 7). We have a 7th PC setup with Ubuntu server 10.10. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]In the server we have two HD's, /dev/sda is the operating system drive and /dev/sdb is intended as the data drive.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]On the data drive I want to have the following:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]1.) A read only folder / directory (all read only areas are read only to all users except the administrator, who has full access), and I want to restrict which users can / can't see this area[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]2.) Individual user folders / directories where each user can store their data (full private access to each user and full access to administrator)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]3.) A general read / write area for dumping information that may be shared between various users (full access to all)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]4.) A ftp folder / directory where we can give access to external users (this area needs to be divided up in such a way that each external user has a folder and all internal users can be individually configured to have differing levels of access to these folders depending on what their involvement with the customer / external user is)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]At the moment I have the server up and running and I have installed SSH so access to the terminal window via putty from my windows machine is possible. I also already have samba installed. I would prefer not to have the a GUI / desktop version of Ubuntu on the server for  4 reasons:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]a.) I am a relative newbie to Ubuntu / Linux and in order to have whatever I learn stick, I prefer to use the terminal environment[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]b.) I want to be able to manage the server from my windows machine using putty[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]c.) I prefer the less complicated installation on the server.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]d.) I love the raw feel of the command prompt, it just seems to have more control.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Is there anyone who can advise / recommend a good tutorial for achieving what we are after. I have found many tuts (mostly on you tube) and followed a lot of them, but they all seem to be very disjointed in the sense that they are incomplete and only follow the process to a point and not all the way through as I would like to have it above. Also there seem to be so many different ways of accomplishing what is needed, but most case I only seem to find at the end of the tut that it is not quite what I was after and then have to try and undo everything that was done, only to end up re-installing Ubuntu.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The areas where I am not sure how to proceed are:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]1. During the original installation, I followed a tut that set up a partition on both my drives. The data drive now has a Linux partition. Can this be used to store windows data files and if not, how do I change it? I know that during the installation process the mount point for this device was set to /srv, but I am not sure how to mount this device.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]2.) How do I set up all the different users and their access as described above.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]3.) How do I set up a FTP server that can be accessed from the outside world? How do I managed the IP address of this server since the IP address would surely change from the point of view of the world outside of our LAN  (not sure about this statement)?  Perhaps an FTP server is not the most appropriate solution. Any suggestions are welcome.[/SIZE][/FONT]
[FONT=Calibri]I know that this is a rather long post and at times may appear ignorant (at best) to the Linux world at best so please accept my apologies, but any advice input would be much appreciated.[/FONT]

---


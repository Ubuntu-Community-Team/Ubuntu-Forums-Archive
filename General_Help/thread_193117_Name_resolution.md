---
title: "Name resolution"
date: 2006-06-09
forum: General Help
---

### Post by tymanthius on 2006-06-09
I have a home network, running off a linksys wrt54g using dd-wrt firmware.  It handles my dhcp.  

I currently have 1 Xubuntu, and 2 edubuntu pc's, plus a windows pc that used to be on a Win2k3 domain. 

Right now, however, when I type 'ssh kidsputer'  it kicks back a 'no such thing' message.  What do I need to do so that all I have to remember is the computer names, and not the IP's.

Probably set up a server, I guess.  But where do I need to start?  I'd like to eventually move all of my /home dir's to the server (easy enough), and all my authentication to the server (no idea how to do that, esp. for the windows side).

I'm not tied to ubuntu, or even linux, for my server.  BSD might not be a bad way to go.

Thanks for pointing me in the right direction.

---

### Post by ubuntuguru on 2006-06-09
add you computers dns names and ip addresses to /etc/hosts file

---

### Post by tymanthius on 2006-06-09
[QUOTE=ubuntuguru]add you computers dns names and ip addresses to /etc/hosts file[/QUOTE]


I don't think that will work - dhcp, so the ip's change.

---


---
title: "Netbooting: how to begin?"
date: 2010-06-24
forum: General Help
---

### Post by Misnomer on 2010-06-24
Hello there,

I am pretty new to Ubuntu Linux specifically. I want to setup my family with a Linux terminal server and some thin clients. It would be nice to do some serving!

I have three old computers. One from 1999, one from 2004 or so and one from 2006/2007. They're all pretty old but I want to learn about maintaining servers and my own little network.

Here's what I attempted so far and what I've been reading about:
[list]
[*]I downloaded the DRBL package to my Linux partition and tried to set it up but it kept failing saying it could not find clonezilla. Trying to install clonezilla was no help either.
[*]I burnt a DRBL live cd and it freezes on my old computer. X cannot start.
[*]The DRBL website says I need two NIC cards but I do not really understand why?
[*]I have a Tomato on my WRT54. Would love to get logs sent to a central server.
[*]Read about Etherboot and Coreboot but don't really know where it fits in.
[/list]

So, I come here utterly confused, rather than stumble about with the above (I do not actually really get what DRBL does!) could you guys point me in the right direction? Are there any guides that work on this? I've been to HowToForge but do not really know what is relevant. I know that I do need to setup:
[list]
[*]DHCP: Do I need to take this responsibility from my Tomato router?
[*]NFS
[*]TFTP
[*]Linux image files
[*]Static IPs (I have assigned static DHCP addresses to each of the machines in me LAN based on MAC).
[/list]

What's the recommended order of doing this? What experiences can you share?

---

### Post by Ferb on 2010-09-09
Follow these instructions. I have set up 3 drbl lab's 100+ pc's in the past 2 weeks. This was made easy by drbl. 

[https://wiki.edubuntu.org/SettingUpClonezillaDRBLonUbuntu](https://wiki.edubuntu.org/SettingUpClonezillaDRBLonUbuntu)

Have a look. Then ask any other questions that you might have

---


---
title: "How do I SCP from a Virtual Machine to a Remote Host?"
date: 2011-10-14
forum: General Help
---

### Post by linuxspy007 on 2011-10-14
Hi,

I've been searching Google for the past couple of hours and I still can't figure out how to SCP files via command line to the remote host of my hosting company.   SSH is enabled on their end and I was able to login via the command line so I know I'm using the right port #.

I'm trying to SCP some files from my local Ubuntu 10.04 Virtual Machine (running on a Windows Vista Platform) up to my remote web host:

scp -P PORT# -r myuserid@127.0.0.1:/~/fromFolder/ ~/public_directory/toFolder/ 

where PORT# = an actual port # like 22

I was asked for myuserid@127.0.0.1's password but it wouldn't take the password I normally use with this localhost account...Help please???

---


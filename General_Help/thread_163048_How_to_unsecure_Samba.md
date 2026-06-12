---
title: "How to unsecure Samba"
date: 2006-04-20
forum: General Help
---

### Post by Mr Green on 2006-04-20
I have just installed 5.10 from scratch again. Now I'm about to setup the shares for the other windows computers on my network. This is a closed network behind a firewall.

What I want is Samba to be totally insecure. Now if I go to System -> Administration -> Shared Folders ( little unsure about the menunames here as I'm using Norwegian version.) and share a folder it is impossible to access from other computers.

Is it possible to setup Samba in a way that every folder you share is accessible for all users on the network, no matter if they have a user account on the linux computer or not, and that they don't need any passwords.

In other words I want Samba/Gnome to behave like Windows file sharing: When you share a folder it is accessible for all other users.

---

### Post by zx6woody on 2006-04-20
I think you have to amend the smb.conf file in /etc/samba

change the security = user to share. 

> ####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;    security = user
   security = share

Then stop and restart Samba. I think that will do what you need, but just to let you know I'm new to Ubuntu, Samba and Linux in general.....:roll:

---

### Post by Mr Green on 2006-04-20
Thanks man, that was excactly what I was looking for. Now folders are accessible without any hassle :D

---


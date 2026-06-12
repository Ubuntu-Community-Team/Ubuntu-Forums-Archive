---
title: "Need Help Setting Up File Server"
date: 2009-10-05
forum: General Help
---

### Post by woodbj on 2009-10-05
I'm looking at setting up a home file server a need some help setting it up (i'm a complete noob when it comes to servers). I have a Ubuntu desktop thats going to be the server, and all the other computers are windows vista and xp... i want the windows computers to be able to store documents, access and store music and back up files... any help on this will be really great

---

### Post by 3rdalbum on 2009-10-05
Creating a file server on Ubuntu is a dangerous process, fraught with difficulties, and there's a good chance that it might just never work.

**Just kidding!** It's easy.

First, you need to install the "samba" and "system-config-samba" packages.

When they are installed, go to System > Administration > Samba and the System-Config-Samba tool will appear. You can use this very simple interface to create some shared folders and specify what users can access them. It will ask you to specify a "workgroup name" - just leave it at the default, which is either "MS_HOME" or "WORKGROUP". Each shared folder needs to be given a "share name" as well, which can be whatever you choose. The other thing you'll need to remember is the computer name (type "hostname" in the Ubuntu terminal to find this out).

For every username and password that you want to be usable to log into the file server, you need to add these as ordinary user accounts on the Linux machine first. So this involves a trip to the "Users and Groups" control panel. When you have added the users to the Ubuntu system, close System-Config-Samba and start it back up, and you will be able to add those users to the shared folder.

That's pretty much all there is to it. Windows machines will be able to browse the "Network Neighbourhood" and find the server, alternatively Windows gives you a way of manually specifying an address to connect to. When you connect, if your Windows username and password are different to one of the ones registered with Samba, you will be prompted to type in the login details of an account that IS registered.

ou can browse the network on Gnome, or use the address bar in Nautilus to quickly connect to the share:

```
smb://computer-name/share-name
```

You can also add a share to the Places menu by bookmarking it. When you mount a share on Ubuntu using the Gnome interface, you will be mounting it to a location inside ~/.gvfs. I don't know what Windows does.

IMPORTANT: Make sure there are no firewalls running on the client machines, or they won't be able to automatically find your server based on its name. You would need to specify them by IP address, and I don't even think Windows can actually do that.

---

### Post by BluShift on 2009-10-05
Damn! You beat me to it ;P

He's right though; Linux is hands down the easiest platform to run a server. You should have no trouble at all.

---

### Post by woodbj on 2009-10-06
Alright so I have installed the apps and setup the Music folder to share... but on the windows machine it keeps asking for a password so i enter my linux user name and password and says login unsuccessful... 

OK so I changed the Authentication mode to domain and now it is working but it is quite slow to access files (its a 3.0 ghz P4 machine with 1.5 gb ram) should it be going at least a bit fast

---


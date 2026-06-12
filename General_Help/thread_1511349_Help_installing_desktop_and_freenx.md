---
title: "Help installing desktop and freenx"
date: 2010-06-16
forum: General Help
---

### Post by mcmoore74 on 2010-06-16
Ive tried and failed at installing a gnome desktop and Freenx server on ubuntu 10.4.  I am a linux noob.  If anyone could install this for me id be happy to offer them $5.  I have a server in which i would like a GUI interface.  Wasted 2 days trying it and finally have decided that i cannot do it.  If anyone would like to help me out and do this for me id be very grateful adn offer $5 via paypal.  Thanks

Please PM me if you would like to do this , ill then send the details of the server

update, pretty sure ive installed gnome correctly but i cannot get nxserver to work

I have got it working now :) - feel free to delete this thread.

---

### Post by cybergalvez on 2010-06-16
how did you do it? I've always just installed NX from nomachine. Any advantages to freenx?

---

### Post by mcmoore74 on 2010-06-17
Yeah i did used nomachine much easier.  I used centos 5.2 aswell as i was getting nowhere with ubuntu, took about 5 mins to install a desktop and nomachine :D

Shall try with ubuntu now that know a little more about linux.  Its a learning curve

---

### Post by doas777 on 2010-06-17
last I checked (about a week ago), it was as easy as:
```

sudo apt-get install python-software-properties && sudo add-apt-repository ppa:freenx-team

sudo apt-get update
sudo apt-get install neatx-server

```[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

the first line installs the pyton dependencies, and adds the Personal Package Archive that the freenx-team set up for ubuntu. 

the second line just updates your computers list of available software (including stuff from the new PPA)

and the thrid line install the freenx server, recently renamed to "neatx-server"


Edit: ahh I see its going for you. rock on, and happy ubuntuing

---

### Post by mcmoore74 on 2010-06-17
Yeah it is really easy, the only problem i had was with nx and its keys for the client.  To install the whole thing ie desktop and nomachine i did:

[INDENT]sudo apt-get update
[/INDENT] [INDENT]sudo apt-get install ubuntu-desktop
[/INDENT]
sudo aptitude install freenx
Use this key in the nx client:[INDENT]cat  /var/lib/nxserver/home/.ssh/client.id_dsa.key

- copied and pasted the key into my nxclient and all works well.

Really easy in the end and took 5 mins - thanks ubuntu
[/INDENT]

---


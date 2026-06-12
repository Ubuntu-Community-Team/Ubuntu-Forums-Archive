---
title: "Update gimp to 2.7.1"
date: 2010-10-01
forum: General Help
---

### Post by THE-LEGEND on 2010-10-01
[COLOR=Blue]Hi everyone :) 
I am a new user on Ubuntu and I have a question ! 

I want to update a program (gimp) to a new one & I don`t know because I still beginner 

So please anyone know the way to update it tell me OK 

sorry for my bad language :( 

thanx  [/COLOR]

---

### Post by Frogs Hair on 2010-10-01
There  are some ppa instructions. I will post back with the latest . The  ones I have are outdated.

---

### Post by lykeion on 2010-10-01
You need to add en external PPA repository to be able to upload GIMP to v2.7.1 
This is a web page explaining how you can do this:
[http://www.howtogeek.com/howto/12047/install-gimp-2.7.1-on-lucid-lynx-using-ppa/](http://www.howtogeek.com/howto/12047/install-gimp-2.7.1-on-lucid-lynx-using-ppa/)

(note that this is for Ubuntu Lucid 10.04)

EDIT
Checked the PPA page 
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn) 
and the current version is GIMP v2.7.3

---

### Post by Frogs Hair on 2010-10-01
Run these commands in the terminal one by one press enter after each command.

sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install gimp

---


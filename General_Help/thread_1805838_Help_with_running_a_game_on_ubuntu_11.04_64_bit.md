---
title: "Help with running a game on ubuntu 11.04 64 bit"
date: 2011-07-16
forum: General Help
---

### Post by crua9 on 2011-07-16
I am having problems getting wine to work on my ubuntu. I try wine HQ but it sounds like you need to root your ubuntu which mine isn't and i don't know what overall good that will do. 

The game I'm trying to run is [http://www.starwraith.com/evochronmercenary/downloads.htm](http://www.starwraith.com/evochronmercenary/downloads.htm)

If the game can't be run on Ubuntu then it's ok because I'm dual boot Windows 7 and Ubuntu and it works for me on Windows

---

### Post by CatKiller on 2011-07-17
The one person that's tested it says that [that game doesn't work]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22046") in Wine.

You don't need to do anything special to make Wine work. If an application works with Wine, it pretty much just works. If it doesn't work, it doesn't work. You get menu launchers and the like. Sometimes you might need to tweak things to make the application work better, which are normally documented on Wine's AppDB entry for that application.

To run something as root you just need to put *sudo* in front of whatever command it is that you want to run as root. There's more information on the Ubuntu user model [here]("https://help.ubuntu.com/community/RootSudo").

---


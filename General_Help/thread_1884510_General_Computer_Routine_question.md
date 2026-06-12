---
title: "General Computer Routine question"
date: 2011-11-21
forum: General Help
---

### Post by Blizzardly on 2011-11-21
How to Power Off My Linux Certified Laptop that runs only Linux Ubuntu as a Operating System? It never seems to want to power off when I go through the proper power off menu and I can only get it to hibernate but not completely shut down. :confused:

---

### Post by wolfen69 on 2011-11-21
Holding the power button in for a few seconds will shut it down completely. Unfortunately you may have to wait for a kernel update for it to be fixed. What kind of laptop is it?

---

### Post by alphaamanitin on 2011-11-21
```
sudo shutdown -P now
```once you type that into the terminal it is in the terminal history. So the next time you want to use that command do this:  type ```
history
``` into the terminal  you will see the shutdown command with a number to the left of it.  Remember that number, for today's example I will assume that number is '55'.  To use the command at any time simply open your terminal and type ```
!55
```  This will run the shutdown command with less typing, but you still have to enter your super user password.  Also, you can replace the now with minutes, so ```
sudo shutdown -P 60
```would power down the system in 60 minutes.  The -P in the command means power down after shutting down the OS.

---

### Post by digithal on 2011-11-21
There is a well known bug in Ubuntu, experienced by some users including me (caused by NetworkManager), which is lengthening the shutdown time. **[This fix]("http://www.madanalogy.com/2008/04/fix-slow-ubuntu-shutdown-with-cifs.html")** is working for me, but I'm not sure will it help you.

You have to:
[quote="Chuck LeDuc Díaz"]cd /etc/init.d
sudo wget [http://www.jejik.com/files/examples/umountcifs](http://www.jejik.com/files/examples/umountcifs)
sudo chmod ugo+x umountcifs
sudo update-rc.d umountcifs stop 02 0 6 .[/quote]

---


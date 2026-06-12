---
title: "X server fails--Radeon X1600"
date: 2006-04-29
forum: General Help
---

### Post by radicalsajon on 2006-04-29
Ok im a transfer from windows--but i only got as far as pressing enter a few times and writing my name and password. Basicaly this thing X-server wont load -gay-so it takes me to this command line type thing--Ive never used a command line before, well a little with windows FDISK stuff---anyways  looked up help on forums and it says to make ubuntu use vesa as fx driver--ok sweet , alrighty then!!! ya ahh how do i go about accomplishing that? "hey X-server, use those vesa drivers ok...good X-server good" So prety much i need a walkthrough on how to do this-
  See this is why linux eludes me--everytime i try and mess with it--it throws something out there that i cant grasp. What is a damn X-server--whats a repos? What im getting at is Ubuntu needs to come out the starting blocks with a GUI something anyone can follow-then load drivers that will work with anyones pc -then boot up to a Update screen--where ubuntu loads drivers for your pc spicifics-then Loads the desktop with a flashy background --lol anyways anyone help--please
sajon

---

### Post by radicalsajon on 2006-04-29
COme on people--BEEN WAITING A WHOLE 15 MINS NOW--lol just messin--anyways uhhh ya any word on that whole driverproblem i was haveing?? no ..not yet..ok thats cool--check back in a few min...half hour i guess--ill just go play some Counter-strike Source from my gay windows--which i have had to reformat and reinstall Windows on about a million times now--blah

---

### Post by Ramses de Norre on 2006-04-29
A little respect doesn't harm anyone.. I doubt you'll get much help with such an atitude.

For you're problem do sudo vi /etc/X11/xorg.conf and search the device section, press i to go into insert mode and change the driver to vesa (it's set to ati by default I think). Then press esc and shift-q and type wq! at the prompt you'll get below. Then do sudo /etc/init.d/gdm restart and press alt-ctrl-F7 .
Search the web on installing the fglrx driver for ati because vesa hasn't got any acceleration.

---

### Post by radicalsajon on 2006-04-30
wow man sorry about that i wasnt meaning disrespect--i was just trying to put a little humor into my problem--sorry about that. Anyways do i do what you told me to do from the command line after X fails? Well i printed off what you said to do- and im very greatefull that you did help me- ill post back after i try what you said- again sorry about that was just trying to add some humor. 
Sorry again
sajon

---

### Post by Ramses de Norre on 2006-04-30
Yes you need to do that in console, you'll probably get dropped to one after X crashed or otherwise press alt-ctrl-F1.

---

### Post by radicalsajon on 2006-05-01
ok i did Sudo apt-get install xorg-driver-fglrx --this was from another guy--anyways it worked im booted up to Dapper Beta--everythings going great--but i would like to install the accelerated fx drivers--how do i do that-? Right now im only getting 800 x 600 and would like to run it at 1040 --if you can help me great-- thanks
sajon

---

### Post by radicalsajon on 2006-05-03
Anyone know what i should do to get Max res at 1040?

---


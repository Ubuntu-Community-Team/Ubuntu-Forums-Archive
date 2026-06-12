---
title: "ubuntu 9.10 update crashed  my pc"
date: 2009-11-11
forum: General Help
---

### Post by Tsquad on 2009-11-11
so Iv got 9.10 on my pc and it was doing updates, the auto updates, i told it to download them and then it was in the middle of installing them and my pc froze up, so i had to shut it down by holding down the power. I turned it back on and the desktop looks different, it changed all the visual settings i had made under system > prefrences > appearence. Now when i try and change them back, the changes are not made, it shows they are made under appearence, but i dont see the changes. Also, when i minimize fire fox it closes it to the trash can....its pretty annoying. I cant tell you what the updates were because i dont remember. a few other things got changed, im thinking of just downgrading to 8.10 or .4

Any suggestions?

---

### Post by wilee-nilee on 2009-11-11
Have you tried to just run the update again since it froze and you had to do a hard shutdown. Do you know why it froze, it could be a number of things that leaves you vulnerable to losing important data.

Also here is a link to a better shutdown method.
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Before doing anything more I would make sure you have critical stuff you can't lose backed up, like media...etc.

---

### Post by bashphoenux on 2009-11-11
your upgrade wouldn't have been completed fully !! try upgrading again or probably try doing a fresh install of Karmic

---

### Post by Tsquad on 2009-11-11
this is an old p4 gateway that im using as a test pc for ubuntu, i have very little experience with it. So i have no data on it to lose. And i was not even looking at it, i was on my main pc doing other stuff because it was taking a while, then i looked at it and the mouse would not move and the little loading circle stoped spinning and was stuck, so i shut it down.

Edit:found the update manager, it shows no new updates and says at the top that the package info was last updated 1 hour ago

Edit2: k i clicked on check and it found 15 updates, now its giving me an error message saying 
E: dpkg was interrupted, you must manually run "sudo dpkg --configure -a" to correct the problem
E:_cache->open() failed, please report.

and noob Q: what is karmic

---

### Post by imtheguru on 2009-11-11
Start synaptic. It's more interactive than the Update Manager.
System > Administration > Synaptic

Look for broken packages
Status > Broken...

'Remove' or 'reinstall' the offending package(s) then 'reload' the package list, 'mark all upgrades' and 'apply'.

Karmic is shorthand for Ubuntu 9.10 Karmic Koala.

Cheers.

---

### Post by wilee-nilee on 2009-11-11
> **Tsquad said:**
> this is an old p4 gateway that im using as a test pc for ubuntu, i have very little experience with it. So i have no data on it to lose. And i was not even looking at it, i was on my main pc doing other stuff because it was taking a while, then i looked at it and the mouse would not move and the little loading circle stoped spinning and was stuck, so i shut it down.

Edit:found the update manager, it shows no new updates and says at the top that the package info was last updated 1 hour ago

Edit2: k i clicked on check and it found 15 updates, now its giving me an error message saying 
E: dpkg was interrupted, you must manually run "sudo dpkg --configure -a" to correct the problem
E:_cache->open() failed, please report.

and noob Q: what is karmic

Do the sudo dpkg --configure-a in a terminal then do sudo apt-get update then look at the update manger to see whats there, and don't do a partial update if it is requesting that go back to the terminal with everything closed and run sudo apt-get dist-upgrade.

Worse case since you have nothing to lose do a fresh install. What is the ram amount and chip speed of the computer?

Karmic is the name of the 9.10 OS Karmic Koala.

---

### Post by Tsquad on 2009-11-11
I did the last 2 posts suggestions and the only thing that happened is i was finally able to change my visual effects. I had also gotten the update to finish. But my FF is still minimizing to the trash can...

---

### Post by jeb800e on 2009-11-11
> **Tsquad said:**
> so Iv got 9.10 on my pc and it was doing updates, the auto updates, i told it to download them and then it was in the middle of installing them and my pc froze up, so i had to shut it down by holding down the power. I turned it back on and the desktop looks different, it changed all the visual settings i had made under system > prefrences > appearence. Now when i try and change them back, the changes are not made, it shows they are made under appearence, but i dont see the changes. Also, when i minimize fire fox it closes it to the trash can....its pretty annoying. I cant tell you what the updates were because i dont remember. a few other things got changed, im thinking of just downgrading to 8.10 or .4

Any suggestions?

Next time you have to do an emergency restart like that, do the REISUB technique, not the "unplug and everything will be all better" method.

This is how you do it:

Alt + SysRq + R
Alt + SysRq + E
Alt + SysRq + I
Alt + SysRq + S
Alt + SysRq + U
Alt + SysRq + B

AND DO ALL THESE SLOWLY, leaving waiting 2-4 seconds after each command you press in!

or, to do a shutdown instead of a restart, replace the "B" with an "O" as in one.

---

### Post by jeb800e on 2009-11-11
You can try reinstalling Ubuntu from a fresh install. That would be the easiest way to fix things! I would recommend 8.04, 9.04 or 9.10. If you do end up using 9.10, you will probably be fine if you just be careful for the first few weeks while the Ubuntu community is getting all the bugs fixed out.

---

### Post by wilee-nilee on 2009-11-11
> **Tsquad said:**
> I did the last 2 posts suggestions and the only thing that happened is i was finally able to change my visual effects. I had also gotten the update to finish. But my FF is still minimizing to the trash can...

could you explain what the minimizing to the trash can means, and what version of Karmic are you running? what desktop in other words.

---

### Post by Tsquad on 2009-11-12
> **wilee-nilee said:**
> could you explain what the minimizing to the trash can means, and what version of Karmic are you running? what desktop in other words.


Umm its gnome im pretty sure, if thats what your asking, not kde. and what i mean about fire fox is when i click minimize on it, it minimizes down to the trashcan in the bottom right and is then closed and i have to re open ff and i lose my tabs.

and to jeb800e: im already using 9.10, and i thought i was being careful. Oh well. what version would be the most noob friendly? 8.4 or 8.10. or should i just stick with a new install of 9.10 because it will be worked out soon enough?

Also, im planning on making this a home server and an FTP server and maby some other server type things later on. Should i stick with the desktop version of 9.10 or should i get the server version? keeping in mind im very new to linux.

---

### Post by jeb800e on 2009-11-14
Version 8.04 may be best for you, as you have to deal with little updating problems, as your distribution needs to be updated only about once every two to three years. (You will have other updates available, but those aren't distribution updates... they are just updates for programs, security updates, etc.)

---

### Post by Tsquad on 2009-11-14
well i just went with a fresh install of 9.10 and i have had good luck with it so far. Except for one issue i keep having where my desktop freezes, my keyboard is unresponsive(num lock and other lock keys get stuck on or off, cant change them). My mouse moves around fine, but nothing i click on opens, and the alt+pring+reisub thing dont work either, cuz of dead keyboard. 

ill be making a new thread for this one.

---

### Post by jeb800e on 2009-11-14
With the REISUB technique, type REISUB slowly, one key at a time.

---


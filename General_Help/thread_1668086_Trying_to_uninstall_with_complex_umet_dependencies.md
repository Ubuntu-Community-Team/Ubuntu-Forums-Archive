---
title: "Trying to uninstall with complex umet dependencies"
date: 2011-01-15
forum: General Help
---

### Post by res.being on 2011-01-15
Greetings! Right now **these problems have rendered my system unusable**, so any help would be **very greatly** appreciated!

*Background info*: I'm unable to log in due to having run out of space & having that problem with Xauth & thus can only access the terminal, not synaptics or anything. I'm running Karmic, & **I'm very much a layperson** even with regards to stuff often considered basics to many of you. 

*Aim*: to remove a partial download/install of Wesnoth, & possibly any other games/superfluous programs to free up enough space to be able to log in. 

*Difficulty*: Unmet dependencies with wesnoth ... & due to the whole lack of free space, likely difficulties with what I gather is the usual fix (installing it all the way & then uninstalling, or updating the OS)

---

### Post by kn0w-b1nary on 2011-01-15
in terminal type: "aptitude"
scroll down to games, and you can find the names of games u can remove.

then exit by typing "Ctrl+C and type:
"sudo apt-get remove wesnoth"
Replace wesnoth with name. Also try:
"sudo apt-get autoremove"

Hope this helps!

---

### Post by res.being on 2011-01-16
Thanks very much for the prompt reply, kn0w-b1nary! 

Ok, so wesnoth has a zillion packages involved, so it seems it may be easier to remove a different game first, called meritous. [Trying to install wesnoth is what took up the remaining space, thus causing the problem, but it can't hurt to free up space removing a different program]

Under the aptitude list of installed games, there's 'meritous' and 'meritous-data'.

If I type 'sudo apt-get remove meritous' into the terminal, it reads the package list, builds dependency tree & reads state info all fine, the goes to listing the unmet dependencies of wesnoth (which are wesnoth-utbs & wesnoth-data) & of wesnoth-core (wesnoth-data). But, going back into aptitude, it still lists meritous under installed game packages. The same thing ocurrs when I type 'sudo apt-get remove meritous-data' and 'sudo apt-get autoremove' :neutral:

---

### Post by kn0w-b1nary on 2011-01-16
here is another way:
in aptitude highlight the file name
hit the dash key: -
then hit "g"

it will show you a list, just hit "g"

This should work as i tried it on my computer.

---

### Post by res.being on 2011-01-16
Eeek! Now I can't log into the terminal - it keeps interrupting with the following error msg:

> long number [available on request - it keeps changing, too] ath5k phy0: noise floor calibration failed (21412MHz)

Any thoughts? :/

---

### Post by kn0w-b1nary on 2011-01-16
> **res.being said:**
> Eeek! Now I can't log into the terminal - it keeps interrupting with the following error msg:



Any thoughts? :/

Sorry, but I don't know the answer to this one. :confused:

---

### Post by res.being on 2011-01-16
Ok, manually turning off the wifi & rebooting worked for that.

So far, I have all of the many wesnoth packages in the to-be-uninstalled (or removed, not sure which, but whatever it is will free up some disk space).

However, it's trying to install of ton of other things (programs I'd uninstalled to free up space), some of them in order to meet other unmet dependencies. It seems that, if I let these be installed, it either won't work due to lack of space, or will just be counterproductive to the goal of freeing up space in order to be able to log in. 

Yet these packages don't seem to go into the list of to-be-removed packages when I type '-' and then 'g'. These packages are all in a green font. Do they require some other commands to remove? Are they even possible to remove at all?

---

### Post by res.being on 2011-01-16
Er ... it randomly tried to go ahead and download those new programs, & I kinda freaked out & removed the battery. Now it's telling me the packages cache is opened in read-only mode ... but I'm not sure how to become root (apparently an option under 'Actions' at the toolbar-type thing at the top of the aptitude screen, but I can't figure out how to get the cursor up there.

---

### Post by kn0w-b1nary on 2011-01-16
> **kn0w-b1nary said:**
> when starting your computer, before the splash (the ubuntu and dots) hit Shift repeatedly, (you have to be fast) and it might take several reboots to get it. You will "GRUB loading" and then a menu. Select recovery mode (if there are several, choose the one closest to the top. In the next menu, Select "exit to root prompt"

There you go!

this will get you root. plz retry the preceding steps and report what happens.

also, you can type:

"sudo apt-get purge filename"

replace filename with whatever. purge removes the package AND config files saving a little more space.

Good luck!

---

### Post by res.being on 2011-01-17
OKay, so I'm finally able to see the desktop! Thanks ^_^

However, now the mouse is stuck in the middle of the screen ...

---

### Post by kn0w-b1nary on 2011-01-18
Have you tried moving some of your personal info to a USB? Is doable in terminal.

---

### Post by res.being on 2011-01-19
So sorry ... it worked, uninstalling stuff through aptitude! Thank you so much! :)

---

### Post by kn0w-b1nary on 2011-01-20
> **res.being said:**
> So sorry ... it worked, uninstalling stuff through aptitude! Thank you so much! :)

You're Welcome. :)

---


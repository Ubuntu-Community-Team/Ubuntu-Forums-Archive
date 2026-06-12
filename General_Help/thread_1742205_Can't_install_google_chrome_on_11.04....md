---
title: "Can't install google chrome on 11.04...???"
date: 2011-04-28
forum: General Help
---

### Post by robertcoulson on 2011-04-28
Tried to load Google chrome on 11.04 (in virtual box) and it does not load and I get an error..see attachment...Plus Unity does not work.

Help, Robert

---

### Post by Lolpanda on 2011-04-28
[https://launchpad.net/ubuntu/natty/i386/libnspr4-0d](https://launchpad.net/ubuntu/natty/i386/libnspr4-0d)


It exists, if thats any comfort.

Open up Software Sources, make sure you have universe, main, partner, etc, all enabled. Open up Synaptic and do a search for 

libnspr4-0d

if it doesn't come up, then something's wrong. 

If it doesn't come up, run sudo apt-get update and post any errors you get (if any).

---

### Post by robertcoulson on 2011-04-28
Lolpanda...I am NO computer wiz, I have a hard time understanding what you are asking, and I know there are more people on here that have more problems than me..I am happy with 10.10 and don't think I will go to 11.04,...Thanks for trying to help me...I will stay with what I got (even with the problems I have with 10.10)
Thanks, Robert

---

### Post by Lolpanda on 2011-04-28
Sorry Robert. For anyone else that may have been following this thread and also got lost I'll give the long form of the instructions.


Go up to the menu, look for an entry called "Software Sources" (this is also available under Synaptic I think under 'tools'). One of the tabs inside of Software Sources should have a list of various entries with checkboxes next to them. 

Make sure that any entry with the words 'natty', 'partner', 'universe' and 'main' in them are checked. 

Hit "refresh."

Go back to Synaptic, and in the search box put in the: libnspr4-0d

If its available to install it should automatically come up. If its not, it won't.

If it comes up,  install it. 

If it doesn't, bring up terminal and type in

```
sudo apt-get update
```


A lot of text will come up but you're just looking for "CANNOT FIND" or "WARNING" or something similar. If you get errors like that, post them (here, if you're Robert. In your own thread for anyone else)

---

### Post by robertcoulson on 2011-04-28
Lolpanda...Could not see anything that looks like "natty"...I have removed 11.04 from my virtual box, and will stick with 10.10 for now...It seems to work better than 11.04 (for me anyway)...Thanks again for all your help.

Robert

---

### Post by Lolpanda on 2011-04-28
Thats honestly, probably your best bet Robert. I've got Kubuntu 11.04 installed, and had tried Ubuntu 11.04 Beta 2 in a VirtualBox as well, and I really wasn't impressed

---

### Post by robertcoulson on 2011-04-28
Yes Lolpanda...I know what you mean...Thanks for the note.

Robert

---


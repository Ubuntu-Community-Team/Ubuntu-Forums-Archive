---
title: "Slow computer -- seems busy but is not"
date: 2010-05-25
forum: General Help
---

### Post by Maerwyn on 2010-05-25
Hi, 

The past day or so my computer is extremely slow to respond. When I move my mouse there is a lag, when I type there is also a lag. Web pages do not seem to load slowly, but whenever I try to interact with them, there's a lag. It seems like my computer is running something in the background but as far as I know, it isn't. 

I ran the clam virus scan, I do not have a virus. That's pretty much the extent of what I know to do. Help is greatly appreciated. 

(I am using Kubuntu 9.10)

---

### Post by dino99 on 2010-05-25
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo apt-get install gconf-cleaner
(run it : apps system gconf-cleaner, yes to all)

if you have errors, watch: system admin log viewer, and .xsession-errors in your /home (unhide it with menu)

---

### Post by Maerwyn on 2010-05-25
Thanks for the suggestion. I tried that and things went smoothly for a short while but now I'm having some other trouble and I'm thinking this is a hardware problem. 

Thanks for your help, though.

---

### Post by keayz on 2010-05-25
Hi, I'm not sure if I can add to this thread as it is marked 'Solved' but hope it is OK to do so.

I have been having the same problem as Maerwyn ever since upgrading to Lucid Lynx. I've tried the suggestion above but no improvement. Everything else seems to work just fine.

Any help would be appreciated.

---


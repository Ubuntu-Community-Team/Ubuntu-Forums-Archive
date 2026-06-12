---
title: "Unity  not working with nvidia current drivers"
date: 2011-10-16
forum: General Help
---

### Post by forestG on 2011-10-16
Hi!

I have an Acer Aspire 5920G and I upgraded from Ubuntu 11.04 to 11.10. It seems that Unity is not loading at all. If I open a window from a another terminal using the DIPSLAY=:0 option then a window will open but without window decorator. Unity 2d seems to work pretty OK. Gnome3 is also working OK. 

During the upgrade I changed all configuration files to the new default ones. 

Sorry if someone has posted a similar problem again  but I did a manual search on "Unity nvidia drivers" and I used also "check if already posted" and I had no results

Regards,

---

### Post by forestG on 2011-11-18
I found the solution to a topic here so I am copying the solution and describing how I solved it:

First I log in to Ubuntu 3d and there is no panel and no window decorator and no unity bar of course. I press ctrl-alt-F1 and I log in to tty1 using my username and password and I write (without sudo): "DISPLAY=:0 unity --replace" (no quotes)

I press ctrl-alt-F7 to go back to X-window system and I press ctrl-alt-T and in the terminal I write ccsm to get the compiz manager. If the package is not installed first write "sudo apt-get install compizconfig-settings-manager".

In the compiz manager I had to enable the Unity plugin and then resolve conficts by selecting the disable option each time. 

Then it worked. I logged of and restarted my machine to check if it is permanent and it is permanent. 

If nothing works I suggest "sudo apt-get install gnome" to install gnome 3 desktop which is quite similar to unity.

---


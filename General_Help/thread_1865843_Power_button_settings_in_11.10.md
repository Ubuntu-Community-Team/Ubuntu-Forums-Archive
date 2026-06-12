---
title: "Power button settings in 11.10"
date: 2011-10-20
forum: General Help
---

### Post by lalilulelo on 2011-10-20
I recently updated from 11.04 to 11.10, and to my dismay I discovered that you can no longer control what the power button does; it always pops up a dialogue box asking you what you'd like to do. I'd like it to suspend the machine every time I press the power button.

I looked at the setting in dconf-editor, and it's already set to suspend, but it still pops up the dialogue every time I press the power button.

Any suggestions on how I might change this setting?

---

### Post by LaptopU on 2011-10-20
To add to this, I would like to press power button and it shuts down my system, but it doesn't - I have set it to shutdown in dconf but the first press of the button gives me some HD activity, the top bar goes from Ambience theme to Radiance theme then back again after a couple of seconds, then if I press power again it finally shuts down.

Pretty annoying but I've had a post in a similar thread for a couple of days now and it's gone unanswered, I think this is something we're probably going to have to live with for now.

---

### Post by lgarcias on 2011-10-21
I have the same problem. :(
But i haven t manage to make it work yet.

---

### Post by upallnight on 2011-10-21
I have this same problem :(

I love some features of Unity ( actually Compiz features ) like Spread where your windows are spread out for easy switching with a hotkey, but I hate how some things can't be changed anymore! For instance, I want to remove the top bar that does nothing except waste space.

---

### Post by roton on 2011-10-23
This guide worked for me: [http://askubuntu.com/questions/66723/power-button-instant-shutdown](http://askubuntu.com/questions/66723/power-button-instant-shutdown)

---

### Post by LaptopU on 2011-10-24
> **roton said:**
> This guide worked for me: [http://askubuntu.com/questions/66723/power-button-instant-shutdown](http://askubuntu.com/questions/66723/power-button-instant-shutdown)

Brilliant, thanks :D that worked for me! (Hold on - no it doesn't, see further down)

It was the message suppress part I was missing as well as the shutdown setting.  Now I shut down with one press of the power button on my PC.  (Why couldn't the developers have just put this in power settings like before?!)

Edit - it only half worked I've discovered.  This seems to work fine for my desktop PC, but my laptop changes its scheme to Radiance theme, then back to Ambience, then the mouse locks up and I have to log out using ctrl-alt-del.  So not quite there yet.

Double edit - it doesn't work.  I thought it did as I successfully powered down twice, but tonight back to square one.

(Plus how do I get the option to restart now I've suppressed it in dconf?)

---


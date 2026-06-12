---
title: "Ubuntu won't log me in anymore"
date: 2011-10-01
forum: General Help
---

### Post by Desktop_n00b on 2011-10-01
Ok, I was attempting to make a music video in ubuntu, but it didn't have an .avi codex. So I thought by installing VLC maybe it would include one. So I installed VLC from the software center, then attempted to open one of the clips I was using. It still wouldn't load so then I went to open firefox so I could google what I could do about it. When I attempted to open firefox it kept crashing over and over, so I restarted my system.

When it rebooted my theme was gone. It looked like windows 98, and when I put in my password it acts like it is going to log me in for a min or 2 then it just takes me back to log in screen.

I looked for anyone else having probs with VLC and didn't see anything.

Any ideas what happened?

I am running ubuntu 11.04

---

### Post by Desktop_n00b on 2011-10-01
When I started it up just now it flashed in the top right of the screen real fast something about gnome install problem or something. Was too fast to read.

I hope that can maybe help.

---

### Post by [S|G] on 2011-10-01
When you mentioned that "it looked like windows 98" I'm tempted to think it might be a permission problem on your home directory. When you boot your Ubuntu, on the user selection screen, press ctrl+alt+f1. You should get to a text terminal. Try to log in there and do the following:

$ sudo chown username: -R /home/username

Replace "username" with your own user. After doing this type:

$ sudo reboot

And try to log in again after the system boots.

---

### Post by Desktop_n00b on 2011-10-08
That didn't work, but it did allow me to log in and access the terminal.

So far I tried all these commands but still no result

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

---

### Post by Desktop_n00b on 2011-10-08
WOO!! I tried this

sudo apt-get install gnome

and something happened and it crashed while doing it

so then I had to do 

sudo gpku (or somethinglike that) --configure -a (i think, it told me to do it)

then I did 

sudo apt-get update
sudo apt-get install gnome (but it said there was an issue and to try this next step)
sudo apt-get install -f

and now it works!

I hope this helps anyone else who may have this prob.
And thank you [S|G] for showing me how to get into the terminal outside of gnome.

---


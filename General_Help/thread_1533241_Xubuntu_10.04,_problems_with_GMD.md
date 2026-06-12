---
title: "Xubuntu 10.04, problems with GMD?"
date: 2010-07-17
forum: General Help
---

### Post by Agemman on 2010-07-17
Hello everyone! This is my first post here, as far as I can remember. 

I've recently, yesterday, encountered a problem with my Xubuntu installation on my laptop. When I started it there was no login screen, only the background. I was quite confused and naturally googled it. After some searchng I found that I could login using:

```
Ctrl+Alt+F2
Log in with my account
sudo service gdm stop
startx
```

That is what I am using now to just get into the desktop environment and I am able to use most things. Some thing however is not usable. For example, my WLAn doesn't work. The network manager doesn't work. The icon shows but when you click it, it just disappears. WICD works though. The Image viewer doesn't work, but Risetto does. Even the update manager doesn't work. It prompts me for mu password, builds dependency tree or something and the just lays off. It worked via the Terminal though.

And that is what I've tried up until now. There are probably more things that works and don't work. I also tried to load the Login Screen configuration from the settings. It has a button namned Unlock. When I press it nothing happens. It doesn't unlock the settings so I can change them in any way.

I've also tried reinstalling GDM through:

```
sudo apt-get install --reinstall gdm
```

It reinstalled GDM, but doesn't solve the problem. When I try to run GDM again through:

```
sudo service gdm start
```

Everything just crashes and kicks me out to the login, without a loginscreen. The trick I used earlier to get into the desktop doesn't work either. It just shows some error.

The last thing I can remember doing is to try to install Desmume-0.9.6 (the gameboy emulator) and along with that zlib-1.2.5, which when I ran ./configure with the Desmume said I was lacking. It also told me that I was missing Glib, but at that point I figured: "I can do this later" and turned the laptop off. After that the problems occured.

I pulled out a LSHW for those of you that want to have a look at what's inside the computer, which is a Acer Aspire 3100. It can be found [here](http://sharebee.com/2c50602d). Worth to mention is that although I've had Xubuntu installed on the computer for 1½ year, I've only been learning it for a few weeks. Up until then I've mostly viewed films on it on vacation. No surfing due to WLAN didn't work. But I am starting to learn more and I am loving it every step of the way. Now I've encountered problems, and I hope you can help me!

I am not sure it has anything to do with GDM, it is just the impression I get from it crashing everything when it starts.

Cheers!

---


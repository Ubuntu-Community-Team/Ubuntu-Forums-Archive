---
title: "Ubuntu 9.04 acting crazy"
date: 2009-07-12
forum: General Help
---

### Post by lowvoice on 2009-07-12
Hey I'm new to Ubuntu and have been running it for just over a week and everything was going great until yesterday when my computer started acting really bizzare let me tell you what is going wrong:

Firefox is taking a very long time to load and when it does load the back and forward navigation buttons are greyed out, however when I run sudo firefox in terminal firefox loads correctly with all the buttons working. I have installed various adds on to firefox if it helps including stumble upon, coolpreview, sage, and adblock plus.

My msn clients are also malfunctioning. I have tried pidgin which just simply closes shortly after it loads and I have also tried Emesene but keep getting error messagges when I try to log in. I'll post a screenshot in a bit if it helps.

Also my desktop background keeps changing to the standard everytime I reboot. I will set it as a picture then I will turn the computer off and when I turn it back on again and it will have reverted back to the standard background again.

Another thing I tried to create a shortcut on my desktop for pidgin and it keeps coming up with error while copying to desktop there is not enough space on the destination which is impossible as I have recently uninstalled programs that I didn't want (I had inadvertently downloaded biblereader when in the Synaps manager when installing other apps and have also removed compiz fusion as it slowed my computer down)

I don't know much about my hardware as my mom brought it from work but it's a dell with 391MB RAM (two cards one I installed), 20GIG hard drive and Pentium 3 processor. I have also installed a Samsung ML-2010 printer and am using a D-link DWL-G122 wireless usb dongle for my internet. If there is any other information I could supply please request it. I have scanned for viruses on the offchance that I have somehow stumbled upon a rare and elusive linux virus but nothing was picked up. Any advice you could give me would be great but I understand that my information supplied isn't full as I'm not sure how to get all of it (if you could tell me that would be great I'm kinda new to linux) and I understand that the nature of the problem seems very puzzling. The only other thing I can think to say is that when I initially installed Ubuntu I had a problem with my hard drive overheating so I opened up the windows in my room and let the computer air out for a couple of days. I have offcause done the same today and my room was literally freezing when I turned my computer on to post this however my computer is still playing up.

---

### Post by miklcct on 2009-07-13
Your disk is full, clean out all unnecessary stuffs from your /home drive.

---

### Post by Celauran on 2009-07-13
Sounds like there are a couple of different issues at work here.

First, you don't want to run Firefox with sudo. Most of your profile is now owned by root, which likely explains the problems you're having there. To correct this, open a terminal and type the following:

```
sudo chown -R username:username ~/.mozilla
```

Be sure to replace username with your username.

It also sounds like your hard drive is full.

```
df -h
```

will confirm this. Assuming the drive is full, then it's just a matter of freeing up some space. Run

```
sudo du -sh /*
```

to see where the space is being used, and work from there.

```
sudo apt-get autoclean
```

will free up some space, but how much will depend on how much software you've installed.

---

### Post by lowvoice on 2009-07-13
Ah thank you I did what you recommended Celauran and after a reboot everything was fixed. Lol I feel stupid to say that me thinks I installed too many games.
Whilst I have a thread to myself however I want to use my webcam on msn so I tried opening amsn and it came up with a dialogue box saying the configuration file is corrupt I have tried reinstalling but the same thing happened. 
Lol soz im probably doing your head in now but any ideas?
 Thank you :D:D:D:D:D:D:D

Also one thing I really love about Ubuntu is that Ryhtmbox actually works a thousand times better with my Ipod than I tunes XD. Just thought I'd throw that out there.

---

### Post by lowvoice on 2009-07-14
Bumptity bump

---


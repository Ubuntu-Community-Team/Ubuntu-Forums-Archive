---
title: "GDM Not Displaying Login Box"
date: 2010-11-22
forum: General Help
---

### Post by MOtAC520 on 2010-11-22
Hey, relatively new Ubuntu user here. I've been using Linux for about a year, dual booting with Windows. Recently switched to Ubuntu from Fedora.

It's been about a month, maybe a month and a half since I installed Ubuntu 10.04 alongside my Vista partition. One day last week, I boot Ubuntu and get to the login screen. The drum beat that is usually indicative of the login box plays, but no login box appears. 

From what I understand this is a problem that afflicts a lot of 10.04 users at some point. I am using x86_64 architecture and I'm somewhat used to things not always working out as they should. I pressed Ctrl Alt F1 and logged in. I did some research, and tried a few suggested fixes, including simply restarting the GDM with 
```
sudo stop gdm
sudo start gdm
```

As well as reconfiguring Xserver with
```
sudo dpkg-reconfigure xserver-xorg
```
This command returned no text, which I believe indicates its success.

Neither had any success. I did manage to get to a graphical desktop environment with the xstart command. However, only 
```
sudo xstart
```would work, and then only landing me in the root user's desktop, not mine. Running the xstart command without sudo brings me to a black screen.

And so I'm stuck. I know that reinstallation is certainly a possibility, but I'd like to exhaust my other options before that. Any help is greatly appreciated.

---


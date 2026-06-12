---
title: "Complete newbie needs help desperately"
date: 2011-05-31
forum: General Help
---

### Post by sumanbolar on 2011-05-31
Hi... I have been using ubuntu for about a year now... but do not understand the under-the-hood workings or jargon (I don't even know what GNOME is) So apologies for what may come across as overly simplistic or dumb.

A couple weeks ago, I upgraded my Vaio C-series laptop to the Natty Narwhal version of Ubuntu, and things have been running very smoothly. 

All of a sudden, while using Chromium browser, my cursor turned into a grid-like thing and parts of my screen went "missing". I managed to shutdown, but it wouldn't reboot. Took out the battery, reinserted, and it began to boot. On boot, there are red parallel lines behind the Vaio logo that have never been there before. The screen then goes blank. After several unsuccessful attempts, I hit F2 and it gave me a text login... did that, highlighted "Ubuntu, with Linux 2.6.38-8-generic (recovery mode)" and hit enter. Lots of scrolling text, followed by a "Recovery Menu" from which I chose "failsafe graphic UI mode". Got a message saying "your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."

When I hit OK, I got these options:
- Run ubuntu in low graphics mode for just one session;
- Reconfigure graphics
- Troubleshoot the error
- Exit to console login
- Restart X

I chose low graphics mode, and my desktop finally loaded. Am in the process of backing up my data, just in case.

What do I do after that in order to get back to a "normal" boot?

As you can probably tell, I am going to need precise,step-by-step, first-do-this-then-do-that instructions. I won't really understand anything, but I am good with instructions.

Thank you!

---

### Post by seawolf167 on 2011-05-31
Welcome to the Forums!

First try simply starting x in a terminal

Either when you boot, open a terminal (Applications -> Accessories  -> Terminal), the keyboard shortcut by default is [CTRL][ALT][T], or  if you hit [CTRL][ALT][F1] you can enter tty1.

```
startx
```The second thing I would do is reconfigure x if the above didn't solve your problem

Once you have a terminal open, type

```
sudo dpkg-reconfigure xserver-xorg
```Follow the onscreen instructions, then you can then restart your xserver if needed with

```
sudo service gdm restart
```

---

### Post by sumanbolar on 2011-05-31
Thank you. When I typed in "startx", I got a bunch of scrolling text that finished with the following:
> xinit: giving up
xinit: unable to connect to X server: connection refused
xinit: server error

I then keyed in: > sudo dpkg-reconfigure xserver-xorg. It asked for my password, which I keyed in, and then it immediately returned > myname@myname-Vaio: ~$

I then keyed in > sudo service gdm restart 
and the screen went blank. Then I hit ctrl alt F1, and got the response > gdm start/running, process 1573 

I then had to force shutdown. When I tried rebooting, I selected "recovery mode" again. I got these options:
- resume normal boot
- try to make free space
- run in failsafe graphic mode
- reboot into file system check
- Update grub boot loader
- Drop to root shell prompt with networking
-Drop to root shell prompt.

I selected "resume normal boot" and it gave me the following:
myname-Vaio tty 1
and then asked aqain for a text login and password.

That's where I'm at.

---

### Post by seawolf167 on 2011-06-01
Try the command

```
sudo service gdm start
```now that you are in tty after the restart

If that still doesn't work for you, we can walk through the steps of installing drivers for your graphics card, to start that, please post the output of

```
sudo lspci
```

---

### Post by ak123 on 2011-06-20
Hi guys.. the original poster on this thread is my mom.. let me give some additional details to the problem.. 

Now, the Vaio logo she mentioned on boot is the BIOS screen.. this led me to believe that the problem was hardware related.. so we sent it to a hardware repair shop, where the changed the wireless switch and graphics card to no avail.. we only just got it back, so please post with any opinions or solutions.

thanks

---


---
title: "Sudo'ing by default, is it possible?"
date: 2011-10-20
forum: General Help
---

### Post by 3Nex on 2011-10-20
I'd like it if either

[LIST]
[*]I'd be root by default right from the moment I open the Terminal, not having to go [FONT=Courier New]sudo -s[/FONT] every time I wanna do something. I am a sudoer and I'm the only one using this computer, so no harm done. or
[*]if I could just log in as **root** on my computer and use everything as root. I tried logging in as root at the startup login, but that doesn't seem to work.
[/LIST]
I'm using (the newest) Ubuntu. 
Thanks.

---

### Post by snowpine on 2011-10-20
Please read the Sticky thread at the top of the Security sub-forum:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by 3Nex on 2011-10-20
Okay I did and all I got from that experience was Don't log in as root to your computer cause it could be dangerous. Opening Terminal as root by default, on the other hand, wasn't mentioned in there, so it'd be awesome if you could point me to somewhere more specific on that subject or even offer a complete solution to the problem. I don't really know Linux that well and I'm not that much into the whole system administering stuff, I'm more a user type of guy. 

So, I guess what I want now is the first of my two proposals from the first post. That is -- to remain a "normal" user for anything outside of the Terminal, but when I open the Terminal I'm root right away. I'd imagine it to be a simple piece of code?

Sorry for being so needy (and lazy I guess). If you can come up with a solution, it'll be greatly appreciated.

---

### Post by spiky001 on 2011-10-20
The reason for not being root in terminal is it is a very powerfull tool. There are commands that you can put in that a click on the enter button NO MORE SYSTEM, even by mistake. Having to enter a password would give you time to think, or if you was user only the commands wouldn't execute.

---

### Post by kittshuldrunlinux on 2011-10-20
you could keep sudo su in your clipboard

---

### Post by coffeecat on 2011-10-20
> **3Nex said:**
> it'd be awesome if you could point me to somewhere more specific on that subject or even offer a complete solution to the problem.

You already have been. Go back to the link that snowpine posted. There's a link in that to the RootSudo wiki page. That has all that you need.

---

### Post by snowpine on 2011-10-20
> **3Nex said:**
> Okay I did and all I got from that experience was Don't log in as root to your computer cause it could be dangerous. Opening Terminal as root by default, on the other hand, wasn't mentioned in there, so it'd be awesome if you could point me to somewhere more specific on that subject or even offer a complete solution to the problem. I don't really know Linux that well and I'm not that much into the whole system administering stuff, I'm more a user type of guy. 

So, I guess what I want now is the first of my two proposals from the first post. That is -- to remain a "normal" user for anything outside of the Terminal, but when I open the Terminal I'm root right away. I'd imagine it to be a simple piece of code?

Sorry for being so needy (and lazy I guess). If you can come up with a solution, it'll be greatly appreciated.

You can easily open a root terminal with:

```
sudo -i
```

---

### Post by 3Nex on 2011-10-20
> **snowpine said:**
> You can easily open a root terminal with:

```
sudo -i
```
I guess I must have been misunderstood, maybe that's also why coffeecat told me there was an answer in the thread which I didn't see.

What I said was that  I wanted to avoid typing that every time i wanted to do stuff as root. Any time I'm opening Terminal anyway is because I want to do some sudo work, so why not just be logged in as root from the start. So, what I want is to be logged in to Terminal as root by default.

---

### Post by gsmanners on 2011-10-20
Well, since you're obviously aware of the risks. Here's is what you do:

```
export EDITOR=gedit && sudo visudo
```

Add this to the bottom (it MUST be at the bottom):

```
%dude ALL= NOPASSWD: /usr/bin/xterm
```

Where "%dude" is your name (or group if you want a group that can do this), and xterm is whatever terminal you want to be using for this.

Save and pray you didn't make a typo (which could result in having to reinstall in order to fix it). And hope someone doesn't sneak into your room and start messing around with xterm, of course. :D

---

### Post by 3Nex on 2011-10-21
> **gsmanners said:**
> Well, since you're obviously aware of the risks. Here's is what you do:

```
export EDITOR=gedit && sudo visudo
```Add this to the bottom (it MUST be at the bottom):

```
%dude ALL= NOPASSWD: /usr/bin/xterm
```Where "%dude" is your name (or group if you want a group that can do this), and xterm is whatever terminal you want to be using for this.
Thank you, but it didn't work. I rebooted in the meantime even, still no change. What could be wrong with it? The Terminal I use is gnome-terminal, so I wrote [FONT=Courier New]/usr/bin/gnome-terminal[/FONT] as path and replaced "dude" with my username. Then I tried doing apt-get while logged out from root, but it only displayed an error that I'm not root and did nothing. 


> **gsmanners said:**
> Save and pray you didn't make a typo (which could result in having to  reinstall in order to fix it).
As I said, any time I open Terminal anyway, is to do sudo work, so i just [FONT=Courier New]sudo -s[/FONT] right at the beginning and do everything else from there. Besides (a reference to spiky001's post), even if you [FONT=Courier New]sudo command[/FONT], you're not gonna have to enter your password for the next sudo command, so a typo would screw you just the same...

---

### Post by lightwarrior on 2011-10-21
You can activate root account in Ubuntu and login as root:

sudo passwd root

or if you want to remain on your user, after creating root type:

su

---

### Post by nothingspecial on 2011-10-21
The answer to your question is not supported here

> Policy
Tutorials explaining how to enable the root account for a graphical login or [COLOR="Red"]autologin[/COLOR] will not be supported on the forums and will be moved to the Jail.

Closed

---


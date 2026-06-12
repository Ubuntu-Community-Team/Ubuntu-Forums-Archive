---
title: "Newbie trying to ditch Windows and switch over - help!"
date: 2006-06-03
forum: General Help
---

### Post by wannaswitch on 2006-06-03
Okay, I don't know if this is the right forum for this topic, but if it's not, please don't bite my head off, I'm not a computer idiot, I'm just having some trouble getting up and running with Ubuntu 5.10.

The first time I tried to install it it did not detect my wireless network adapter (D-Link DI-524). The CD that came with my hardware only has the Windows driver. From that point on I was sunk because I couldn't access the internet for any upgrades or documentation (I had no other OS on my system to boot into. Scratch installation attempt #1.

After reinstalling the dreaded Windows so I could access the Internet (sad, I know), I did some research and found out about something called Ndiswrapper. My understanding is that Ndiswrapper will allow the Windows driver to work in Linux. Am I right? If so, how is this done? Ubuntu will not execute the EXE file that came on the D-Link CD, so regardless of Ndiswrapper, how is that supposed to happen?

My next question is this: how do you access the shell in Ubuntu? I've looked high and lo for a Root Terminal option (which is supposed to be in the Applications Menu under System Tools, if I'm not mistaken), but it goes straight from New Login to Run as Different User... No mention of Root Terminal. I have tried pressing Alt+Shift+F-whatever, but no other console is displayed. It seems like the simplest thing to do, but it seems like Ubuntu is so bent on being "user friendly" that it hides the shell! How do I get a simple, good old shell prompt?

Now, granted, that was on the Live CD. Maybe the full install has that option, I can't remember... but I don't want to risk blowing up my Windows install just to find out that it isn't there- and then I won't be able to get on the Internet to do anymore research about it!

I have some past experience with Linux and FreeBSD, so I know if I can get a shell prompt I'll be in business, I know how to use the sudo command to apt-get install ndiswrapper-utils, but I'm out of luck until I can make it show me the prompt at which to type that in! And if somebody could explain to me how Ndiswrapper is going to make it possible to use the Windows driver for my D-Link ethernet card, I'd really appreciate it.

So, just to sum up:

1) Once I have Ubuntu running and I'm looking at the GNOME desktop, how do I get to a shell prompt so I can type in commands the good old-fashioned way?

2) Once I install Ndiswrapper-utils, what's the next step for getting my D-Link card to work?

Thank you. I'd really like to ditch Windows and switch over, I just need a little hand-holding if you don't mind.

---

### Post by olsonar on 2006-06-03
well, i don't know about ndsiwrapper, but the shell is easy. it's under applications -> Accessories ->Terminal. if u need a root terminal, open alacarte/smeg (applicatons/system tools, respectively) and put a check next to root terminal under system tools.

---


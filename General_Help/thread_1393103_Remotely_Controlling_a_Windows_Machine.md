---
title: "Remotely Controlling a Windows Machine"
date: 2010-01-28
forum: General Help
---

### Post by sricks3 on 2010-01-28
I've been looking for a way to use my laptop (running Ubuntu) to help service a remote laptop (running Windows XP).

I've used TeamViewer and Cisco's VPN Client before, but TeamViewer is Windows only, and I don't want to pay for a Cisco system just to help maintain my friend's computer.

Ideally, I'm looking for something similar to the programs listed above, but I really just want to know if any of you have done this before, and if so, how?

Thanks!

---

### Post by rogue_0111 on 2010-01-28
Check out this thread:


[http://ubuntuforums.org/showthread.php?t=272986](http://ubuntuforums.org/showthread.php?t=272986)

I prefer logmein.

--

---

### Post by howefield on 2010-01-29
> **sricks3 said:**
> I've used TeamViewer and Cisco's VPN Client before, but TeamViewer is Windows only, and I don't want to pay for a Cisco system just to help maintain my friend's computer.

If you liked Teamviewer, be aware it runs perfectly through wine.

It isn't strictly windows only, it can be run (and is supported)  from Mac and Windows, and as I say, from Linux using Wine.

You can connect to a Mac or Windows machine from any of the 3 platforms, but you cannot connect to a Linux box as yet.

As others have said, there are plenty of good native choices, but just to make sure you know you are not restricted to Windows platform with Teamviewer.

---

### Post by Cyhawk on 2010-01-29
Are you in a position to just connect whenever asked? If so, Windows already has a built in method for this and there are a ton of great Linux programs for connecting to them. 

To setup the WinXP machine (Google for Vista/Win7, methods are effectively the same)
[http://www.microsoft.com/windowsXp/using/mobility/getstarted](http://www.microsoft.com/windowsXp/using/mobility/getstarted)
/Remoteintro.mspx

Make sure to setup your own account with a strong password, etc etc.

Then all you need is a Linux client. I prefer gnome-rdp. Its simple, effective, and works across the entire Win2k Family(2k, XP, 2003, Vista, 2008 and Win7). 

Its important to note, the remote machine will be inaccessible while you use it, they'll be presented with a "user\blah is logged in" screen.
Getting the IP address is easy as [www.whatismyip.com](www.whatismyip.com)

Or.. you can just go with VNC. TightVNC works (Has both server and client in both Linux and Windows) Though there are issues with VNC (aside from being slow, its also very insecure if your on untrusted connections, works best via Lan)

---

### Post by sricks3 on 2010-01-29
Thanks for all of the input.

I'm not sure why using TeamViewer via Wine never occurred to me. That probably should have been one of my first thoughts.

As for Windows' own RDP software, I've heard of people having some issues connecting with linux. Plus, unless I'm mistaken, my friend would have to be logged off in order for me to access her computer. This isn't a huge issue, but it would be nice for her to be able to watch what I'm doing.

I've considered VNC as well, but the issues that Cyhawk mentioned have kept me looking for something else.

Out of curiosity (and since I have the time), I'll probably end up trying all of these.

If anyone still has more ideas, please let me know. I'll be sure to tell y'all which of these ends up working best for me.

Thanks!

---


---
title: "XMMS2 player installed but can only get CLI interface not the GUI player HELP PLEASE!"
date: 2010-03-25
forum: General Help
---

### Post by Young God on 2010-03-25
Hello Linux World,

I'm trying to get my XMMS Player to work. I've been reading the linux bible and it has a whole section just on xmms player management. when I typed in xmms in the terminal i get :
<!--
 $ xmms
No command 'xmms' found, did you mean:
 Command 'lmms' from package 'lmms' (universe)
 Command 'xmds' from package 'xmds' (universe)
 Command 'xdms' from package 'xdms' (universe)
xmms: command not found
-->

So i went to synaptic package manager and installed xmms but all I found was xmms2 I guess its the newer version. I ended up installing it, but now when I type in xmms2 in the terminal (because if i type in xmms i get the same output as above), it brings me to a bunch of cli commands used for using xmms in the terminal. How do I get the "winamp" type GUI interface with xmms2, I tried looking for it in my applications menu (even under sound and video) and its nowhere to be found. I just wanna enjoy the player with its normal graphical tool not through the command prompt (which seems like the only choice right now). 

ps. I tried installing xmms through the terminal like this:
<!--
$ sudo apt-get install xmms
-->
and get this:
<!--
$ sudo apt-get install xmms
[sudo] password for ricky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
-->

and as I said before there's no xmms installer in synaptic only xmms2 (which I installed and got the CLI not the GUI version). I'm using Ubuntu Karmic Koala.

Young God
Linux Fanatic
Web Developer

---

### Post by johny_ on 2010-03-28
xmms has been removed from the ubuntu repositories. Xmms2 that you installed is a deamon player architecture. That simply means, that you can install only the core (lets call it "the base") then to get the GUI you will need a client. So search Google for "xmms2 frontend"

---

### Post by Young God on 2010-03-28
thanx I tried searching for one but it just seemed like too much work to get a player that looks like winamp going. Instead I moved to Audacious player which has a winamp looking player and works great.

Young God
Linux Fanatic
Web Developer

---


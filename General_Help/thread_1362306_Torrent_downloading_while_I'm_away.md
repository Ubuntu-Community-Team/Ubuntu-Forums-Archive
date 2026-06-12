---
title: "Torrent downloading while I'm away"
date: 2009-12-23
forum: General Help
---

### Post by kyle6513 on 2009-12-23
Okay, hello everyone! :)
I would like to create a server sort of installation of Ubuntu where it will download some set torrents out of a folder.
now here's the catch, I want to be able to see whats going on from anywhere around the world, aka I want a web interface for the torrents and for the computer for say, I want either terminal access (which is safe and secure) or atleast be able to see the temperatures of the computer and have a big shut down button. I already know how to turn the computer off at a certain time, so that's not an issue. Also, how would I go about making a script that when a torrent is finished, or a temperature goes over a set amount the computer will send an email to a set account. But if I somehow never receive the message about the temperature, about 10 degrees higher the computer will turn itself off.
Another thing, a script that if it finds no torrents are being downloaded it will send me an email and then turn the computer off, (it will turn itself back on through bios).

TL:DR?
I want to make a server that can
-download torrents
-send me emails if its overheating or finished downloading all the torrents
-be administrated from the internet

any input is greatly appreciated.
anyone who can find me a tutorial or MAKE a tutorial, I would be forever in your debt!
thanks!
I have 3 days so PLEASE HURRY

---

### Post by lovinglinux on 2009-12-23
Deluge has web interface, command-line and gtk remote interface, which means you can control your torrents on another machine with the same graphical interface, just like if you were downloading locally.

For controlling your machine remotely, use ssh.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

About the scripts, my brain is not functioning right now.

---

### Post by JoelOl75 on 2009-12-23
ktorrent has a php remote interface plugin.  You would need to set it up on a port, set up dyndns [http://dyndns.org](http://dyndns.org) to get a hostname that follows dynamic ip addresses (Unless you have a static IP)  set up your router with your dyndns account info and port forward your ktorrent webinterface port to your local machine address.

Or....

Install nomachines NX client, node, and server packages and install.  Set up openssh server, Preferably change the ssh default port from 22 to something else (In /etc/ssh/sshd_config and /usr/NX/etc/node.cfg and /usr/NX/etc/server.cfg)  Do the above with the dyndns stuff and the router config but instead port forwarding your SSH port.  Then installing the nomachine NX client on any computer you want to access your server with (Also has windows versions as well).  Then it's like your sitting at your servers desktop so you can run any bittorrent client you want (As well as remotely manage and run other apps!)

There's also VNC options, but for security nothing beats SSH IMO as VNC has had exploits and weak passwords in the past.  Plus nomachine nx is much faster (compresses better) so even on dial up it's usable.

---

### Post by nothingspecial on 2009-12-23
Sounds like what you need is screen and rtorrent with ssh. You`ve already been posted a link for ssh.

[[COLOR="Magenta"]Here[/COLOR]]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") and [[COLOR="Cyan"]here[/COLOR]]("http://wiki.archlinux.org/index.php/RTorrent") are 2 good rtorrent tutorials.

To use with screen simply log in to your computer remotely with ssh.
Launch screen, start rtorrent, then press Ctrl + D this will detach your rtorrent screen session.

Now shut down your remote computer, fly half way round the world. Find any computer with an internet connection and ssh installed. Log in remotely and type ```
screen -r
```

There you will see rtorrent happily going about it`s business as if you`d never left.

---

### Post by kyle6513 on 2009-12-23
Thanks for the replys guys!
I'm sure I'll be able to work out some scripts, although I have no idea what they would be coded in, hopefully I can work off someone else's scripts.

As for this, I'll follow your advice and I'll report back and see how its worked!
thanks alot! :)

---


---
title: "How to set up remote access to computer?"
date: 2010-05-03
forum: General Help
---

### Post by gldearman on 2010-05-03
Hi, all.

My home network consists of two computers that share one internet connection via a router.  I have a desktop computer that runs Ubuntu (Karmic), connected via ethernet; and a netbook that runs Windows 7 (will be Ubuntu, eventually), which connects wirelessly.

Both computers have multiple user accounts.

What I would like to do is access my account on the Ubuntu desktop via the netbook while my wife is using the desktop with her account (or enable her to access her account on the desktop while I am using it).

I have no idea how to set this up.  I looked into VNC, but it, apparently, only supports the active desktop.  So, if someone connected to the computer while it was in use, they would be looking at the other user's desktop. Is this a misconception on my part?

So, I have 3 questions:

[LIST]
[*]From the netbook, how can I log into my account on the desktop and just get a command-line shell?

[*]From the netbook, how can I log into my account on the desktop and actually have access to my Gnome desktop?

[*]If I leave my house with the netbook, and want to log into my desktop machine across the internet (CLI and/or Gnome), how can I do that?
[/LIST]
Thanks!

---

### Post by spiky001 on 2010-05-03
ssh and putty  have a google on those 2, I,m not sure about samba but that might be worth a google

---

### Post by gldearman on 2010-05-03
OK, so from googling around, here's what I'm getting ...

[LIST=1]
[*]Download ssh from the repos.  It should run automatically at startup, but if not, I know how to set it up in services (I think).
[*]Configure the firewall to allow ssh connections.  As of finsihing this step, I should be able to connect via CLI, either locally or via the internet, right? (Assuming the computer is on or can be woken.)  The bits below are for connecting to my Gnome desktop.
[*]Do something called configuring a VNC server to start in "once mode."  OK, I'm having a bit of a problem understanding this step.  The VNC server that comes pre-installed with Ubuntu doesn't, apparently, do this?  So I'll need to install another one? Is the package x11vnc what I need?
[*]Connect via ssh, then launch the vnc server in once mode from the command line, then connect via the vnc client on the netbook.
[/LIST]

OK, so here are my other questions:
[LIST]
[*]What do I do when I'm done with the remote desktop?  I know I can log out of SSH, but can I kill the Gnome desktop first, and how? If I am logging in over the internet, can I power down my box as I log out?
[*]Once mode apparently refuses all VNC connections but the first one.  If I'm, say, on a road trip and want to access my home box multiple times, this isn't going to cause problems, right? I'd connect with ssh, start the vnc server, then kill it, and then log in again and start a separate instance on my next login. That would work?
[/LIST]

---

### Post by Erik765 on 2010-05-03
Or, since it sounds like the PC you want to remote into is going to have a person at it, you could use a MUCH simpler approach with something like [logmein.com/express]("logmein.com/express")

I work for LogMeIn so if you need help let me know ;) 


...and no, this is not an advertisement because that product is completely free.

---

### Post by spiky001 on 2010-05-03
I dont know about Having 2 desktops running (i.e wife,s then remote to see mine)

have a look at this

[http://ubuntuforums.org/showthread.php?p=8761388](http://ubuntuforums.org/showthread.php?p=8761388)

---

### Post by gldearman on 2010-05-03
Erik --
I can't check that link out immediately because my employers have blocked that domain.  But, is that a secure connection?  I mean, I'd be passing all of my info through a third party.  Is that encrypted end-to-end? I'm sure you and your employers are honest, but I can never tell if your server has been compromsed by black hats (not that black hats are real interested in my business, but my wife might use this for business, which would include clients' SSNs and credit information).  I'd prefer to use a more secure connection like ssh (I mean, unless your service provides a secure connection).

spiky --
That link looks perfect.  I say "looks," 'cause I can't understand a dang word of it.  But once I have time to read it real slow and try to follow the directions, it appears to be just what I was looking for!

Thanks to both.  I'll probably be back to this thread with more questions.

---

### Post by Erik765 on 2010-05-03
It is extremely secure. I would say even more so than a p2p connection over ssh. I know off the top of my head it uses up to 256 encryption overall.

Here is a security white paper if you're interested.

[http://c1323042.cdn.cloudfiles.rackspacecloud.com/LogMeIn_SecurityWhitepaper.pdf]("http://c1323042.cdn.cloudfiles.rackspacecloud.com/LogMeIn_SecurityWhitepaper.pdf")

Our product has proven itself by being very usable and secure and we serve millions of customers either personally or for business needs every day.

It may not be able to do everything you need however, because there are no default Linux clients, but you would be able to use our web-based products for at least accessing other computers (windows, linux, mac) the express link I sent you uses the same encryption methods as the other products and is web based.

---

### Post by mobi on 2010-05-03
Check out FreeNX if you're looking to connect to a graphical desktop.  SSH is the way to go if you do not need graphics.

---

### Post by Erik765 on 2010-05-03
Ah yes, FreeNX. Forgot about that one. Used it. Very good solution. Does not require someone to be at host (remote) pc and installs natively in Linux.

---

### Post by gldearman on 2010-05-03
Well, having read the thread that spiky001 linked to, it looks like FreeNX is probably the way to go.  Looks a good bit harder to set up than x11vnc, but is allegedly faster and more secure.  So, I'll give it a try.

The linked thread also linked to this handy [table]("http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software"), which compares a lot of this software.  That table does include LogMeIn, which is, in fact, encrypted with SSL.  But LogMeIn, according to the table, doesn't appear to support file transfer (in the free version), so it isn't quite as useful.

Thanks for the help, everyone!

---


---
title: "Remote Desktop Options"
date: 2011-09-03
forum: General Help
---

### Post by Joshua on 2011-09-03
I have remote desktop access set up to my home server/desktop (Ubuntu Desktop 11.04), but it's not very responsive and the resolution is difficult to work with.  Does anyone know of more customizable ways for getting remote desktop access to Ubuntu?

I've searched for other options, but I don't really know what words to use for a search.  Here's the situation:

My server/desktop hosts shared files, printers, websites, and other typical and some more advanced server stuff.  It uses the desktop rather than server version of Ubuntu because I also use it for word processing, money management, some software development, and other typical desktop things.

Most desktop applications I use aren't really optimized for use over a network, so I can't just install them on a laptop to work on things that were started on the server/desktop.  That's why I set up remote desktop - to do quick desktop-type things on the server/desktop itself.  As I said at the start, it's slow and uses the really high resolution of the desktop, which won't easily fit on the small screens of the laptops.  I don't want to change the resolution of the desktop because I'd have to keep going back and forth every time I changed where I was working.

I think the ideal solution would be to have one GUI (with a unique resolution and maybe even other customized settings) that I see when I log in remotely, and a different GUI that I see when I log in locally.

Any ideas how to make this work?

---

### Post by Toz on 2011-09-03
What I do is ssh into the server with X forwarding enabled and run the server apps but display them on my laptop display. Here is how:

1. From the laptop:
```
ssh -X xxx.xxx.xxx.xxx
```
where xxx.xxx.xxx.xxx is the ip of the server. Note, that I have enabled X forwarding on the server in sshd_config file.

2. From the laptop, I run the server application and it displays on my laptop:
```
xterm &
```
and the server xterm window displays on my laptop.

---

### Post by Joshua on 2011-09-03
That sounds like it could be the best option for me.  If only the application interface is forwarded to the client, then resizing windows would be handled by the application.  Can I do this from a Windows computer with putty or would it only work from a Linux client?

---

### Post by Toz on 2011-09-03
You could do this from a windows computer, but you would need to install an xserver on windows. xming ([http://www.straightrunning.com/XmingNotes/]("http://www.straightrunning.com/XmingNotes/")) or cygwin/X ([http://x.cygwin.com/]("http://x.cygwin.com/")) come to mind (xming appears to be "donationware" now). I'm using cygwin/X.

Once you have one of these installed and running, fire up putty, enable the X11 forwarding option (Connection->SSH->X11) and set the "X11 Display Location" to **localhost:0**. Then in the putty window try:
```
xterm &
```
and it should show up on your MS Windows desktop.

EDIT: When installing cygwin/X, make sure you install the xinit package from the X11 section. Also, you can bypass the need for putty if you also install the openssh package from the net section. You can then startup cygwin/X, and in the terminal window that opens, type in:
```
ssh -X -l <userid> xxx.xxx.xxx.xxx
``` to open the ssh connection and then run your apps from there.

---


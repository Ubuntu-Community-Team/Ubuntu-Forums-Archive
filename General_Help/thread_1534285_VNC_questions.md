---
title: "VNC questions"
date: 2010-07-19
forum: General Help
---

### Post by Zorgoth on 2010-07-19
I am trying to VNC into a server to which I have no physical access (but I can ask someone to start a session or something) but can ssh into.  I have gotten a VNC session working by sshing in and running vncserver, although once the VNC session died in a confusing manner.

I don't know how to start a VNC session any way but vncserver, which is odd since I'm sure that Ubuntu's Remote desktop should somehow allow me to do this by default.  The server by the way is being used as a desktop by someone else.

Also, how do I tell if my VNC is encrypted and if it isn't how do I make sure it is?

---

### Post by cariboo on 2010-07-19
I would reaaly suggest you not use VNC on a server, especially as it is one of the quickest ways to get your server cracked. Use X-forwarding instead. Use the following command to enable X-forwarding:

```
ssh -X user@server
```

then type the name of the application you want to run at the prompt.

---

### Post by bodhi.zazen on 2010-07-19
> **Zorgoth said:**
> I am trying to VNC into a server to which I have no physical access (but I can ask someone to start a session or something) but can ssh into.  I have gotten a VNC session working by sshing in and running vncserver, although once the VNC session died in a confusing manner.

I don't know how to start a VNC session any way but vncserver, which is odd since I'm sure that Ubuntu's Remote desktop should somehow allow me to do this by default.  The server by the way is being used as a desktop by someone else.

Also, how do I tell if my VNC is encrypted and if it isn't how do I make sure it is?

You should not, IMO, use VNC to manage a server. VNC is insecure and does not help much, if at all.

Most of server management is starting / stopping services or editing config files, so VNC does not add much.

Either forward X applications or better use a web based control system, such as webmin or phpmyadmin.

If my must, be sure to secure your ssh server and I advise you tunnel VNC over ssh.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by pricetech on 2010-07-19
You might also try NX from nomachine dot com.  They have Client, Node, Server for Linux and Client for windows.  That's what I use and it works like a charm for me.

---

### Post by Zorgoth on 2010-07-19
I am not talking about the kind of server you are thinking about; this "server" is a big powerful computer in my office for doing heavy numerical computations.  My connection to it is over a secure and heavily firewalled local network.  The problem with ssh -X is that some of my processes take many hours and a problem with the web connection could kill an entire process without me knowing until the next day.  I have already lost basically a day of work because of ssh doing just that.

One thing to note is that all of my processes can be started from the command line without X fairly easily; is there a nice way to have a VNC-like session to a console that would be stable and moderately secure (basically I want to be able to start the process on my desktop and then be able to have whatever happen to my network, or my desktop crashing, without any problems for the process)?

---

### Post by bodhi.zazen on 2010-07-19
> **Zorgoth said:**
> I am not talking about the kind of server you are thinking about; this "server" is a big powerful computer in my office for doing heavy numerical computations.  My connection to it is over a secure and heavily firewalled local network.  The problem with ssh -X is that some of my processes take many hours and a problem with the web connection could kill an entire process without me knowing until the next day.  I have already lost basically a day of work because of ssh doing just that.

One thing to note is that all of my processes can be started from the command line without X fairly easily; is there a nice way to have a VNC-like session to a console that would be stable and moderately secure (basically I want to be able to start the process on my desktop and then be able to have whatever happen to my network, or my desktop crashing, without any problems for the process)?

Are you familiar with screen ?

Screen will allow you to ssh in and run processes. You can then "detach" form the screen session and close the ssh session, your command continues to run.

Later, you ssh in and "reattach" to the screen session.

See :

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

[http://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-](http://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-)

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

---

### Post by anon.jdh on 2010-07-19
I use ssh tunneling with VNC so I can get to my machine at home. It's very secure as the only exposed port on my router is 22 (SSH).

Here's a great tutorial:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Enabling compression helps and if you want to use a local X-server to run individual applications, I would try Cygwin's X-Win Server on your local machine after tunneling with SSH.

---

### Post by techunit on 2010-07-19
I can agree with not using VNC to access a server... A VPN works alot better and much more secure... But the company has to have to VPN client installed for you to do it...

---

### Post by Zorgoth on 2010-07-20
Thank you bodhi.zazen; screen is beautiful and does everything I need together with ssh -X after the processing is done to get the pictures.  I am never messing with VNC again; I hate the stupid graphics anyway.

---

### Post by Zorgoth on 2010-07-20
Out of curiosity, is there screen for OS X/Windows; I don't use them but others in the office do.

---

### Post by bodhi.zazen on 2010-07-20
> **Zorgoth said:**
> Out of curiosity, is there screen for OS X/Windows; I don't use them but others in the office do.

For Windows I would suggest using screen under cygwin

[http://www.cygwin.com/](http://www.cygwin.com/)

[http://benjisimon.blogspot.com/2009/04/preferred-cygwin-screen-version.html](http://benjisimon.blogspot.com/2009/04/preferred-cygwin-screen-version.html)

Screen is available for OSX as well

[http://sourceforge.net/projects/screen-osx/](http://sourceforge.net/projects/screen-osx/)

I have not used screen on either windows or OSX.

---


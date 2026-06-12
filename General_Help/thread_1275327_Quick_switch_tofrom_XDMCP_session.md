---
title: "Quick switch to/from XDMCP session?"
date: 2009-09-25
forum: General Help
---

### Post by t0p on 2009-09-25
I need to do some stuff that involves both my desktop machine and my netbook.  I've set the machines up so I can log into the desktop computer from the netbook over XDMCP.

I want to be able to switch quickly from the XDMPC session to a normal local session and back again.  But I can't see how to do that.  I have just the one user account on the netbook, so when I click on "Switch users or shut down" I'm offered just Guest ession, Lock screen, Log Out, Suspend, Hibernate, Restart... and Shut Down.. ie no Switch user option.  So if I'm in my local user session and I want to switch to an XDMCP session, I have to log out of the local session then log into the XDMCP session.  And vice versa.  Which is slow as hell and a pain.

How can I switch quickly between an XDMCP session and a normal local session?

---

### Post by geirha on 2009-09-25
Applications -> Internet -> Terminal Server Client, choose XDMCP as the protocol. If XDMCP is greyed out, you need to install the [xnest](apt://xnest) package.

Another option is to set up FreeNX instead. See [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX).

---

### Post by t0p on 2009-09-25
Okay, I installed the xnest package, and tried to use Terminal Server Client to log into the desktop computer.  I got through the login okay, and the Terminal Server Client started to draw the remote Desktop.  But then there was an error, as shown in the attached screenshot.

What's up with the Terminal Server Client?  Is this problem fixable?

---

### Post by geirha on 2009-09-25
I'm afraid that error message doesn't tell me much, but I found a bug report on it: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/296122](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/296122)

After skimming through the bug report, freenx seems like the quickest workaround, though I really hope that bug will be fixed soon.

---

### Post by t0p on 2009-09-25
I installed freenx-server on the dektop computer, and I installed lx client for linux, all as described[ here]("https://help.ubuntu.com/community/FreeNX").   When I try to log in, it goes through all the stages of login (I think), then the freenx window opens for just an instant.  Then it disappears.

I also tried qtnx, the open source client.  And this did the same: opened the freenx window for a flash, then it vanished.

The fix described in this blog doesn't do anything.  But I suspect it's for a different problem.  Even though it sounds the same:freenx window appears then disappears.  This fix is for an ssh authentication problem, and I don't think that's what's wrong with mine - the messages at the bottom of the freenx login page says that authentication has been successful, and more messages follow, until the window flashes on then off.

Any tips how I might fix this?  Or Terminal Server Client.  Or another way...

---

### Post by t0p on 2009-09-26
Okay, I fixed the problem by following instructions [here]("https://help.ubuntu.com/community/FreeNX"):

> 

[LIST]
[*]Problem: At the client, the !M logo window appears, but after a few seconds that window just closes, even without showing any error message. 
[*]Solution: In the server, access your home directory and run this command, sudo rm .Xauthority* followed by touch .Xauthority and finally chmod 600 .Xauthority . This issue is due custom VNC configuration.
[/LIST]
All better now.

---


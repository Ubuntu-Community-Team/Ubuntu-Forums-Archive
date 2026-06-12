---
title: "Can't use remote desktop over the internet"
date: 2010-10-08
forum: General Help
---

### Post by Meph1st0 on 2010-10-08
I want to be able to use my desktop from work over VNC but it won't let me connect.  In the Remote Desktop Preferences I have "Allow other users to view your desktop" checked and I also have "Allow other users to control your desktop" checked.  But it says below that "Your desktop is only reachable over the local network. Others can access your computer using the address 192.168.1.10 or brownserver.local."

Under the Security section I have "Require user to enter this password" checked and I've filled in a password for it.

I've also port forwarded port 5900 to my desktop on my router so that shouldn't be an issue either.  When I attempt to connect over the internet from my laptop I get a message that says that the connection was refused.  So I think my request is at least making it to the desktop, it's just that the desktop doesn't want to allow it.

One quick question though....I'm not sure, but I might have changed the default port on which VNC is listening on this machine.  I don't remember if I did or not.  And if I did, I don't remember how I did it.  Could someone point me in the proper direction to see which port remote desktop is listening on?

---

### Post by 98cwitr on 2010-10-08
You realize that 192.168.1.10 is your private subnet right? You need to use your public IP address

Read this: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by pricetech on 2010-10-08
VNC is inherently insecure and should not be exposed to the Internet.

Use SSH instead.  If you need a GUI, install NX from nomachine dot com.  Client, Node, Server on your Ubuntu box and Client on your laptop.

Make sure open ssh server is installed on your desktop also.

---

### Post by Meph1st0 on 2010-10-08
98cwitr,

I am aware that that's my private IP.  I'm not attempting to access the machine over the internet by using the private IP.  If you reread my post I was only quoting the message that appears on the remote desktop configuration page.  And I was quoting it because I believe that that is part of the problem.  The computer itself is indicating that it can only be remotely controlled by the someone on the local domain.  What I want to do is configure it such that I can access it over the internet.  But I can't seem to figure out how to do it.  If I enter MyPublicIP:5900 in VNC then the computer refuses the connection.

Thanks again.

Pricetech,

That's good to know that VNC is inherently insecure.  It's not a big surprise.  It doesn't surprise me either that there are other and better alternatives.  And at some point I'll likely switch to one of those alternative.  Nevertheless, I'm a very stubborn man when it comes to a problem that I can't fix.  Can you help me fix the problem at hand and then I'll look into more secure alternatives?

Just FYI, SSH is working fine on the machine and I have no issues connecting to it remotely.  It is; however, in this case the GUI that I'm after.  There are some small occasions when I prefer the GUI over the CLI.

Thanks again.

---


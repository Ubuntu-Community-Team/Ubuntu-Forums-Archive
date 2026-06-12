---
title: "SSH into desktop on remote network"
date: 2010-01-20
forum: General Help
---

### Post by sublimation on 2010-01-20
I've run into a bit of a problem with an attempt to remotely admin a friend's computer. Here's the basic layout:

--My Ubuntu is connected via wireless router, port 22 forwarded properly. I can ssh in and out as I please to other hosts.
--Across the internet, their Eeebuntu is behind a router as well. Port 22 may or may not be properly forwarded. Nobody in that house really knows how to access their router. (I accept this may be an issue I'll need to handle)

What I'd like to do:
First priority, ssh access to the remote Eeebuntu.
   Assuming the remote router does not forward port 22, would I be able to have the remote computer remote forward, say my local port 10022 to remote 10022, thus allowing me to ssh user@localhost:10022 and bypass the need to access the router?

Lower priority, prepare a bash script for my friend to download that would require one input of the root password, and go through the full process of installing OpenSSH, setting up the server, and initiating contact to my computer. The ideal situation is allowing my friend to start the computer, run one script, type in one password, and walk away.

Any ideas for better remote admin options are welcome, as well as comments/suggestions from anyone who has attempted this backwards form of ssh access.

---

### Post by Brandon Williams on 2010-01-21
If your friend runs 'ssh -R10222:localhost:22 yourbox', then you will be able to connect back through the tunnel to sshd on your friend's machine. You could easily simplify that be providing a script for your friend to run and a desktop icon to click that will run the script. If you configure the system for key-based authentication, then your friend won't even have to enter a password in order to connect to your machine.

The script you describe seems like a simple enough way to get the initial configuration done. Once it's there, then the desktop icon idea will make things even simpler in the future.

---

### Post by sublimation on 2010-01-21
Great! That was a nice solve for the first step. I've always had trouble understanding the difference between the -L and -R flags and which does which. While it's intuitive once you know, it's a devil to figure out through the man pages.

some trial and error on a similar system and I was able to create the kind of access I was looking for. But now I have a related question:

What's the lowest bandwidth form of remote gui usage?
   I've done a fair amount of VNC and X-forwarding in the past. Using the x11vnc utility on the remote host and vncviewer -via remotehost localhost:# is usually successful, but has crawling responses over a less than ideal network situation (say a low signal wireless remote host!). 
   X-forwarding, while improved on the bandwidth, tends to have inexplicable problems when diving through too many hoops (I'll often forward successfully through five hosts one direction, but a direct connection on the way back yields "wrong authentication" issues).

Any other ideas for GUI usage on a remote host?

-sublimation

---


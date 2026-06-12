---
title: "remote desktop viewer"
date: 2010-03-26
forum: General Help
---

### Post by krishna1650 on 2010-03-26
Hello all, I am using Remote Desktop Viewer from other machines, to see my desktop. But it only shows the desktop, nothing else, like if i open a file, it doesn't show the gedit in the other machines.

Can anyone provide the correct procedure?
Thanks.

---

### Post by HermanAB on 2010-03-26
What is the other machine, Linux?  VNC is mainly a Windows thing and should not be used on Linux (unless you are doing user training sessions on a LAN).

VNC is an abomination that should not be lightly discarded.  It should be thrown, with great force.  It is insecure and will eventually result in your machine being compromised, since there are automated attack scripts that will find it.  These forums are awash with complaints from sad users that had VNC broken into.

You should kill the VNC process and rather use SSH:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

will launch gedit remotely and run it transparently on your local desktop.

You can also run a remote panel and go click happy:
$ ssh -X -C -c blowfish user@server gnome-panel

---

### Post by krishna1650 on 2010-03-26
> **HermanAB said:**
> What is the other machine, Linux?  VNC is mainly a Windows thing and should not be used on Linux (unless you are doing user training sessions on a LAN).

VNC is an abomination that should not be lightly discarded.  It should be thrown, with great force.  It is insecure and will eventually result in your machine being compromised, since there are automated attack scripts that will find it.  These forums are awash with complaints from sad users that had VNC broken into.

You should kill the VNC process and rather use SSH:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

will launch gedit remotely and run it transparently on your local desktop.

You can also run a remote panel and go click happy:
$ ssh -X -C -c blowfish user@server gnome-panel

Thanks for the reply. Both machines are ubuntu 9.10. Actually i want to do everything, not only editing by gedit. I want to control all the things from other machines, it's needed because i have to show some experiments running on my machine to others from their machines. Hopefully, i am able to clear the problem.

Thank you once again.

---

### Post by 3rdalbum on 2010-03-26
> **HermanAB said:**
> What is the other machine, Linux?  VNC is mainly a Windows thing and should not be used on Linux (unless you are doing user training sessions on a LAN).

VNC is an abomination that should not be lightly discarded.  It should be thrown, with great force.  It is insecure and will eventually result in your machine being compromised, since there are automated attack scripts that will find it.  These forums are awash with complaints from sad users that had VNC broken into.

[Citation Needed]

VNC is multi-platform. RDP is a "Windows thing".

VNC is perfectly secure when run across a network, where the network gateway has a firewall and you're not forwarding the VNC port to the Internet.

X forwarding using SSH is a good solution, but it doesn't allow the person to interact with the full desktop.

---

### Post by rejuvenate on 2010-03-26
i am also facing the same problem but when i start the remote desktop viewer then it shows the remote screen of that time i am even able to use the option on remote desktop but the view remains same in my desktop where as it changes in remote desktop..I am using it over lan ...is this due to speed and also i need any secure way of doing this..

---

### Post by cjhabs on 2010-03-26
> **3rdalbum said:**
> [Citation Needed]

VNC is multi-platform. RDP is a "Windows thing".

VNC is perfectly secure when run across a network, where the network gateway has a firewall and you're not forwarding the VNC port to the Internet.

X forwarding using SSH is a good solution, but it doesn't allow the person to interact with the full desktop.

I believe you can interact with the full desktop by using Xnest or Xephyr - I have done this running a Mac OSX client and displaying a Solaris Gnome desktop - but I haven't tried it under Ubuntu.

---

### Post by krishna1650 on 2010-03-26
> **rejuvenate said:**
> i am also facing the same problem but when i start the remote desktop viewer then it shows the remote screen of that time i am even able to use the option on remote desktop but the view remains same in my desktop where as it changes in remote desktop..I am using it over lan ...is this due to speed and also i need any secure way of doing this..

I am little confused about your problem, is your own desktop is working well or the other machine is working well? Well in my case, my desktop is changing but this changes are not shown in other machines, from where i am trying to access my machine.

---


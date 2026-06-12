---
title: "OpenVPN - anyone know anything on this?"
date: 2011-01-11
forum: General Help
---

### Post by listerdl on 2011-01-11
Am I correct that OpenVPN you can install it on a machine that can be static, say a Desktop machine and then on another machine access the files from the static desktop?

So basically to get this to work you need to install the package and then confiure it?

I guess my real question is - how do you access the static desktop - through an IP address? 

Is this difficult to set up - seems fairly difficult - thanks!

---

### Post by Kljuka on 2011-01-11
Actually as I understand OpenVPN is for Virtual Private Networks:
for example it's meant for connecting safely into your home network from other places (for example: you travel somewhere and want to connect safely to your home network).

Using OpenVPN, you can create connection (tunnel) to your home network. That means that your compuater at remote location becomes a member of your home network. You still need to connect to your computer.

For that last step, you can use:
- SSH server (to connect to computer with "terminal")
- some VNC (for remote desktop functionality) or other program.

---

### Post by veggen on 2011-01-11
What exactly do you mean by "accessing"? File sharing? Remote desktop?
And as Kljuka said, unless you're trying to remotely join a network, you don't need VPN.

---


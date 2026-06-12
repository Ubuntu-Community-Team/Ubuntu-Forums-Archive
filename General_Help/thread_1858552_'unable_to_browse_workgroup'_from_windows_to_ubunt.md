---
title: "'unable to browse workgroup' from windows to ubuntu"
date: 2011-10-12
forum: General Help
---

### Post by andrew.taylor on 2011-10-12
hi all.
I'm running a network with an ubuntu server with xubuntu installed. I've installed webmin and the samba module to run a couple of file shares. Then I decided to set up a VPN on this server using the PPTP protocol, to gain access to the shares from a remote pc. 

I've downloaded PPTPD from Ubuntu Software Center and modified these four files :
/etc/pptpd.conf
/etc/ppp/pptpd-options
/etc/ppp/chap-secrets
-> /etc/init.d/ restart 
/etc/sysctl.conf
-> sysctl -p
.. following this link (in italian) : [www.ilsoftware.it/articoli.asp?id=6670&pag=0]("http://www.ilsoftware.it/articoli.asp?id=6670&pag=0")

everything was working quite good, even if my surfing from home to the remote network was quite slow, I'd think this was due to the remote adsl speed .. 

then .. after a black-out, things changed to the worse.

now everything is working fine again in the network, but I can't remotely enter the workgroup from my xp (or win7, it's the same) computer at home. it says 'unable to browse workgroup' and something about permissions. 

looks like something's gone corrupted ..

I've checked everything, samba configuration, vpn config, .. but the problem is still there.
If I connect to the remote network, I can ping the server IP, I can still access the the remote surveillance cameras .. but  I can't access the workgroup.
on my xp pc, there's a link in the net resources that points to one of the two remote shares .. if I double click on it, I can access to the remote folder .. strange enough ..

moreover, my speed connection slows down when connected to the remote network.

don't know anything else to do ..

can anyone help?

---


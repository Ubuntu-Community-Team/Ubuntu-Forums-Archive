---
title: "problem with network-manager-pptp"
date: 2011-11-15
forum: General Help
---

### Post by Riuzaki90 on 2011-11-15
I've a problema with the VPA CAble connection of my university...
on the website of the university there's a .sh file that set all the  variables of the connection in ETC/PPP/PEERS and another .sh file that  call the connection...I'm on ubuntu 11.10 and when I run the setup.sh I  have this error:

impossible to find network-manager-pptp

these are the two file that I had talk about:

```
#!/bin/bash 
echo "Creazione della connessione in corso attendere........."  
apt-get update 
apt-get install pptp-linux network-manager-pptp 
echo -n "Digitare la propria Username: " 
read USERNAME 
echo -n "Digitare la propria Password: " 
read PASSWORD 
pptpsetup --create UNICAL_Campus_Access --server 160.97.73.253 --username $USERNAME --password $PASSWORD       
echo  'pty "pptp 160.97.73.253 --nolaunchpppd"' >/etc/ppp/peers/UNICAL_Campus_Access 
echo 'require-mppe-128' >>/etc/ppp/peers/UNICAL_Campus_Access 
echo 'file /etc/ppp/options.pptp'>>/etc/ppp/peers/UNICAL_Campus_Access 
echo 'name '$USERNAME''>>/etc/ppp/peers/UNICAL_Campus_Access 
echo 'remotename PPTP'>>/etc/ppp/peers/UNICAL_Campus_Access 
echo 'ipparam UNICAL_Campus_Access'>>/etc/ppp/peers/UNICAL_Campus_Access 
echo  $USERNAME' PPTP '$PASSWORD' *'>>/etc/ppp/chap-secrets 
rm  /etc/ppp/options.pptp 
echo '###############################################################################'>/etc/ppp/options.pptp 
echo '# $Id: options.pptp,v 1.3 2006/03/26 23:11:05 quozl Exp $'>>/etc/ppp/options.pptp 
echo '#'>>/etc/ppp/options.pptp 
echo '# Sample PPTP PPP options file /etc/ppp/options.pptp'>>/etc/ppp/options.pptp 
echo '# Options used by PPP when a connection is made by a PPTP client.'>>/etc/ppp/options.pptp 
echo '# This file can be referred to by an /etc/ppp/peers file for the tunnel.'>>/etc/ppp/options.pptp 
echo '# Changes are effective on the next connection.  See "man pppd".'>>/etc/ppp/options.pptp 
echo '#'>>/etc/ppp/options.pptp 
echo '# You are expected to change this file to suit your system.  As'>>/etc/ppp/options.pptp 
echo '# packaged, it requires PPP 2.4.2 or later from http://ppp.samba.org/'>>/etc/ppp/options.pptp 
echo '# and the kernel MPPE module available from the CVS repository also on'>>/etc/ppp/options.pptp 
echo '# http://ppp.samba.org/, which is packaged for DKMS as kernel_ppp_mppe.'>>/etc/ppp/options.pptp 
echo '###############################################################################'>>/etc/ppp/options.pptp 
echo '# Lock the port'>>/etc/ppp/options.pptp 
echo 'lock'>>/etc/ppp/options.pptp 
echo '# Authentication'>>/etc/ppp/options.pptp 
echo '# We do not need the tunnel server to authenticate itself'>>/etc/ppp/options.pptp 
echo 'noauth'>>/etc/ppp/options.pptp 
echo '#We won"t do PAP, EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2'>>/etc/ppp/options.pptp 
echo '#(you may need to remove these refusals if the server is not using MPPE)'>>/etc/ppp/options.pptp 
echo 'refuse-pap'>>/etc/ppp/options.pptp 
echo 'refuse-eap'>>/etc/ppp/options.pptp 
echo 'refuse-chap'>>/etc/ppp/options.pptp 
echo 'refuse-mschap'>>/etc/ppp/options.pptp 
echo '# Compression Turn off compression protocols we know won"t be used'>>/etc/ppp/options.pptp 
echo 'nobsdcomp'>>/etc/ppp/options.pptp 
echo 'nodeflate'>>/etc/ppp/options.pptp 
echo '# Encryption'>>/etc/ppp/options.pptp 
echo '# (There have been multiple versions of PPP with encryption support,'>>/etc/ppp/options.pptp 
echo '# choose with of the following sections you will use.  Note that MPPE'>>/etc/ppp/options.pptp 
echo '# requires the use of MSCHAP-V2 during authentication)'>>/etc/ppp/options.pptp 
echo '# http://ppp.samba.org/ the PPP project version of PPP by Paul Mackarras'>>/etc/ppp/options.pptp 
echo '# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o'>>/etc/ppp/options.pptp 
echo '#{{{'>>/etc/ppp/options.pptp 
echo '# Require MPPE 128-bit encryption'>>/etc/ppp/options.pptp 
echo '#require-mppe-128'>>/etc/ppp/options.pptp 
echo '#}}}'>>/etc/ppp/options.pptp 
echo '# http://polbox.com/h/hs001/ fork from PPP project by Jan Dubiec'>>/etc/ppp/options.pptp 
echo '#ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o'>>/etc/ppp/options.pptp 
echo '#{{{'>>/etc/ppp/options.pptp 
echo '# Require MPPE 128-bit encryption'>>/etc/ppp/options.pptp 
echo '#mppe required,stateless'>>/etc/ppp/options.pptp 
echo '# }}}'>>/etc/ppp/options.pptp 
echo "setup di 'UNICAL Campus Access' terminato correttamente" 
echo "per connettersi eseguire lo script 'UNICAL_Campus_Access.sh' "  
 

```
```
#!/bin/bash
echo "Connessione alla Rete del Centro Residenziale in corso attendere........." 
modprobe ppp_mppe
pppd call UNICAL_Campus_Access

sleep 30
tail  -n 8  /var/log/messages

echo "Connessione Stabilita"


echo -n "Per terminare la connessione premere invio (in alternativa eseguire il commando 'killall pppd'):---->   "
read CONN


killall pppd


echo "Connessione terminata"





```

I've correctly installed network-manager-pptp to the latest version...help?

---

### Post by Riuzaki90 on 2011-11-16
nobody answer me?

---


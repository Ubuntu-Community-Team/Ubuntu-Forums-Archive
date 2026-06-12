---
title: "VSFTPD blues :("
date: 2009-07-31
forum: General Help
---

### Post by anubix on 2009-07-31
OKAY, here's the poop:

Goal: Place large sound files in a folder; gain access to said folder from outside the network via ftp.

Method: VSFTPD came very highly recommended from a friend
(would like to use ssh, but at this point i'll take what i can get)

Procedure: Installed and configured /etc/vsftpd.conf & made a user.  Still need to figure out where to tell vsftpd where this user's folder will be, and assign appropriate privelages.

Having difficulty forwarding ports.
I have a wrt54gs running dd-wrt.
Goal is to connect externally to ftp on port user.noip.com:XX87, and forward it to 20.. or so i thought.
All of the searching I have done reveals that ports 20 AND 21 need to be forwarded.
However, when I attempt to setup port range forwarding (start on 20 end 21) I am not given outside ports to forward from.  I am not certain my isp (or noip.com for that matter) are going to allow me to get 20 and 21 inbound.

If there is already a good how-to on this I have done considerable searching and have come up with nothing.

If someone could point me in the right direction, i may end up not banging my head against a wall when the sun rises.

thanks

---


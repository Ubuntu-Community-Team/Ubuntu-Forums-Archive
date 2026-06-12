---
title: "Ubuntu 9.04 server SSH connection not persistent"
date: 2009-07-22
forum: General Help
---

### Post by 2cjh on 2009-07-22
I seem to be having ssh issues on ubuntu?  On initial connect using PuTTY, NX, or Cygwin (ssh) I am logged in for some period of time (few seconds to several minutes) before the connection dies with the following errors:

-->
PuTTY Fatal Error
Network error: Software caused connection abort
<--

-->
NX
The connection with the remote server was shut down.  Please check the state of your network connection.
<--

subsequent attempts either log me in for a short time or fail all-together.

server config:
Ubuntu 9.04 (jaunty) kernel 2.6.28-13-server
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g
nomachine NX Free Edition Server

I tried connecting using the nomachine NX clients for Windows and Linux, along with PuTTY and Cygwin on winXP.

I have had this setup for months with no problems until recently.  I turned on ssh debug logging, looked in auth.log, and found an unusually large number of dbus-daemon messages.  I could post the log if it will help.  Thanks.

---

### Post by cariboo on 2009-07-22
Do the easiest thing first, change the nic and see if that clears up the problem.

---

### Post by 2cjh on 2009-07-22
Issue resolved.  Another host was configured with the same static ip.

---


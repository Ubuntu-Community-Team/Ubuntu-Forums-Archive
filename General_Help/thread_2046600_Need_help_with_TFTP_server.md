---
title: "Need help with TFTP server"
date: 2012-08-23
forum: General Help
---

### Post by jhall1990 on 2012-08-23
Hello everyone,

I am running Ubuntu 10.04 and I am trying to set up a tftp server. It is currently working but I am unable to put new files unless they already exist on the server. I understand that this is a security feature but I work in a secure lab so I would like to enable it, unfortunately I have no option to do so.

I found a man page online that provides the -c flag that I need but I am unable to figure out what package it is from. I googled tftpd man page as that is the server that I am using, but my man page looks nothing like the one found here, [http://linux.die.net/man/8/tftpd](http://linux.die.net/man/8/tftpd). Could someone please provide me with the package that this man page describes? or at least point me in the right direction?

Thanks in advance.

---

### Post by sepo on 2012-08-23
can you post the result of your ```
man tftpd
``` ?

---

### Post by jhall1990 on 2012-08-23
Sure here it is,

```
TFTPD(8)                  BSD System Manager's Manual                 TFTPD(8)

NAME
     tftpd — DARPA Trivial File Transfer Protocol server

SYNOPSIS
     tftpd [-n] [-s] [directory ...]

DESCRIPTION
     Tftpd is a server which supports the DARPA Trivial File Transfer Proto&#8208;
     col.  The TFTP server operates at the port indicated in the ‘tftp’ ser&#8208;
     vice description; see services(5).  The server is normally started by
     inetd(8).

     The use of tftp(1) does not require an account or password on the remote
     system.  Due to the lack of authentication information, tftpd will allow
     only publicly readable files to be accessed.  Files may be written only
     if they already exist and are publicly writable.  Note that this extends
     the concept of “public” to include all users on all hosts that can be
     reached through the network; this may not be appropriate on all systems,
     and its implications should be considered before enabling tftp service.
     The server should have the user ID with the lowest possible privilege.

     Access to files may be controlled by invoking tftpd with a list of direc&#8208;
     tories by including pathnames as server program arguments in
     /etc/inetd.conf.  In this case access is restricted to files whose names
 Manual page tftpd(8) line 4
     tftpd — DARPA Trivial File Transfer Protocol server

SYNOPSIS
     tftpd [-n] [-s] [directory ...]

DESCRIPTION
     Tftpd is a server which supports the DARPA Trivial File Transfer Proto&#8208;
     col.  The TFTP server operates at the port indicated in the ‘tftp’ ser&#8208;
     vice description; see services(5).  The server is normally started by
     inetd(8).

     The use of tftp(1) does not require an account or password on the remote
     system.  Due to the lack of authentication information, tftpd will allow
     only publicly readable files to be accessed.  Files may be written only
     if they already exist and are publicly writable.  Note that this extends
     the concept of “public” to include all users on all hosts that can be
     reached through the network; this may not be appropriate on all systems,
     and its implications should be considered before enabling tftp service.
     The server should have the user ID with the lowest possible privilege.

     Access to files may be controlled by invoking tftpd with a list of direc&#8208;
     tories by including pathnames as server program arguments in
     /etc/inetd.conf.  In this case access is restricted to files whose names
     are prefixed by the one of the given directories. If no directories are
     supplied the default is /tftpboot.  To give out access to the whole
     filesystem, should this be desired for some reason, supply / as an argu&#8208;
     ment.

     Unfortunately, on multi-homed systems, it is impossible for tftpd to
     determine the address on which a packet was received. As a result, tftpd
     uses two different mechanisms to guess the best source address to use for
     replies. If the socket that inetd(8) passed to tftpd is bound to a par&#8208;
     ticular address, tftpd uses that address for replies. Otherwise, tftpd
     uses ``UDP connect'' to let the kernel choose the reply address based on
     the destination of the replies and the routing tables. This means that
     most setups will work transparently, while in cases where the reply
     address must be fixed, the virtual hosting feature of inetd(8) can be
     used to ensure that replies go out from the correct address.  These con&#8208;
     siderations are important, because most tftp clients will reject reply
     packets that appear to come from an unexpected address.

     The options are:

     -n      Suppresses negative acknowledgement of requests for nonexistent
             relative filenames.

     -s      All absolute filenames are treated as if they were preceded by
             the first directory argument, or /tftpboot if there is none.

SEE ALSO
     tftp(1), inetd(8)

HISTORY
     The tftpd command appeared in 4.2BSD.

Linux NetKit (0.17)              July 29, 2000             Linux NetKit (0.17)

```

---

### Post by sepo on 2012-08-23
Which system are you using? 
The man page you sent is about the Linux NetKit' tftpd (that honestly I don't know)

---

### Post by jhall1990 on 2012-08-23
What do you mean which system am I using?

---

### Post by sepo on 2012-08-23
Are you using the latest Ubuntu or an older version (or not Ubuntu at all)?

It's strange because seems that the Linux NetKit isn't in the Ubuntu repositories (you can install it by hand with some trick). If you tell me which operating system are you using it will be easier for me to understand :) (and to help you, off course)

---

### Post by nerdux on 2012-08-23
The tftp-hpa package will allow you to do that with the -c switch.

---

### Post by jhall1990 on 2012-08-23
Oh I am using Ubuntu 10.04

---

### Post by nerdux on 2012-08-23
> **jhall1990 said:**
> Oh I am using Ubuntu 10.04

So? it's available for 10.04.

---

### Post by jhall1990 on 2012-08-23
Thats what I'm trying to figure out haha.

---

### Post by nerdux on 2012-08-23
lol!

It's right there!

[http://packages.ubuntu.com/lucid/net/tftpd-hpa](http://packages.ubuntu.com/lucid/net/tftpd-hpa)

It should only be a matter of doing:

sudo apt-get remove --purge tftpd
sudo apt-get install tftpd-hpa

Good luck!

---

### Post by sepo on 2012-08-24
+1 for nerdux

---


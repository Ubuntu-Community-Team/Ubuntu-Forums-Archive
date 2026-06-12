---
title: "cifs"
date: 2010-09-22
forum: General Help
---

### Post by ub007 on 2010-09-22
I'm trying to use cifs shares on my fedora box and getting confused the more i read up in it.

as i understand:

Quote:
CIFS is a network filesystem and it uses the CIFS filesharing protocol which is an updated version of the Server Message Block (SMB) protocol.  

But i'm unclear, if i need to use cifs shares on linux box, is there a cifs server i need to install or there is no such thing as 'cifs server'and you still use 'samba server' which supports the cifs protocol anyway.

elementary question maybe, but i've been googling & got muddled up. Appreciate if someone can give some clarification

Thanks in advance
david

---

### Post by Iowan on 2010-09-22
> **ub007 said:**
> ...there is no such thing as 'cifs server'and you still use 'samba server' which supports the cifs protocol anyway. Just my opinion... There's a difference in how you mount CIFS shares compared to smb. [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To (for Ubuntu... it IS an Ubuntu forum...:)). If you install SMBFS, you get CIFS, too...

---

### Post by capscrew on 2010-09-22
> **ub007 said:**
> I'm trying to use cifs shares on my fedora box and getting confused the more i read up in it.

as i understand:

Quote:
CIFS is a network filesystem and it uses the CIFS filesharing protocol which is an updated version of the Server Message Block (SMB) protocol.

Even Microsoft gets this confused every once in a while.  SMB is an old network file sharing protocol for sure.  Microsoft has extended the protocol and sometimes refers to it as CIFS.  >  

But i'm unclear, if i need to use cifs shares on linux box, 
is there a cifs server i need to install or there is no such thing as 'cifs server'and you still use 'samba server' which supports the cifs protocol anyway.
If you want to share files using SMB/CIFS on a *nix host (e.g serve files via SMB) then you need Samba Server.  If you are only browsing shares on remote (other) hosts then all you need is the client routines.  This is the *"smbfs" *package in Ubuntu and it is already installed by default.   FYI -- Oracle Solaris calls there version "CIFS Server", but it really is Samba.  It uses the same smbd/nmbd daemons.

---


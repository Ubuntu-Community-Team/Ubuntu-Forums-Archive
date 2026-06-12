---
title: "samba &amp; windows file sharing"
date: 2006-03-05
forum: General Help
---

### Post by lordjeff on 2006-03-05
Hola gang,  I have a bit of a noob type question.
I have samba up and working, I can access it, but I need to use a username/password to do it.  
How does one go about setting up fileshares that are "public" in nature?  

Any help you could offer, would be greatly appreciated.

---

### Post by anil_robo on 2006-03-06
[quote=lordjeff]Hola gang,  I have a bit of a noob type question.
I have samba up and working, I can access it, but I need to use a username/password to do it.  
How does one go about setting up fileshares that are "public" in nature?  

Any help you could offer, would be greatly appreciated.[/quote]

Even I need to do that! :(

---

### Post by skirkpatrick on 2006-03-06
Well, you can set your "security = share" in /etc/samba/smb.conf then restart Samba.  That will allow anybody to have access to any shared directory.

---

### Post by anil_robo on 2006-03-07
[quote=skirkpatrick]Well, you can set your "security = share" in /etc/samba/smb.conf then restart Samba.  That will allow anybody to have access to any shared directory.[/quote] 
Thanks Patrick!

Initially I was trying to set "security=none" :D But soon I found that out myself after searching for two hours on google, and took 10 mins to write a howto here:

[http://www.ubuntuforums.org/showthread.php?p=799912#post799912]("http://www.ubuntuforums.org/showthread.php?p=799912#post799912")

---

### Post by spartan777 on 2006-03-07
setting security=share doesn't have any potential security problems does it? (like somebody from outside the network somehow gaining access?)

---

### Post by The Warlock on 2006-03-07
[QUOTE=spartan777]setting security=share doesn't have any potential security problems does it? (like somebody from outside the network somehow gaining access?)[/QUOTE]

Well, they'll have access to all your shared files, obviously. But if you mean "will they be able to pwn my computer", then no, I don't think so.

(disclaimer: IANAsysadmin)

---

### Post by mr.p on 2006-03-07
[QUOTE=skirkpatrick]Well, you can set your "security = share" in /etc/samba/smb.conf then restart Samba.  That will allow anybody to have access to any shared directory.[/QUOTE]

What if I want to share some dirs as "public" but others as "private"? Do you know how I can go about this?

So for example.

/var/share/ "public"
/home/nathan/ "private"
/var/priv/ "private"

---

### Post by WelterPelter on 2006-03-07
That will work. Each share is individually configurable.

---

### Post by skirkpatrick on 2006-03-08
Private as in private access?  In that case you'll need to have those shares set with a password.

As far as security goes, if you are behind a router that provides NAT, you'll be fine.

---


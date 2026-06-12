---
title: "update-inetd: help"
date: 2006-04-16
forum: General Help
---

### Post by lezz on 2006-04-16
i cant get things working with update-inetd. i have installed vsftpd but then i run:

update-inetd --add vsftpd

i get this error message:

The entry definition does not contain any whitespace characters!

what does that mean? and what does ENTRY really means in this how-to-use-syntax:

update-inetd  --add ENTRY

PS. my /etc/inetd.conf is empty. DS.

---

### Post by z_diver on 2006-04-16
[QUOTE=lezz]
update-inetd --add vsftpd[/QUOTE]

1. Just checking, you are you doing this as root, aren't you?

2.  In order to pre&#8208;vent the shell from changing your ENTRY definition you  have  to quote the ENTRY using single or double quotes.

so try:
```
[COLOR="DarkRed"]sudo update-inetd --add 'vsftpd'[/COLOR]
```

---

### Post by lezz on 2006-04-16
> **z_diver]1. Just checking, you are you doing this as root, aren't you?

2.  In order to pre&#8208 said:**
> sudo update-inetd --add 'vsftpd'[/COLOR]
```

yes i am always root. i get the same error message when running

update-inetd --add 'vsftpd'

what is supposed to happen? and how does update-inetd know the information about the entry (as the location of vsftpd and so on)?

---

### Post by z_diver on 2006-04-16
Not sure how update-inetd handles this.  Below is an example entry that I have from pure-ftpd in my /etc/inetd.conf file.  I believe the ftp tells which port to use based on what is found in /etc/services.  You can find more of how update-inetd works by reading the man pages.  You might also try the --add command using double quotes or editing the /etc/inetd.conf file by hand.
```

#<off># ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/pure-ftpd-wrapper
```

---


---
title: "What's the difference between semicolons &amp; hash characters in config files?"
date: 2011-04-22
forum: General Help
---

### Post by insanity54 on 2011-04-22
Ok guys, here's an easy one.

I'm messing with my samba config file. For line comments, some use a number sign/pound sign/hash symbol, while other lines use a semicolon:

```
############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

```

What is the difference between the two?

---

### Post by marshmallow1304 on 2011-04-22
According to 'man smb.conf':
[QUOTE="man smb.conf"]Any line beginning with a semicolon (“;”) or a hash (“#”) character is ignored, as are lines containing only whitespace.[/QUOTE]

---

### Post by JKyleOKC on 2011-04-22
The hash mark is recognized as a comment flag by almost all *nix programs; the semicolon by only a few. When in doubt, use the hash mark.

That said, the Samba configuration file uses them both to convey a slight difference in significance. The hash mark indicates a true comment, while the semicolon indicates the default value of an attribute. If you want to change to a non-default value, just change it and remove the semicolon, or alternatively leave the line alone and insert a new one following it to define the new value.

---

### Post by insanity54 on 2011-04-27
JKyleOKC and marshmallow1304, thanks for your replies!
> **JKyleOKC said:**
> The hash mark is recognized as a comment flag by almost all *nix programs; the semicolon by only a few. When in doubt, use the hash mark.

That said, the Samba configuration file uses them both to convey a slight difference in significance. The hash mark indicates a true comment, while the semicolon indicates the default value of an attribute. If you want to change to a non-default value, just change it and remove the semicolon, or alternatively leave the line alone and insert a new one following it to define the new value.

JKyleOKC, that answered my question, thank you very much!

---

### Post by 5149.5 on 2011-04-27
Last night I ran across another one. The vim config file uses double quotes for comments.

---

### Post by bodhi.zazen on 2011-04-27
> **5149.5 said:**
> Last night I ran across another one. The vim config file uses double quotes for comments.

/Off topic

<-- html !--> 
-- lua
## grub (1)
// php, javascript
/* php , javascript, css */

As as you can see, depends on the interpreter.

---


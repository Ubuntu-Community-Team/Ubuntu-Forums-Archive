---
title: "Why is autoremove wanting to remove bind?"
date: 2010-06-14
forum: General Help
---

### Post by DThurman on 2010-06-14
v10.4

I am at loss to understand why autoremove wants to
remove the following files:

bind9 bind9utils resolvconf

I cannot find the rationale why dpkg wants
to remove these files.  Is there a way to find
out?

---

### Post by zvacet on 2010-06-15
If you don't want to autoremove tell you to remove these packages (and if you don't want to remove them)


```
sudo apt-get install bind9 bind9utils resolvconf
```

---

### Post by DThurman on 2010-06-15
> **zvacet said:**
> If you don't want to autoremove tell you to remove these packages (and if you don't want to remove them)


```
sudo apt-get install bind9 bind9utils resolvconf
```

Huh?  Can you explain why autoremove wants to remove these
in the first place?  I did install these and yet later, when
I do an update or an install of another package, there is that
pesky autoremove message again!

What is it that "tells" autoremove to activate?

I hope I am making any sense....

---

### Post by doas777 on 2010-06-15
autoremove uninstalls packages referred to by another package which has since been uninstalled. 
how did you install bind? did it piggyback on another package?

---

### Post by DThurman on 2010-06-15
> **doas777 said:**
> autoremove uninstalls packages referred to by another package which has since been uninstalled. 
how did you install bind? did it piggyback on another package?

That is the mystery I am trying to discover.  For some reason
it seems that bind is being pre-empted by another package and
I have yet to figure this out.  I have completely removed the
dhcp packages thinking that this somehow interfered with bind.

I will try once again to reinstall bind and see if autoremove
yet once again wants to remove the package.

If you can think of *any* package that could interfere please
let me know?

Thanks!

---

### Post by doas777 on 2010-06-15
> **DThurman said:**
> That is the mystery I am trying to discover.  For some reason
it seems that bind is being pre-empted by another package and
I have yet to figure this out.  I have completely removed the
dhcp packages thinking that this somehow interfered with bind.

I will try once again to reinstall bind and see if autoremove
yet once again wants to remove the package.

If you can think of *any* package that could interfere please
let me know?

Thanks!
dhcp recomends bind, because people use the two together for Dynamic DNS registration. the DHCP assigns the addr, and automatically tells bind to add an address/name for that host. 

I'd follow zvacet's advice if you want to keep providing DNS but don;t need dhcp anymore. if that don't work, try backing up your zones, and uninstalling bind. then just reinstall it and restore. apt may have gotten confused. with as complex as it is, I am surprised there aren't more problems with it TBH.

---

### Post by Chame_Wizard on 2010-06-15
```
aptitude remove packagename
```:popcorn:

---

### Post by DThurman on 2010-06-15
This thing with resolvconf: it fails to install after
a removal because it says that the /etc/resolv.conf
must be a synlink.  In other words this package does
not properly create a symlink and it hangs, so it seems
this package is broken on 10.4?

I killed the install process, removed resolveconf, removed
the /etc/resolv.conf, and installed it again and the same
problem occurs again.  And autoremove comes back again wanting
to remove the same set of files as before.

This seems to be a catch-22 involving the failed installation
of resolvconf package...

---

### Post by DThurman on 2010-06-15
OK!  I found out what I had to do!

I had to purge resolvconf so as to have the
/etc/{resolvconf,resolv.conf} completely
removed, otherwise if there is any existing
/etc/resolconf structure, installing this
package will fail.  Seems that this package
does not have the smarts to deal with the
symlink creation for resolv.conf, or so it
seems.

autoremove no longer is asking to remove these
files again.  Whew!

Thanks for your help!

---

### Post by DThurman on 2010-06-15
Oops, I need to ask:

What are the default dhcp packages I need that were
freshly installed by LiveCD?  I need to get these
back in!

Thanks

---

### Post by doas777 on 2010-06-15
I've never tried DHCP in linux, but I think this should point you in the right direction:
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

---

### Post by DThurman on 2010-06-15
I should put this on a separate thread....  I guess I will
leave this message here and create a new thread on this issue
as it has nothing to do with the topic...  will do that!

Ok, I found out why I was having such a horrible time with
bind in the first place.  When I installed dhcp3 (which was
installed when installing new from LiveCD), it is interferring
with the bind9 nameserver.

Somehow, dhcp(3) is preventing bind9 nameserver from serving up
queries - it acts as if the bind server is not there at all.

When I turned off the dhcp3-server, bind started to respond
as expected.

Does anyone know how to get the dhcp & bind to cooperate?

Thanks-

---


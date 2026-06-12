---
title: "gksudo problem"
date: 2006-04-01
forum: General Help
---

### Post by fedechispa on 2006-04-01
When I try to do
```
 gksudo gedit
```
immediately I get
```
(gedit:10048): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```
But the gedit window appears after ~30-40 seconds.

Do you have any idea about this? That's the same for any other gnome application.

I use Breezy with security updates.

Federico

---

### Post by dcstar on 2006-04-01
[QUOTE=fedechispa]When I try to do
```
 gksudo gedit
```
immediately I get
```
(gedit:10048): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```
But the gedit window appears after ~30-40 seconds.

Do you have any idea about this? That's the same for any other gnome application.

I use Breezy with security updates.

Federico[/QUOTE]
That message also appears on my system without any adverse effects, so don't worry about it.

As far as the delay goes, that is a separate issue and is possibly due to IPv6 lookups, have you disabled IPv6 on your system? (if not, do a forum search for detailed instructions on how to do it).

---

### Post by Ramses de Norre on 2006-04-01
IPv6 causing gedit to start slow? Why does gedit use the internet?

---


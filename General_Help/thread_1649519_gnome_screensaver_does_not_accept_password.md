---
title: "gnome screensaver does not accept password"
date: 2010-12-20
forum: General Help
---

### Post by mamnmamn on 2010-12-20
Hi,

I have an Ubuntu 10.10 box authenticating Users against an LDAP server. User authentication works fine - ssh, console or Gnome.

The only place it has an issue is when the gnome-screensaver is activated and locks the computer. When I try to enter the correct password at this point I get these error in the logs;

Dec 20 14:42:23 box-ubuntu unix_chkpwd[12240]: password check failed for user (myname)
Dec 20 14:42:23 box-ubuntu gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=10038 euid=10038 tty=:0.0 r
user= rhost=  user=myname
Dec 20 14:42:23 box-ubuntu gnome-screensaver-dialog: pam_ldap(gnome-screensaver:auth): Authentication failure; user=myname
Dec 20 14:42:26 box-ubuntu unix_chkpwd[12242]: check pass; user unknown

/etc/pam.d/gnome-screensaver references common-auth with @include common-auth

If I run "getent shadow" the ldap users are listed. 

I have stopped screensaver from locking the screen but would like to resolve this.

uname: Linux box-ubuntu 2.6.35-24-generic-pae #42-Ubuntu SMP Thu Dec 2 03:21:31 UTC 2010 i686 GNU/Linux
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Thanks for any help.

---

### Post by marrusl on 2011-02-22
Hello mamnmamn...

Did you get anywhere with this?

---

### Post by mamnmamn on 2012-08-09
Hi marrusl,

Sorry I never answered your question. I don't come on this very often and didn't get an email about your message.

TBH, really can not remember now what we did, and now we don't have any PCs on maverick.

Sorry,

mamnmamn

---


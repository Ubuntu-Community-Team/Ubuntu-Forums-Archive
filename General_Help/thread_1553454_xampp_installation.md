---
title: "xampp installation"
date: 2010-08-15
forum: General Help
---

### Post by criptonite on 2010-08-15
Hi, I've installed xampp 1.73 on Ubuntu 10.04

When I start xampp everything reports back fine.  However, when I try to view xampp with my browser (typing [https://localhost](https://localhost)) I can't connect.  I've tried Firefox and Chrome.

Any ideas on what I'm missing.

Thanks

---

### Post by mikewhatever on 2010-08-15
You probably need to add the port xampp is listening on.
[http://localhost:123](http://localhost:123)
Is anything wrong with the installation?

---

### Post by lovinglinux on 2010-08-15
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

---

### Post by criptonite on 2010-08-15
When I start xampp with /opt/lampp/lampp start

I receive the following

Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

Which suggests the installation is ok.  If I try localhost:123 Firefox says

This address uses a network port which is normally used for purposes other than Web browsing. Firefox has cancelled the request for your protection.

It's confusing!

---

### Post by lovinglinux on 2010-08-15
> **criptonite said:**
> When I start xampp with /opt/lampp/lampp start

I receive the following

Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

Which suggests the installation is ok.  If I try localhost:123 Firefox says

This address uses a network port which is normally used for purposes other than Web browsing. Firefox has cancelled the request for your protection.

It's confusing!

htpp://localhost:123 was just an example, I don't think xampp listens to that port by default. You could try [http://localhost:80](http://localhost:80) or [http://localhost:8080](http://localhost:8080), which should be the default or configure it to use another port. Any port between 49152 and 65535 should do it.

---

### Post by criptonite on 2010-08-17
I now have the xampp control panel working and I notice that Apache isn't working (Pic attached).

Could this mean that the xampp installation wasn't successful?  Should I uninstall and re-install?

---

### Post by criptonite on 2010-08-17
Sorry, forgot the xampp control panel pic

---

### Post by Jett Deion on 2010-08-17
If you have access to php.ini

set the
magic_quotes_gpc directive to On
magic_quotes_runtime=on

If you don't have access to php.ini

ini_set('magic_quotes_gpc', 1); in your code

---

### Post by kingheart on 2010-08-17
> **criptonite said:**
> I now have the xampp control panel working and I notice that Apache isn't working (Pic attached).

Could this mean that the xampp installation wasn't successful?  Should I uninstall and re-install?

Did you started apache from the Panel ? I guess you didn't.

---

### Post by criptonite on 2010-08-17
Hi, I've tried starting apache via the terminal with /opt/lampp/ lampp start and I've tried starting apache via the control panel.  When I click on execute for Apache, nothing happens.

---


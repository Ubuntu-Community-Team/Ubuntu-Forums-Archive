---
title: "apt is trying to install something but fails"
date: 2012-10-01
forum: General Help
---

### Post by WinterMadness on 2012-10-01
Hi, whenever I try to install something I get the following error. Im not entirely sure what the deal is with it. I really dont care if "qmail" gets installed as I dont even know what it is. The software that I attempt to install always gets installed with no issues, it just seems that apt wants to do something that I dont really care about. Any idea how to make it go away?

```
The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
Setting up libsigc++-2.0-0c2a (2.2.10-0ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          
ldconfig deferred processing now taking place
Errors were encountered while processing:
 qmail
 qmail-run

```

---

### Post by sandyd on 2012-10-01
Post output of
```

cat /etc/hostname

```

If it returns something empty, or a bad hostname, do this

```

sudo mv /etc/hostname /etc/hostname.bak
sudo nano /etc/hostname

```

Put a hostname in, like 'desktop' or 'laptop', but without quotes. Mine is 'sandyd-laptop', but I doubt you would want to use it cause then, I could claim that the pc is mine :D . The hostname should be a one-liner.

```

sudo nano /etc/hosts

```

add a line containing '127.0.0.1' and your hostname at the bottom of the file. The line should look something like this (this is mine)
```

127.0.1.1       sandyd-laptop

```

Reboot

---


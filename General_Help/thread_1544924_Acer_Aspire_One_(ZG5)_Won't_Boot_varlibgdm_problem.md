---
title: "Acer Aspire One (ZG5) Won't Boot: /var/lib/gdm problem"
date: 2010-08-03
forum: General Help
---

### Post by Josh2010 on 2010-08-03
I'm helping a friend with a Acer netbook that came with Ubuntu on it.  The computer starts to load and then shows this message in Italian:

> a directory di autorizzazione del server (daemon/ServAuthDir) è impostata a /var/lib/gdm che non esiste. Correggere la configurazione di GDM e riavviare GDM.

Translation:

> permission to directory server (daemon / ServAuthDir) is set to / var / lib / gdm does not exist. Please correct GDM configuration and restart GDM.

There is no /lib directory in /var.

```
~$ ls var
lock  log  run
```

Any ideas?

---

### Post by anglican on 2010-08-03
> **Josh2010 said:**
> I'm helping a friend with a Acer netbook that came with Ubuntu on it.  The computer starts to load and then shows this message in Italian:



Translation:



There is no /lib directory in /var.

```
~$ ls var
lock  log  run
```Any ideas? Does:
```
sudo dpkg-reconfigure gdm

``` help?

H

---

### Post by Josh2010 on 2010-08-04
> **anglican said:**
> Does:
```
sudo dpkg-reconfigure gdm

``` help?

Thanks for the reply. It says:

```
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
```

It looks like there is nothing in /var:

```
~$ ls var
lock  log  run
```

---

### Post by anglican on 2010-08-04
> **Josh2010 said:**
> Thanks for the reply. It says:

```
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
```It looks like there is nothing in /var:

```
~$ ls var
lock  log  run
```
Looks to me like that AA1 installation has been thoroughly borked. I'd consider re-installing as the best way to avoid wasting a lot of time trying to fix something that's very broken. You don't have to re-format the HD when you install so any application data (documents etc...) should survive - though I'd make backup copies of anything irreplaceable first. You'll need either an external CD/DVD or a USB stick to reinstall from - should only take an hour or so.

H

---

### Post by Josh2010 on 2010-08-04
> **anglican said:**
> Looks to me like that AA1 installation has been thoroughly borked. I'd consider re-installing as the best way to avoid wasting a lot of time trying to fix something that's very broken.

Thanks... I'll try that tomorrow.

---


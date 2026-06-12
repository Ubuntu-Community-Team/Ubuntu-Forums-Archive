---
title: "installation of untrusted packages"
date: 2012-01-05
forum: General Help
---

### Post by Paventhan on 2012-01-05
paventh@paventh-Aspire-4736:~$ sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.k0QOc9SZQS --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-key --keyserver keyserver.ubuntu.com 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


How to deal with this??????????????????:(:(:(

---

### Post by imachavel on 2012-01-05
this is what mine says:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg 
gpg: Go ahead and type your message ...

what are you trying to perform? go ahead and try out sudo apt-get install update and sudo apt-get upgrade.

well, upgrade if you want to upgrade. What else can I say I'm on the other side of the world trying to help your problem through the internet. Oh well

---

### Post by oldos2er on 2012-01-05
> **Paventhan said:**
> paventh@paventh-Aspire-4736:~$ sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.k0QOc9SZQS --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-key --keyserver keyserver.ubuntu.com 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


How to deal with this?

Try ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

---

### Post by Paventhan on 2012-01-07
i want to allow update manager to install (update) untrusted packages

---

### Post by dino99 on 2012-01-07
the good command is:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5

as done previously, so you know what to do, but remind than exotic archive is at your own risk and needs you to understand what you are doing, then fix yourself if needed.

---

### Post by Paventhan on 2012-01-08
I have solved the problem by typing the following commands::p:p:p

sudo apt-get clean
sudo cd /var/lib/apt
cd /var/lib/apt
ls
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

---

### Post by BlueSunshine on 2012-01-14
> **Paventhan said:**
> I have solved the problem by typing the following commands::p:p:p

sudo apt-get clean
sudo cd /var/lib/apt
cd /var/lib/apt
ls
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
This seemed to work for me. Thank you! :D

---

### Post by Guilden_NL on 2012-01-20
Many thanks Paventhan!
I have been ](*,) since yesterday trying to clear up a problem with the keys.  My problem was with BAD KEY, not missing keys, so nothing I could find or think of worked.

But your approach made sense, I tried it and it worked! =D>

---


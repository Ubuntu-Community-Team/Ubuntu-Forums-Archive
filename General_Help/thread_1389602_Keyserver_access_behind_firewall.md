---
title: "Keyserver access behind firewall?"
date: 2010-01-24
forum: General Help
---

### Post by mmebane on 2010-01-24
I'm trying to install Wine, and it's failing to get the gpg key.

```
mmebane@mmebane-vbox:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
mmebane@mmebane-vbox:~$ 

```

After some poking around, I think this is because of the restrictive firewall I'm behind here at my school.  Is there any manual way to get the key?

---

### Post by duanedesign on 2010-01-24
Try using 
```
--keyserver-options http-proxy=some-proxy
```
I have never used this personally so i cant provide you with any more specific information.

You can also look at

```
man gpg
```

---


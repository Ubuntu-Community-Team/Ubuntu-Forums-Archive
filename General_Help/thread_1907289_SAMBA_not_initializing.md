---
title: "SAMBA not initializing"
date: 2012-01-11
forum: General Help
---

### Post by metalcryptor on 2012-01-11
Hi All.. I'm a new user to Ubuntu so please bear with me .. i've searched all over the forums for this but still no luck :( I'm trying to get SAMBA to work so to enable file sharing between my Windows and Linux installs. The problem is as follows: 
When i select SAMBA from UBUNTU 11.10 installed applications, it asks for a Password. After typing the correct password, nothing happens. i repeat, NOTHING. I've done the following to resolve: 

1. Removed SAMBA using sudo apt-get remove SAMBA
2. Reinstalled SAMBA using sudo apt-get install SAMBA (and SAMBAsystem-config-samba)
3. Upgraded SAMBA using sudo apt-get upgrade SAMBA
4. Restarted the PC
:razz:
All is successful, but same problem every time i try run SAMBA. Am i doing something dummy PLS HELP!

---

### Post by metalcryptor on 2012-01-11
Hi All.. I'm a new user to Ubuntu so please bear with me .. i've searched all over the forums for this but still no luck :( I'm trying to get SAMBA to work so to enable file sharing between my Windows and Linux installs. The problem is as follows: 
When i select SAMBA from UBUNTU 11.10 installed applications, it asks for a Password. After typing the correct password, nothing happens. i repeat, NOTHING. I've done the following to resolve: 

1. Removed SAMBA using sudo apt-get remove SAMBA
2. Reinstalled SAMBA using sudo apt-get install SAMBA (and SAMBAsystem-config-samba)
3. Upgraded SAMBA using sudo apt-get upgrade SAMBA
4. Restarted the PC
:razz:
All is successful, but same problem every time i try run SAMBA. Am i doing something dummy PLS HELP!

---

### Post by mörgæs on 2012-01-11
Please don't double-post.
Merged.

---

### Post by lukeiamyourfather on 2012-01-11
Samba isn't an application that launches. Once installed it runs in the background as a daemon and is configured through text files.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by metalcryptor on 2012-01-11
ok thanks lukeiamyourfather.. i was obviously confused but now enlightened .. I will follow the links you suggest

---


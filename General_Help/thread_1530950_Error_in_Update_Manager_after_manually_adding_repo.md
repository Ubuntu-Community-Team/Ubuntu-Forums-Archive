---
title: "Error in Update Manager after manually adding repository"
date: 2010-07-14
forum: General Help
---

### Post by Svens on 2010-07-14
Hi everybody! I hope you have a nice day and someone will be able to help me here.
Some while ago I decided to add Firefox repository directly through terminal. (Idea born when I saw in one old page (yes, never look for info in old pages :D ) "tutorial" how to do it.) The whole idea was simple: just add one line in terminal.
The line was like this:
sudo add-apt-repository ppa:mozillateam/firefox-stable
But since that, when I try to update through update manager I get errors:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D45DF2E8FC91AE7E
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

Updates are coming (I hope that this problem doesn't deny me any updates), but it is still annoing. Could someone help me on tis?
I add a picture so you can see how it looks like.
[[IMG]http://a.imageshack.us/img153/2374/screenshot1ie.png[/IMG]](http://img153.imageshack.us/i/screenshot1ie.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
Thank you!

---

### Post by Svens on 2010-07-14
Anybody? :-k

---

### Post by Linye on 2010-07-14
Try this.

[http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html](http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html)

---

### Post by Svens on 2010-07-14
Thankyou! Now I have four errors less!
But I still have these one, which the script couldn't fix:
> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5


```
svens@svens-hp:~$ sudo ./launchpad-update.sh 
sudo: ./launchpad-update.sh: command not found
svens@svens-hp:~$ sudo sh ./launchpad-update.sh 
Grabbing key CE49EC21 for archive firefox-stable by ~mozillateam
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: public key "Launchpad PPA for Mozilla Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Grabbing key 0624A220 for archive ppa by ~tualatrix
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0624A220
gpg: requesting key 0624A220 from hkp server keyserver.ubuntu.com
gpg: key 0624A220: public key "Launchpad PPA for TualatriX" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Grabbing key F9CB8DB0 for archive ppa by ~ubuntu-wine
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com F9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Grabbing key FC91AE7E for archive ppa by ~gezakovacs
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com FC91AE7E
gpg: requesting key FC91AE7E from hkp server keyserver.ubuntu.com
gpg: key FC91AE7E: public key "Launchpad PPA for Geza Kovacs" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
DONE
svens@svens-hp:~$ sudo sh ./launchpad-update.sh 
Already have key CE49EC21 for archive firefox-stable by ~mozillateam
Already have key 0624A220 for archive ppa by ~tualatrix
Already have key F9CB8DB0 for archive ppa by ~ubuntu-wine
Already have key FC91AE7E for archive ppa by ~gezakovacs
DONE
svens@svens-hp:~$ 

```

What could I do?

---

### Post by Svens on 2010-07-15
Anyone? :)

---

### Post by plucky on 2010-07-15
From a terminal ```
gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```

one line at a time and then see what happens.

Good Luck

---

### Post by Svens on 2010-07-16
It worked perfectly! Thank you very much!
And could someone explain me how could it happen by just adding repository?

---


---
title: "How can i Solve this"
date: 2012-10-11
forum: General Help
---

### Post by Mohan1289 on 2012-10-11
When i ran the command **"sudo apt-get-update"** 

it is showing the following warning.. what does that mean?? how can i solve that error??


W: GPG error: [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26

---

### Post by Bucky Ball on 2012-10-11
Please help yourself and use descriptive thread titles. ;)

Open Update Manager and click Settings at bottom left. Click the Other Software tab. Look for an entry containing:

 [http://www.duinsoft.nl](http://www.duinsoft.nl)

Untick. Close. Try again.

---

### Post by drpjkurian on 2012-10-11
Hi enter this in terminal
```
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com E18CE6625CB26B26
```

Then update the system.

---

### Post by josephmills on 2012-10-11
duinsoft.nl is repo for java ? 

looks like the key is

```
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
```

source: 
[http://www.duinsoft.nl/packages.php](http://www.duinsoft.nl/packages.php)

---

### Post by Mohan1289 on 2012-10-11
> **drpjkurian said:**
> Hi enter this in terminal
```
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com E18CE6625CB26B26
```Then update the system.

This is the output i got when i executed


```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.BiYvKHEzRZ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-key --keyserver keyserver.ubuntu.com E18CE6625CB26B26
gpg: requesting key 5CB26B26 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

---

### Post by Mohan1289 on 2012-10-11
> **josephmills said:**
> duinsoft.nl is repo for java ? 

looks like the key is

```
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
```source: 
[http://www.duinsoft.nl/packages.php](http://www.duinsoft.nl/packages.php)

when i did as you told ```


Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.GJa10MAv5F --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keys.gnupg.net --recv-keys 5CB26B26
gpg: requesting key 5CB26B26 from hkp server keys.gnupg.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

It's showing this why??

---

### Post by Bucky Ball on 2012-10-11
I still vote for disabling the repo for now. See post #2. Could be a problem their end. Wonder if anyone else is having problems with the same key?

---

### Post by oldos2er on 2012-10-11
I just tried it and it worked fine for me.

---

### Post by Bucky Ball on 2012-10-11
> **oldos2er said:**
> I just tried it and it worked fine for me.

There you go. Rules that out my idea the repo might be having problem and gives a clearer picture where to dig. Thanks oldos2er. ;)

---

### Post by Mohan1289 on 2012-10-12
> **Bucky Ball said:**
> There you go. Rules that out my idea the repo might be having problem and gives a clearer picture where to dig. Thanks oldos2er. ;)

Thank you i will try

---

### Post by Mohan1289 on 2012-10-12
> **Bucky Ball said:**
> There you go. Rules that out my idea the repo might be having problem and gives a clearer picture where to dig. Thanks oldos2er. ;)


But What's the error??? why i have to disable it??

---

### Post by Mr Nemo on 2012-10-12
The repo just might not exist anymore, or there's a problem on the devs end. It probably has nothing to do with you. This happens to me every once in a while.

---

### Post by Mohan1289 on 2012-10-13
> **Mr Nemo said:**
> The repo just might not exist anymore, or there's a problem on the devs end. It probably has nothing to do with you. This happens to me every once in a while.

Ohh Okay Thank you

---


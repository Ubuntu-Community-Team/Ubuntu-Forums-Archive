---
title: "Updating Error"
date: 2011-01-18
forum: General Help
---

### Post by pramod826 on 2011-01-18
I am new to ubuntu10.10 and while updating synaotic manager i get following error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

i am tired of this error ,plz help......

---

### Post by adeee on 2011-01-18
type in terminal.(Applications->accessories->Terminal)

sudo apt-get install -f

---

### Post by plucky on 2011-01-18
> **pramod826 said:**
> I am new to ubuntu10.10 and while updating synaotic manager i get following error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

i am tired of this error ,plz help......

Open a terminal and

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE
```

Then do the same for each key given in the error messages.

How did you add the PPA's?

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE

You are mixing Maverick and Karmic PPA's,which is not recommended.

Go [Here](https://help.launchpad.net/Packaging/PPA/InstallingSoftware) and learn how to install a PPA correctly so that you don't get the warnings when you add a PPA as a repository.

Good Luck

---

### Post by pramod826 on 2011-01-18
> **plucky said:**
> Open a terminal and

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE
```

Then do the same for each key given in the error messages.

How did you add the PPA's?



You are mixing Maverick and Karmic PPA's,which is not recommended.

Go [Here](https://help.launchpad.net/Packaging/PPA/InstallingSoftware) and learn how to install a PPA correctly so that you don't get the warnings when you add a PPA as a repository.

Good Luck
Thanx for your responce but i hav done all above and agian i did but i got following result:

pramod@pramod-HP-Pavilion-dv6-Notebook-PC:~$ sudo add-apt-repository ppa:gwibber-daily/ppaError reading 
[https://launchpad.net/api/1.0/~gwibber-daily/+archive/ppa:](https://launchpad.net/api/1.0/~gwibber-daily/+archive/ppa:) <urlopen error [Errno 110] Connection timed out>

pramod@pramod-HP-Pavilion-dv6-Notebook-PC:~$ sudo gedit /etc/apt/sources.listpramod@pramod-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 72D340A3gpg: requesting key 72D340A3 from hkp server keyserver.ubuntu.com?: keyserver.ubuntu.com: Connection timed outgpgkeys: HTTP fetch error 7: couldn't connect: Connection timed outgpg: no valid OpenPGP data found.gpg: Total number processed: 0

---

### Post by Bucky Ball on 2011-01-18
Welcome!

Put it in exactly as Plucky described, starting with their first example:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE
```... then:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D0AFF96872D340A3
```... then:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
```Where did this key come from:

72D340A3?

Please copy your terminal output and paste it between code tags (found  in 'New Reply' or 'Go Advanced'). It is very confusing trying to read  what you have posted. ;)

---

### Post by pramod826 on 2011-01-18
Terminal:code> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE

output:
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

next..
code>  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D0AFF96872D340A3

output:
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys D0AFF96872D340A3
gpg: requesting key 72D340A3 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


and same as above for the other key
....

i was trying to install ppa properly as suggested by pluky from :[https://launchpad.net/~gwibber-daily/+archive/ppa](https://launchpad.net/~gwibber-daily/+archive/ppa)
and key "72D340A3" was used as instructed in the website.....

---

### Post by Bucky Ball on 2011-01-18
How long did these outputs take? You have a solid internet connection? Wired or wireless?

---

### Post by pramod826 on 2011-01-18
wired lan connection and it took nearly 1 min to show the entire result

---

### Post by Bucky Ball on 2011-01-18
Could you go here:

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

... and run a speed test. How long does it take and what speed did you get up and down?

---

### Post by pramod826 on 2011-01-19
with locatio:SEATTLA ,WA 
DOWNLOAD:1.72Mbps
UPLOAD:0.41Mbps

---


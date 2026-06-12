---
title: "ell my why it is not working installation instructions TOR"
date: 2010-04-30
forum: General Help
---

### Post by Ode2 on 2010-04-30
add in  the sources of application "deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org)  lucid main" issue after updating was not possible to obtain  [http://deb.torproject.org/torproject.org/dists/lucid/main/binary](http://deb.torproject.org/torproject.org/dists/lucid/main/binary) -i386/Packages.gz 404 Not Found [IP: 88.198.151.34  80] 

Why? What is my mistake?

---

### Post by 2hot6ft2 on 2010-04-30
There is no lucid in the dists folder there.
[http://deb.torproject.org/torproject.org/dists/](http://deb.torproject.org/torproject.org/dists/)

So you will have to wait for them to add it.
They don't even have a 	experimental-lucid yet
And welcome to the forum.

---

### Post by Ode2 on 2010-04-30
Thank  you. At the regional forum could not find an  answer. I would be enlightened here :)

---

### Post by 2hot6ft2 on 2010-04-30
You're welcome. I looked but didn't find any mention of Lucid on their site. Maybe they wont take too long to add it.

---

### Post by Ode2 on 2010-04-30
Manual  installation is taken from the internet. Wait,  I think a couple of days will create a working repository

---

### Post by pushpsmarty on 2010-05-27
I have change my /etc/apt/sources.list
where i have pasted the link
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main
after this i have given follwing commands for updating keys-
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

but these are not working and giving error-
in case of first error was

gpg: failed to create temporary file `/home/pushpsmarty/.gnupg/.#lk0x9e873d8.Revolution.1807': Permission denied
gpg: keyblock resource `/home/pushpsmarty/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/pushpsmarty/.gnupg/.#lk0x9e879b8.Revolution.1807': Permission denied
gpg: keyblock resource `/home/pushpsmarty/.gnupg/pubring.gpg': general error
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

In case of secod-

gpg: failed to create temporary file `/home/pushpsmarty/.gnupg/.#lk0x9112190.Revolution.1809': Permission denied
gpg: keyblock resource `/home/pushpsmarty/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/pushpsmarty/.gnupg/.#lk0x9112928.Revolution.1809': Permission denied
gpg: keyblock resource `/home/pushpsmarty/.gnupg/pubring.gpg': general error
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

After it i think that it is prompting for sudo so i do so with sudo but still giving following errors-

gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'keys.gnupg.net'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

&

gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.


So please if u have some solution of this problem then please help me.

Pushpi

---


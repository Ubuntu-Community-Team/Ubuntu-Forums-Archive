---
title: "lib32jack0 error after &quot;apt-get dist-upgrade&quot;"
date: 2011-10-02
forum: General Help
---

### Post by M@s on 2011-10-02
Hey!

I was going to install [LADISH]("http://ladish.org/wiki/installing_on_ubuntu") according to their tutorial, but after I ran the **apt-get dist-upgrade** command something went wrong and i can no longer install packages. Now when I start the Software Center, I'm met by a dialog saying that the package catalog must be repaired. Running the repair process fails with this output: ```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 184116 files and directories currently installed.)

Unpacking lib32jack0 (from .../lib32jack0_6%3a1.9.6~dfsg.1-3ubuntu2+fixes1~natty2_amd64.deb) ...

dpkg: error processing /var/cache/apt/archives/lib32jack0_6%3a1.9.6~dfsg.1-3ubuntu2+fixes1~natty2_amd64.deb (--unpack):

 trying to overwrite '/usr/lib32/libjack.so', which is also in package ia32-libs 20090808ubuntu13

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 /var/cache/apt/archives/lib32jack0_6%3a1.9.6~dfsg.1-3ubuntu2+fixes1~natty2_amd64.deb

dpkg: dependency problems prevent configuration of libjack0:

 libjack0 depends on lib32jack0 (= 6:1.9.6~dfsg.1-3ubuntu2+fixes1~natty2); however:

  Package lib32jack0 is not installed.

dpkg: error processing libjack0 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of libjack-jackd2-0:

 libjack-jackd2-0 depends on libjack0; however:

  Package libjack0 is not configured yet.

dpkg: error processing libjack-jackd2-0 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of qjackctl:

 qjackctl depends on libjack0; however:

  Package libjack0 is not configured yet.

dpkg: error processing qjackctl (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of patchage:

 patchage depends on libjack0; however:

  Package libjack0 is not configured yet.

dpkg: error processing patchage (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of jackd:

 jackd depends on libjack0 (= 6:1.9.6~dfsg.1-3ubuntu2+fixes1~natty2); however:

  Package libjack0 is not configured yet.

dpkg: error processing jackd (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of libjack-dev:

 libjack-dev depends on libjack0 (= 6:1.9.6~dfsg.1-3ubuntu2+fixes1~natty2); however:

  Package libjack0 is not configured yet.

dpkg: error processing libjack-dev (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of jackd1:

 jackd1 depends on jackd; however:

  Package jackd is not configured yet.

dpkg: error processing jackd1 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of ardour:

 ardour depends on libjack0; however:

  Package libjack0 is not configured yet.

 ardour depends on jackd; however:

  Package jackd is not configured yet.

dpkg: error processing ardour (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of jackd-firewire:

 jackd-firewire depends on jackd (= 6:1.9.6~dfsg.1-3ubuntu2+fixes1~natty2); however:

  Package jackd is not configured yet.

dpkg: error processing jackd-firewire (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of jackd1-firewire:

 jackd1-firewire depends on jackd-firewire; however:

  Package jackd-firewire is not configured yet.

dpkg: error processing jackd1-firewire (--configure):

 dependency problems - leaving unconfigured
```

How can I fix this? I'm running 11.04 64-bit.

---

### Post by M@s on 2011-10-03
Fixed by updating with the kxstudio packages:

```
sudo add-apt-repository ppa:kxstudio-team/ppa
sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade
```

---


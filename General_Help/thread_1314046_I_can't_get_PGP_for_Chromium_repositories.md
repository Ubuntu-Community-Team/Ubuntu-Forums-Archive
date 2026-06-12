---
title: "I can't get PGP for Chromium repositories"
date: 2009-11-04
forum: General Help
---

### Post by lordgreg on 2009-11-04
Hi,

i've been strugling to get PGP key for my chromium browser. I followed the tutorial listed [here]("http://ulyssesonline.com/2009/11/02/install-google-chrome-on-ubuntu-9-10/comment-page-1/#comment-241119"). 

so here's what i do:

```
gregor@warlock:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
```

and the result:

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpgkeys: key FBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```


please help me out ://

---

### Post by sisco311 on 2009-11-04
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4e5e17b5
```

---

### Post by lordgreg on 2009-11-05
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4e5e17b5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpgkeys: key 4E5E17B5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

:(

---

### Post by lethalfang on 2009-11-05
If you add the line: 
ppa:chromium-daily 
to your software source, I think the key will be automatically added.

---

### Post by garvinrick4 on 2009-11-05
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5


This is what I used.

---

### Post by lordgreg on 2009-11-05
```
gregor@warlock:~$ sudo add-apt-repository ppa:chromium-daily/ppa
[sudo] password for gregor: 
<urlopen error [Errno 110] Connection timed out>
```

I remember I had this issue before. What should I change to bypass this error? I'm behind proxy and everything works as charm (updating and such). I googled a bit but found no good solutions to this problem.

---

### Post by sisco311 on 2009-11-05
open a text file:
```
gedit ch.key
```

copy/paste the [public key]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5A9BF3BB4E5E17B5") in the file:
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESaSPtAEEAK1nJtoDZ0ewpOOf0ET6Vp28LqO9mB4ubWjzXyRSbiha5pCvnnSIU1K+7Gzb
t3r0iUV9eKLUmf8pqfF/9kwsoqFqFSCjp+XjUzXsEChcGBWvyfGdTX8ClFfwNxSVLvGSqmdX
gZhs0F8tQB0lPWHGy3VvEt7wG/VHqpcOYpdNYRqxABEBAAG0IExhdW5jaHBhZCBQUEEgZm9y
IGNocm9taXVtLWRhaWx5iEYEEBECAAYFAknOwV0ACgkQ9rPTxuzZSv0f2QCeLjemEkq5tYjI
xtFpw3F11szeakYAoKsBZcl3Az08cYEd9UNZjQE1j4YtiEYEEBECAAYFAknS5Z8ACgkQrZOR
ep7Yx+qZ8wCfZYBABDkYO0Ulrivpxn6hARmgLxEAn0SeWaGjVQ4UE3zpNESguf+t9K1xiLYE
EwECACAFAkmkj7QCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRBam/O7Tl4XtV/2BACs
/RTpEWB/NUlluJmp1e6iFoyyfbT+HOD3hg35aQMzbdcmijsAiY9MvIfZ0YKWyqNUdGpDj5n0
bUNO0IcvKBBkOn5o4CiBsMp4DJHdrgJU4S00nAJK00E8I/yAv+x4C9uOacW3yrzSHs7Hv/vG
6Z1Jh+1JrabK13hdhwOL8+aY6Q==
=9P6G
-----END PGP PUBLIC KEY BLOCK-----
```
save the file and exit.

add the key:
```
sudo apt-key add ch.key
```

remove the file.

---

### Post by lordgreg on 2009-11-05
Finally!

No wonder it didn't worked. since i'm behind a proxy, there's no way i could access something that goes through port 11371 o_O.

Thank you sisco and others who helped!

---


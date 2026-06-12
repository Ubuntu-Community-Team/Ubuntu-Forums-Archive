---
title: "Ubuntu keyserver"
date: 2010-05-11
forum: General Help
---

### Post by oshirowanen on 2010-05-11
Dear Community,

Our firewall does not allow access to port 11371 which it seems is the port used by the ubuntu keyserver.

Is it possible to get a key/signature from somewhere else?  If not, is it possible to redirect port 22 to access 11371 via sudo apt-key?

---

### Post by mike555 on 2010-05-11
You should be able to copy the file to a text file and direct ubuntu to it......

---

### Post by oshirowanen on 2010-05-11
I need to get the text from the keyserver, how do I get it?

---

### Post by gmargo on 2010-05-11
This link has a suggestion on how to get around it, if you have access to another machine without the restriction (like your home machine.) 
[http://cprov.blogspot.com/2009/06/your-firewall-does-not-like.html](http://cprov.blogspot.com/2009/06/your-firewall-does-not-like.html)

If you only need a couple, post the info here and we'll look them up for you.

---

### Post by oshirowanen on 2010-05-12
Yes, I think I only need about 3 keys.  I will post the info in a moment.

edit

The first key/sig I need is for chromium beta:
[https://launchpad.net/~chromium-daily/+archive/beta]("https://launchpad.net/%7Echromium-daily/+archive/beta")

The second key/sig I need is for dropbox:
[https://launchpad.net/~nautilus-dropbox/+archive/ppa]("https://launchpad.net/%7Enautilus-dropbox/+archive/ppa")

Finally, the key/sig for flash64:
[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

I appreciate all the help.

Thanks

---

### Post by gmargo on 2010-05-12
> 
The first key/sig I need is for chromium beta:
[https://launchpad.net/~chromium-daily/+archive/beta]("https://launchpad.net/%7Echromium-daily/+archive/beta")
```

$ gpg --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: key 4E5E17B5: public key "Launchpad PPA for chromium-daily" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

$ gpg -a --export 4E5E17B5
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mI0ESaSPtAEEAK1nJtoDZ0ewpOOf0ET6Vp28LqO9mB4ubWjzXyRSbiha5pCvnnSI
U1K+7Gzbt3r0iUV9eKLUmf8pqfF/9kwsoqFqFSCjp+XjUzXsEChcGBWvyfGdTX8C
lFfwNxSVLvGSqmdXgZhs0F8tQB0lPWHGy3VvEt7wG/VHqpcOYpdNYRqxABEBAAG0
IExhdW5jaHBhZCBQUEEgZm9yIGNocm9taXVtLWRhaWx5iEYEEBECAAYFAknOwV0A
CgkQ9rPTxuzZSv0f2QCeLjemEkq5tYjIxtFpw3F11szeakYAoKsBZcl3Az08cYEd
9UNZjQE1j4YtiEYEEBECAAYFAknS5Z8ACgkQrZORep7Yx+qZ8wCfZYBABDkYO0Ul
rivpxn6hARmgLxEAn0SeWaGjVQ4UE3zpNESguf+t9K1xiLYEEwECACAFAkmkj7QC
GwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRBam/O7Tl4XtV/2BACs/RTpEWB/
NUlluJmp1e6iFoyyfbT+HOD3hg35aQMzbdcmijsAiY9MvIfZ0YKWyqNUdGpDj5n0
bUNO0IcvKBBkOn5o4CiBsMp4DJHdrgJU4S00nAJK00E8I/yAv+x4C9uOacW3yrzS
Hs7Hv/vG6Z1Jh+1JrabK13hdhwOL8+aY6Q==
=9P6G
-----END PGP PUBLIC KEY BLOCK-----

```> 
The second key/sig I need is for dropbox:
[https://launchpad.net/~nautilus-dropbox/+archive/ppa]("https://launchpad.net/%7Enautilus-dropbox/+archive/ppa")
```

$ gpg --keyserver keyserver.ubuntu.com --recv-keys 30A514BE
gpg: requesting key 30A514BE from hkp server keyserver.ubuntu.com
gpg: key 30A514BE: public key "Launchpad PPA for nautilus-dropbox" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

$ gpg -a --export 30A514BE
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mI0ESYBmLQEEAOgskT7y2at901ptplylkKVFDWjDQuZTChUv1vlvY8uXbrj8stjL
V92iJraih01uxhvlCvbG/2xaswuNYdx1RjIjRdVk+KX4tBgWTBeQLgbbe2dHJkbi
pjeSjnbpzj6pVhjRmGNZAzVeMVxQcNSSy5U462BSnbfrACOLjfNuVA93ABEBAAG0
IkxhdW5jaHBhZCBQUEEgZm9yIG5hdXRpbHVzLWRyb3Bib3iItgQTAQIAIAUCSYBm
LQIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEMv/6VQwpRS+7c0D/0ihJEJ/
wsGB/Ns0vykvBX4tj69QuiYWY5T+TgNANc8G9x5Yc52u1atUOsqs+vAIt9kbnkrj
RRqVrOFasViXocGFdxOmNhKut+Rl0qpU9LNqVzueTWP7kpFV/fBm+jRpq8H79y9p
mmrDeMg/i/VJxhnhpB7vrzKZpAP6sJ+KJUMY
=SqBX
-----END PGP PUBLIC KEY BLOCK-----

```> 
Finally, the key/sig for flash64:
[https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash")
```

$ gpg --keyserver keyserver.ubuntu.com --recv-keys 61E46227
gpg: requesting key 61E46227 from hkp server keyserver.ubuntu.com
gpg: key 61E46227: public key "Launchpad Default PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

$ gpg -a --export 61E46227
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mI0ESrZJBwEEAKgM1pykdrm07mA4V2s3zht3BcZErHWQra5gpeAI5jAobhTz6gnf
cBW8MN7GlgewFYlwey9QdJT+LaK9vlbhEzMCwXFzEEOnf5ha9rO9XHHmYeBOGjVV
Xbhz/TMl1q1RaYw3eEDkaqVNmY0B5aaDt8+BIa5LtFJBhCX5BmkBRTYVABEBAAG0
FUxhdW5jaHBhZCBEZWZhdWx0IFBQQYi2BBMBAgAgBQJKtkkHAhsDBgsJCAcDAgQV
AggDBBYCAwECHgECF4AACgkQNdoBwmHkYifgtgQAnNBQx82hp3EpuTNeCFqvjTor
wSao6UB9WoSkDSFXAY4uvkQWW6u/NQeTbZjqcgbyTXFc14tZ9WPQLW2Rd7aw6zUc
FUqdi2112qQtHqADz3KY99LDaLl606jL+dGKv12LCZikh2KO6u0HHdHjImfbmIdV
d7oIxOBBixHEElIwlHM=
=HQ3n
-----END PGP PUBLIC KEY BLOCK-----

```Now just save each "ascii-armored" key to a file and use "sudo apt-key add filename".

Consider requesting that the firewall be modified to open port 11371, since this will enhance security.  Point them at this handy Debian article that explains Secure Apt: [http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

---

### Post by oshirowanen on 2010-05-12
Hi gmargo:

That looks perfect.  I will do this tomorrow.  I really appreciate the help.

Thanks.

---

### Post by oshirowanen on 2010-05-26
Hello

Really sorry about this, but I need another key/sig as I cannot run this command because our firewall will not allow me to use the ubuntu's keyserver port.

sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E

---

### Post by gmargo on 2010-05-26
> **oshirowanen said:**
> 
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E

```

$ gpg --keyserver pgp.mit.edu --recv-keys 5044912E
gpg: requesting key 5044912E from hkp server pgp.mit.edu
gpg: key 5044912E: public key "Dropbox Automatic Signing Key <linux@dropbox.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

$ gpg -a --export 5044912E
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQENBEt0ibEBCACv4hZRPqwtpU6z8+BB5YZU1a3yjEvg2W68+a6hEwxtCa2U++4d
zQ+7EqaUq5ybQnwtbDdpFpsOi9x31J+PCpufPUfIG694/0rlEpmzl2GWzY8NqfdB
FGGm/SPSSwvKbeNcFMRLu5neo7W9kwvfMbGjHmvUbzBUVpCVKD0OEEf1q/Ii0Qce
kx9CMoLvWq7ZwNHEbNnij7ecnvwNlE2MxNsOSJj+hwZGK+tM19kuYGSKw4b5mR8I
yThlgiSLIfpSBh1n2KX+TDdk9GR+57TYvlRu6nTPu98P05IlrrCP+KF0hYZYOaMv
Qs9Rmc09tc/eoQlN0kkaBWw9Rv/dvLVc0aUXABEBAAG0MURyb3Bib3ggQXV0b21h
dGljIFNpZ25pbmcgS2V5IDxsaW51eEBkcm9wYm94LmNvbT6JATYEEwECACAFAkt0
ibECGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRD8kYszUESRLi/zB/wMscEa
15rS+0mIpsORknD7kawKwyda+LHdtZc0hD/73QGFINR2P23UTol/R4nyAFEuYNsF
0C4IAD6y4pL49eZ72IktPrr4H27Q9eXhNZfJhD7BvQMBx75L0F5gSQwuC7GdYNlw
SlCD0AAhQbi70VBwzeIgITBkMQcJIhLvllYo/AKD7Gv9huy4RLaIoSeofp+2Q0zU
HNPl/7zymOqu+5Oxe1ltuJT/kd/8hU+N5WNxJTSaOK0sF1/wWFM6rWd6XQUP03Vy
NosAevX5tBo++iD1WY2/lFVUJkvAvge2WFk3c6tAwZT/tKxspFy4M/tNbDKeyvr6
85XKJw9ei6GcOGHD
=5rWG
-----END PGP PUBLIC KEY BLOCK-----

```

---

### Post by oshirowanen on 2010-05-27
For some reason that key is not working?

---

### Post by gmargo on 2010-05-27
> **oshirowanen said:**
> For some reason that key is not working?
In what way?  You'll have to give me a clue on how to test it.

---

### Post by oshirowanen on 2010-05-28
Ignore me, the key was OK, but for some reason the software installation fails.

---


---
title: "Safari On Ubuntu."
date: 2009-07-26
forum: General Help
---

### Post by TheNerdAL on 2009-07-26
Is there a way to get Safari On Ubuntu? If there is, Can anyone Tell me How?

---

### Post by credobyte on 2009-07-26
[http://ubuntu-unleashed.com/2008/03/howto-install-safari-on-ubuntu-with-flash-and-shockwave-hulu-youtube-shockwave-works.html](http://ubuntu-unleashed.com/2008/03/howto-install-safari-on-ubuntu-with-flash-and-shockwave-hulu-youtube-shockwave-works.html) ( involves Wine ).

---

### Post by TheNerdAL on 2009-07-26
In that Case, I will stick with FireFox. :P

---

### Post by darolu on 2009-07-26
You can use a Webkit browser; it is what Safari and Chrome use to render webpages (firefox uses gecko and opera uses presto); I personally like Epiphany but for some reason Jaunty doesn't have Epiphany-webkit in its repositories; you can try Midori though:
```
sudo apt-get install midori
```
Or search Midori with the Add/remove at Applications menu.

You can however install Epiphany (my favourite browser) with Webkit adding this repositories to your sources.list file or under system - admin - software sources:
```
# Epiphany Webkit PPA
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
```

Create a file named webkit.key and copy/paste this and save:
```
<html><head><title>Public Key Server -- Get ``0x991e6cf92d9a3c5b ''</title></head>
<body><h1>Public Key Server -- Get ``0x991e6cf92d9a3c5b ''</h1>
<pre>
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXd+zAEEAOvjASmjPdNPHAkyGQGwN7l0zdtdUkG9ekVDfhDZxu8OYL+jfeAoFWA4/KhT
CUnLPfNuWu6G5tlWedpPjgQcwAdlxv4ARSoKh0msNlr2WVyPeALPaRvjull0T6oR/dnPPWq7
nyb+8pXCJco5Vdt85cnMPheqSw71+FVJ3+Lp4dbvABEBAAG0HUxhdW5jaHBhZCBQUEEgZm9y
IFdlYktpdCBUZWFtiLYEEwECACAFAkl3fswCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAK
CRCZHmz5LZo8W5m1BADK/Q9BUKZIeppes435z17lyTvqwSqif7NDj0dsFDXrpyTDYAIvNsV6
TYZ1gxCNLfOCaF3oxNgqB+FxVDh2OK1Agylm82XrfsB6P6WRIJvnEzsvMT/N6kZfEb0M/I2b
ohU1rn91UyN/vO6410LK1/hlNy0jpzKXEit/rI+ZCrcPRA==
=0io6
-----END PGP PUBLIC KEY BLOCK-----
</pre>
</body></html>
```
then:
```
sudo apt-key add webkit.key
```
And you can install with:
```
sudo apt-get install epiphany-webkit mozplugger
```

Or you can get the latest versions (in .deb files fo Ubuntu) here:

[https://launchpad.net/~webkit-team/+archive/epiphany](https://launchpad.net/~webkit-team/+archive/epiphany)

---

### Post by TheNerdAL on 2009-07-26
I will Stick With FireFox.:P

---

### Post by binbash on 2009-07-26
You can run Safari with wine but it crashes so often.Stick with firefox

---


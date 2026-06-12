---
title: "Trouble with add-apt-repository behind proxy"
date: 2011-05-16
forum: General Help
---

### Post by mebigfatguy on 2011-05-16
I am trying to do

sudo add-apt-repository ppa:freenx-team

from behind a proxy. 

Issuing **export** from the terminal gives

declare -x ftp_proxy="ftp://proxy.acme.com:80/"
declare -x http_proxy="http://proxy.acme.com:80"
declare -x https_proxy="http://proxy.acme.com:80"

which is the correct proxy for my company (and works elsewhere)

however the add-apt-repository fails with

[B]Error reading [https://launchpad.net/api/1.0/~freenx-team/+archive/ppa:](https://launchpad.net/api/1.0/~freenx-team/+archive/ppa:) <urlopen error [Errno 113] No route to host>
[/B]

This same action works correctly from my home machine that is not behind a proxy. Is there somewhere else i need to specify the proxy for add-apt-repository?

this is on ubuntu 11.04

---

### Post by gsmanners on 2011-05-16
Sounds similar to this:

[Problem adding repositories ...]("http://askubuntu.com/questions/23211/problem-adding-repositories-and-connecting-from-terminal-behind-a-proxy")

---

### Post by mebigfatguy on 2011-05-16
thanks, following that instruction 

> create a file in /etc/sudoers.d with

Defaults env_keep = https_proxy

in it

does change things abit, now i'm getting


gpg: requesting key D018A4CE from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: No route to host



I also tried launchpad-getkeys as described here [http://www.webupd8.org/2011/02/launchpad-getkeys-gets-proxy-support.html](http://www.webupd8.org/2011/02/launchpad-getkeys-gets-proxy-support.html) with no love.

---

### Post by kabeza on 2012-04-24
I am with the same problem when trying to add a repository from terminal

```
keyserver.ubuntu.com: No route to host
gpgkeys: HTTP fetch error 7: couldn't connect: No route to host
```

Is there a proven solution?

---


---
title: "apt-get behind firewall?"
date: 2006-05-29
forum: General Help
---

### Post by bullgr on 2006-05-29
hi...

i have a firewall installed and when i try to use "apt-get" i get errors.
it's because the outgoing ports are blocked.
when i stop the firewall all it's ok.

i read somewhere that if i use proxy server the problem are done.
[HTML]Edit your /etc/bash.bashrc file as root.

Put these line at the end of your /etc/bash.bashrc file :

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/
[/HTML]

but if i don't have proxy?
it's complicated to use this sollution.
is there anything better?
how can i setup the firewall to use "apt-get"?

---

### Post by az on 2006-05-29
[QUOTE=bullgr]hi...

i have a firewall installed and when i try to use "apt-get" i get errors.
it's because the outgoing ports are blocked.
when i stop the firewall all it's ok.

i read somewhere that if i use proxy server the problem are done.
[HTML]Edit your /etc/bash.bashrc file as root.

Put these line at the end of your /etc/bash.bashrc file :

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/
[/HTML]

but if i don't have proxy?
it's complicated to use this sollution.
is there anything better?
how can i setup the firewall to use "apt-get"?[/QUOTE]

The archives use port 80 just like your web browser.  If you cannot access them, that means you cannnot access the web, either.  Do you use a proxy for your web?  You can set up your proxy using synaptic, I beleive....

---

### Post by bullgr on 2006-05-29
i have access to the web, i be able to make
> sudo apt-get update

the dependencies list are update normal.
but when i try to make
> sudo apt-get dist-upgrade
i get errors.

then i disable the firewall (iptables), then i can
> sudo apt-get dist-upgrade
without problems...

---


---
title: "Paid for a game but can't download"
date: 2011-10-15
forum: General Help
---

### Post by GoldWing on 2011-10-15
Hi,

I bought a games for $15 but I can't download it,
Now, I receive following error when trying to download from the sofwarecenter


Server Error (500)
An error occurred which prevented the page you requested from loading. If this problem continues, please consider reporting this problem by sending an e-mail to [email]webmaster@canonical.com[/email]

(Error ID: ) 2114satsuma320321



When I do a manual sudo apt-get update, I am receiving this:

W: Ophalen van [https://private-ppa.launchpad.net/commercial-ppa-uploaders/familyfarm/ubuntu/dists/oneiric/main/binary-amd64/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/familyfarm/ubuntu/dists/oneiric/main/binary-amd64/Packages) Problem with the SSL CA cert (path? access rights?) is mislukt

W: Ophalen van [https://private-ppa.launchpad.net/commercial-ppa-uploaders/familyfarm/ubuntu/dists/oneiric/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/familyfarm/ubuntu/dists/oneiric/main/binary-i386/Packages) Problem with the SSL CA cert (path? access rights?) is mislukt

E: Some index files failed to download. They have been ignored, or old ones used instead.


Some words are in Dutch, "is mislukt" just means failed.


Thx.

---

### Post by GoldWing on 2011-10-17
is there an official place where I can put this question? It's not normal that you pay for stuff and don't find a way to install it.

---

### Post by jockyburns on 2011-10-17
Your first port of call, should be the [email]webmaster@canonical.com[/email]  quoting the reference you've been given. I don't know if the canonical website has any contact information for failed downloads. Perhaps worth browsing there to see if there is??

Edit, here's all of the contact details for Canonical

[http://www.canonical.com/about-canonical/contact](http://www.canonical.com/about-canonical/contact)

---

### Post by GoldWing on 2011-10-17
thanks.
It's a confirmed bug:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/804900](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/804900)

---


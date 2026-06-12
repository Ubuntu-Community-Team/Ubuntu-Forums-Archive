---
title: "An error occurred  The following details are provided:"
date: 2009-07-29
forum: General Help
---

### Post by Mrcollegeman on 2009-07-29
[SIZE=4]Can some one please tell me if their is a fix for this error message here? :confused:[/SIZE] 

[SIZE=3]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

This is from Ubuntu 9.04 in the Update Manager...
[/SIZE]

---

### Post by wojox on 2009-07-29
Open a terminal:

```
gpg --keyserver keyserver.ubuntu.com --recv 247510BE
```

Then:

```
gpg --export --armor 247510BE | sudo apt-key add -
```

---

### Post by sisco311 on 2009-07-29
You have to add the ppa key. Open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
```

```
sudo apt-get update
```

[https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

---

### Post by Mrcollegeman on 2009-07-29
> **Mrcollegeman said:**
> [SIZE=4]Can some one please tell me if their is a fix for this error message here? :confused:[/SIZE] 

[SIZE=3]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

This is from Ubuntu 9.04 in the Update Manager...
[/SIZE]

[SIZE=4]I would like to say thank-you guy's and it worked.. :)[/SIZE]

---


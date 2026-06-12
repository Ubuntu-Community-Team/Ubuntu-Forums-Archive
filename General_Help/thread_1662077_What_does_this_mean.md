---
title: "What does this mean?"
date: 2011-01-07
forum: General Help
---

### Post by sbaig on 2011-01-07
Theres a triangle with an exclamation mark on the top right of my screen. I got this message, after I tried to update : > GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I have no idea what it means and how to fix it. Help please?

---

### Post by mmsmc on 2011-01-07
i tried going to it, and the page does not exist, just ignore it

---

### Post by plucky on 2011-01-07
> **sbaig said:**
> Theres a triangle with an exclamation mark on the top right of my screen. I got this message, after I tried to update : 

I have no idea what it means and how to fix it. Help please?

Open **Software Sources** and disable the PPA for Ubuntu-win as that is not a valid URL.

Good Luck

---

### Post by sbaig on 2011-01-07
thanks I did that but it didn't fix it lol. the error message just got shorter.

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

still no idea what it means :$

---

### Post by plucky on 2011-01-08
> **sbaig said:**
> thanks I did that but it didn't fix it lol. the error message just got shorter.



still no idea what it means :$

It means you added a PPA but didn't add the authentication key to the PPA.

See [Here](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

and open a terminal ```
gpg --keyserver keyserver.ubuntu.com --recv 5A9A06AEF9CB8DB0 
gpg --export --armor 5A9A06AEF9CB8DB0  | sudo apt-key add -

``` should add the key for you.

Good Luck

---

### Post by sbaig on 2011-01-10
ok thank you so much.

---


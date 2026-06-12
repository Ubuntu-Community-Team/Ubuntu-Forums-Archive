---
title: "Can't insall this morning's updates."
date: 2011-11-12
forum: General Help
---

### Post by Linuxratty on 2011-11-12
Why?
Because one of them is Adobie Flash and it's coming from where? Ubuntu's repositories.
I've tried four times. First it tells me that I need to check my internet connection
 
It's fine.

Then it tells me another update manager is open.

Nope, it's the only one open.

So I reboot.

Then it tells me it can't install updates cause one of them selected for me can't be trusted.
I know Adobie's Flash is trash...Just give me the bloody update!

Why is there not an "install it anyway,you idiot" button?

So how do I make it do this? Sure I can tell it to forget Adobe, but I'd like my plug in.

---

### Post by raja.genupula on 2011-11-12
```
sudo apt-get update
```

output post here

---

### Post by Linuxratty on 2011-11-12
> **raja.genupula said:**
> ```
sudo apt-get update
```

output post here

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.88.33), connection timed out

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
gozzin@gozzin-System-Product-Name:~$

Ok,looks like that's as good as it gets. Thanks.

---

### Post by stinkeye on 2011-11-12
Had similar error messages earlier but working now.
Maybe just a key server issue?

---

### Post by ballantony on 2011-11-12
> **stinkeye said:**
> Had similar error messages earlier but working now.
?

Ditto

---

### Post by snakeplizzken on 2011-11-12
This is what I get:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.


I have tried several servers.

---

### Post by ElGaton on 2011-11-12
Maybe the Ubuntu server is just overloaded - try waiting some minutes.

---

### Post by raja.genupula on 2011-11-12
> **snakeplizzken said:**
> This is what I get:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.


I have tried several servers.

...update manager -> settings --> other software and uncheck that canonical PPA and update again

---

### Post by Lupine on 2011-11-12
Yeah, it's a little on the "hit or miss" side of things this morning.  I ran it 2 minutes ago, and it failed.  I ran it 2 seconds ago, and it worked.  Must just be a problem with 91.189.88.33

---

### Post by Linuxratty on 2011-11-13
> **Lupine said:**
> Yeah, it's a little on the "hit or miss" side of things this morning.  I ran it 2 minutes ago, and it failed.  I ran it 2 seconds ago, and it worked.  Must just be a problem with 91.189.88.33

Ok,I tried this morning and it worked.
Thanks!

---


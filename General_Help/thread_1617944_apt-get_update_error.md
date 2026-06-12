---
title: "apt-get update error"
date: 2010-11-10
forum: General Help
---

### Post by Verbeck on 2010-11-10
when ever i run apt-get update i'm getting the following error at the end.

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

i'v tried changing the servers and also a using generating sources.list from [here]("http://repogen.simplylinux.ch") but it doesn't fix it

any help?

edit : tried this too [http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

### Post by ubudog on 2010-11-10
Check out this page, it may help:
[http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error](http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error)

---

### Post by Verbeck on 2010-11-10
> **ubudog said:**
> Check out this page, it may help:
[http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error](http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error)

still doesn't work :(

---

### Post by ubudog on 2010-11-10
Hmm... try this page, it's on the forums.

[http://ubuntuforums.org/showthread.php?t=1616840](http://ubuntuforums.org/showthread.php?t=1616840)

---

### Post by drs305 on 2010-11-10
How about:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5

```
I'm currently using the Georgia Tech repository in the US.

---

### Post by ubudog on 2010-11-10
> **drs305 said:**
> How about:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5

```
I'm currently using the Georgia Tech repository in the US.

That should work.  Any progress OP?

---

### Post by Verbeck on 2010-11-10
Fixed :D thanx all
i was about to reinstall

---

### Post by ubudog on 2010-11-10
> **Verbeck said:**
> Fixed :D thanx all
i was about to reinstall

Cool.  :P

---


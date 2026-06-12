---
title: "RT Click Encrypt Nautilus Gone 11.10"
date: 2011-12-03
forum: General Help
---

### Post by strange_cathect on 2011-12-03
In 11.10 I do not have a right click encrypt option as in previous versions of Ubuntu.

I have GNUpg and seahorse installed. Ideas?

---

### Post by strange_cathect on 2011-12-04
Bump

---

### Post by GiladGressel on 2011-12-09
bump!
same problem for me

i'd like it back

in the meanwhile can someone tell me how to decrypt my files some other way? it's the only way i knew how to use ecryption/decryption.

-gilad

---

### Post by Denis on 2011-12-11
Hi

I have exactly the same problem. This bug report files the disappearance of seahorse-plugins: [https://bugs.launchpad.net/debian/+source/seahorse-plugins/+bug/796752/](https://bugs.launchpad.net/debian/+source/seahorse-plugins/+bug/796752/) It seems to be related to the maintenance of the package, which also includes the plugins for nautilus. As far as I understood, the package is incompatible with latest versions of Gnome. 

I think it's rather unacceptable that users who relied on the encryption/description GUI are now left with files they can't easily open. I do hope the next version of Ubuntu addresses this issue...

In the mean while, I successfully used the following command to decrypt files: 
```
gpg -d --output new_file.tar.bz2 'encrypted_file.tar.bz2.pgp'
```
If all goes well, it will ask for your passphrase and create a new file (specified by the --output option).

---

### Post by aneganov on 2012-03-21
For 11.10:

```
sudo add-apt-repository ppa:mdeslaur/testing 
sudo apt-get update
sudo apt-get install seahorse-plugins
```

---

### Post by ottosykora on 2012-04-22
> **aneganov said:**
> For 11.10:

```
sudo add-apt-repository ppa:mdeslaur/testing 
sudo apt-get update
sudo apt-get install seahorse-plugins
```

do you have any idea where to get anything like tha tfor the current versions of ubuntum as it seems to not exist any more.

---


---
title: "what would be the linux version of MS EFS?"
date: 2011-05-27
forum: General Help
---

### Post by ant2ne on 2011-05-27
MS EFS is so easy and so efficient. What woudld be a linux equivelant. I've been playing with [encfs]("http://www.cs.arizona.edu/computing/utilities/linux-encryption.html"), but I'm running into a fusermount issue. (never could get that to work like it is supposed to.) I'm just wondering if there are any other user side options. I dont' want the users to need to sudo to encrypt or decrypt their own data.

---

### Post by linuxinstalledfromhdd on 2011-05-27
I have installed SELinux, and that might be what you are looking for:

[http://en.wikipedia.org/wiki/Security-Enhanced_Linux](http://en.wikipedia.org/wiki/Security-Enhanced_Linux)

It works great, albeit more slowly than normal under the circumstances. :p

---

### Post by Joe of loath on 2011-05-27
I think it's luks, I encrypted a hard drive with it a few weeks back. It 'Just Works', Linux asks you for a password when you plug it in (tested on Arch and Lubuntu 10.10/11.04), if you get the password right it mounts. Pretty foolproof AFAIK.

You can enable it using the disk utility, just format a drive and select 'encrypt underlying filesystem'.

---

### Post by ant2ne on 2011-06-01
luks looks very interesting. I think I'll give it a test on a blank partition.

---


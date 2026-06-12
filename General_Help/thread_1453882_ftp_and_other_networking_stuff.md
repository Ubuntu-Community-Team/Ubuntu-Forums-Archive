---
title: "ftp and other networking stuff"
date: 2010-04-13
forum: General Help
---

### Post by flyingsliverfin on 2010-04-13
i know that firefox can do ftp connections, then display the different files and folder at the other ends in a user-friendly way. however, is this safe? What i mean is does it use a secure tunnel or sftp or something so that my password and username for the ftp server aren't sent in cleartext?

what im trying to do is set up a private ftp server on my comp at home, and then have my friends access it from their web browser at their house, so they can upload and download files. However, they aren't about to use the command line or anything like that (their not that great at computer stuff). I also dont want their username and password sent in cleartxt...

Unless there's something like the [ftp://___](ftp://___) in firefox only for sftp (like sftp://___), which would make things a lot easier. I've already got a ssh server running somewhere else in my house.

---

### Post by takisan on 2010-04-13
It should just be at [ftp://ipaddress/](ftp://ipaddress/)
It'd prompt you for a user and password. You can still make ftp connections without needing to use a web browser.

---


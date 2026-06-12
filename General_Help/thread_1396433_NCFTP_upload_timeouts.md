---
title: "NCFTP upload timeouts"
date: 2010-02-02
forum: General Help
---

### Post by dyingsun on 2010-02-02
Hello

Trying to upload a directory tree to a remote server using NCFTP,
using ```
put -R
```. It uploads for a few minutes then the remote host closes the connection. I then have to reconnect, start the upload again using ```
s!
``` to skip files already uploaded, then it has to remember where it left off and then continue the upload. For a couple of minutes. It's getting there, slowly, but there must be a way of either maintaining the connection, or setting ncftp to reconnect automatically and resume the upload.

Anybody know how to do this? I cant find it in the manual or various forums. It's annoying to have to babysit a transfer!

Thanks in advance!

---


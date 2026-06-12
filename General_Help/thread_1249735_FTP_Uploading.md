---
title: "FTP Uploading?"
date: 2009-08-25
forum: General Help
---

### Post by PaulTR on 2009-08-25
I connected to an ftp server using the "connect to server" option under places, and it opens up the page in firefox, but I'm not sure how to upload files to the server. I try to drag and drop the index.html and images file I want to go there, but it just opens them in firefox and doesn't upload them. Thanks.

---

### Post by crystal88_ on 2009-08-25
I don't use nautilus but what about ctrl+c ctrl+v ?

---

### Post by uylug on 2009-08-25
> **crystal88_ said:**
> I don't use nautilus but what about ctrl+c ctrl+v ?

Sure. Nautilus has a complete ftp client inside!

run this command:

```
nautilus sftp://your_host_address
```
or
```
nautilus ftp://your_host_address
```

---


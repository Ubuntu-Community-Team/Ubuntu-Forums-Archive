---
title: "Downloading files  - HTTP or not?"
date: 2010-06-11
forum: General Help
---

### Post by zozza on 2010-06-11
This isn't really an Ubuntu question but I can't find out with Google.

I just want to confirm something.

When anyone connects to a website using HTTP or HTTPS and downloads a document (like a .doc file) or a photo (like .jpg) or a program (.exe) where Firefox asks you where you want to download it to, what protocol is used.

And the same for when you upload a file to a server

In other words: are the downloads HTTP or HTTPS traffic going to port 80 or 443 on the client (i.e. my) machine?

Thanks.

---

### Post by weemadarthur on 2010-06-11
No, your machine connects to port 80 (HTTP) or 443 (HTTPS) on the server.

---

### Post by zozza on 2010-06-11
>  	 		**Re: Downloading files  - HTTP or not?**
 		No, your machine connects to port 80 (HTTP) or 443 (HTTPS) on the server. 	

Yes, I know my machine connects to port 80 or 443.  I just want to confirm that anything uploaded or downloaded (like a .exe or .doc file) is also using the HTTP/S protocols on these ports.

Thanks.

---

### Post by Jakiejake on 2010-06-11
> **zozza said:**
> When anyone connects to a website using HTTP or HTTPS and downloads a document (like a .doc file) or a photo (like .jpg) or a program (.exe) where Firefox asks you where you want to download it to, what protocol is used.


FTP (File Transfer Protocol)

---


---
title: "Authentication for printing"
date: 2009-08-25
forum: General Help
---

### Post by theozzlives on 2009-08-25
I have Windows XP & 7 in a Virtual Box. My print server is Ubuntu 9.04. Ubuntu wants Authentication to print jobs over the network, Windows provides no such option. Therefore I can't print from Windows.

How do I override the authentication requirement that Ubuntu has?

P.S. I'm using SAMBA for my network.

---

### Post by Ms_Angel_D on 2009-08-25
Try visiting [http://127.0.0.1:631/](http://127.0.0.1:631/)

Look under the admistration tab and make sure "Share published printers connected to this system" is checked. It will tell you it needs to restart the server when you click "change Settings", you'll be asked for a username and pass those would be same as your login name & pass for ubuntu.

I have found sharing printers with windows computers to be easiest setup this way.

---

### Post by theozzlives on 2009-08-25
> **Ms_Angel_D said:**
> Try visiting [http://127.0.0.1:631/](http://127.0.0.1:631/)

Look under the admistration tab and make sure "Share published printers connected to this system" is checked. It will tell you it needs to restart the server when you click "change Settings", you'll be asked for a username and pass those would be same as your login name & pass for ubuntu.

I have found sharing printers with windows computers to be easiest setup this way.

Thanks, I was tired of printing my Invoices to PDF then using Ubuntu to print. :)

---

### Post by Ms_Angel_D on 2009-08-25
So did it work then for ya ;) If so glad I could help :)

---

### Post by theozzlives on 2009-08-26
> **Ms_Angel_D said:**
> So did it work then for ya ;) If so glad I could help :)

Ya it worked! How about I by you a steak dinner? That's been a problem for 2 years now.

---

### Post by Ms_Angel_D on 2009-08-26
lol aww gee thanks. :D

Happy Printing!!!

:guitar:

---

### Post by theozzlives on 2009-08-27
> **Ms_Angel_D said:**
> lol aww gee thanks. :D

Happy Printing!!!

:guitar:

;)

---


---
title: "How do I... print/file server?"
date: 2010-09-21
forum: General Help
---

### Post by dougalkerr on 2010-09-21
Hi folks - I have an old PC at work and want to consider using it as a print server. A file server isn't any use as we already have access to Networked machines.
So, I have never though about this before and need to know what is involved. I would be using either Crunchbang or the latest Ubuntu.
Crunchbang is nice and lightweight and I am familiar with it.

Any howtos going around?

Thanks.

---

### Post by pbrane on 2010-09-21
Using Ubuntu you would configure your printer and network access to the printer with CUPS. Then you simply setup your network printing on the computers you want to print from.

If you point your web browser to localhost:631 on an Ubuntu machine you will see the CUPS home page. you should see a link called **Using Network Printers**. From there you can access help on **Printer Sharing** in the right side menu.

I was able to set mine up pretty quickly, there are lots of tutotials on the web about this.

---

### Post by dougalkerr on 2010-09-22
Thanks very much for the info.

---


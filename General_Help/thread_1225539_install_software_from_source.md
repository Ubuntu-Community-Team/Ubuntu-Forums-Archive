---
title: "install software from source"
date: 2009-07-28
forum: General Help
---

### Post by gishaust on 2009-07-28
Hi Ubuntu fans

I want to install the latest version of nebeans from tgz as I think the repositories have only older versions.

I want to know the following about Ubuntu,

Where is the best place to install it?
How do I remove it when I update to the next version?

Secondly is it hard to package as I use netbeans a lot and I might try and package it? But I have no idea how to do it!

Thanks for any assistance.

---

### Post by ibutho on 2009-07-28
If you are installing for multiple users, then /opt/netbeans is a good place to install it. For yourself, anywhere in your home directory will do. Its not difficult to uninstall netbeans because it comes with an uninstall script. Don't know how easy or difficult it is to package netbeans.

---

### Post by gishaust on 2009-07-28
Thanks 

For the reply is opt the storage area for the packages. Because I have read that bin is the installation area for the binaries in linux.

I have no idea how to package but if I can help the community in a small way that would be great as it has give me so much.

---

### Post by ibutho on 2009-07-28
/opt is correct for things like netbeans (because netbeans comes as a prebuilt package with its supporting libraries and other files in one diretory). Take a look at the [FHS]("http://www.pathname.com/fhs") to find out where things go in Linux and other Unix like systems.

---


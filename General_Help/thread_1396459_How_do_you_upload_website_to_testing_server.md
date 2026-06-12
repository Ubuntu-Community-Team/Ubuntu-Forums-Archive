---
title: "How do you upload website to testing server"
date: 2010-02-02
forum: General Help
---

### Post by drarncruz on 2010-02-02
This is what I have thus far:
1. uploaded Ubuntu 9.10 and finally got rid of windows
2. installed LAMP - 
3. trying to extract a site to var/www

The Problem:  I keep getting the message I do not have permission to that folder.

Can anyone help?  Is there a simple solution?

Thanks

---

### Post by Some Penguin on 2010-02-02
Ask yourself which user account owns that directory and thus has write permissions (/var/www, if that already exists; /var, if /var/www doesn't and therefore you need to create it), and which user account you happen to be using.  Reconcile the two.

---

### Post by lordskid on 2010-02-02
I believe it is owned by root by default. so you might want to sudo chown yourusername:yourgroup /var/www

correct me if I am wrong though.

---


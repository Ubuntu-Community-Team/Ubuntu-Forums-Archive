---
title: "I messed up with chown"
date: 2012-04-02
forum: General Help
---

### Post by morle on 2012-04-02
Hi,

I was trying to install Joomla following the instructions here: [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

When configuring access rights for Joomla 2.5.3 (I followed the instructions for the 1.5 version) I <snip> up. Instead of being in /var/www/joomla directory, I was at /var/www,
so now all is owned by root.

Is there a way to return to the normal privileges for that folder?

Thanks!

PS: I don't know what privileges were before I messed up.

---

### Post by winh8r on 2012-04-02
SEE POST BELOW BY Lars Noodén

---

### Post by morle on 2012-04-02
Thanks! I'll check it now!

---

### Post by Lars Noodén on 2012-04-02
> **winh8r said:**
> This thread might help you:

[http://ubuntuforums.org/showthread.php?t=1381217]("http://ubuntuforums.org/showthread.php?t=1381217")

Or it might harm him.  ;)  That thread advises to change the owner for /var/www to www-data instead of root.  That gives write access to the directory by the web server and that is not necessarily wise.  

To reset /var/www back to the defaults which were user root, group root:

```

sudo chown root:root /var/www
sudo chmod u=rwx,g=rx,o=rx /var/www

```

www-data is used for privilege separation in the web server and should not own anything and the corresponding group should not have any additional members.

---

### Post by morle on 2012-04-03
Thanks!

---

### Post by Adrian98 on 2012-04-05
> **winh8r said:**
> SEE POST BELOW BY Lars Noodén

Thanks for the post, although I don't get it tried till now but I think , This would solve the issue!!

---


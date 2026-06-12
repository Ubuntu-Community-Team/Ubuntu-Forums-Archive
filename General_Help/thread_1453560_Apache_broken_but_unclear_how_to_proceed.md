---
title: "Apache broken but unclear how to proceed"
date: 2010-04-13
forum: General Help
---

### Post by davidpbrown on 2010-04-13
I run Apache for localhost, running simple services under PHP. Having changed nothing directly, it's now not working "can't establish a connection to the server at localhost".


---------------
Edit:

I tried restarting the server and got an error "bad user name ${APACHE_RUN_USER}"
which [led to a manual solution]("http://ubuntuforums.org/showthread.php?t=804436")

So,
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart

That gets it working but I've no sense of what's changed or why that apparently better way of starting the server is now needed.

---


---
title: "Webmin in ubuntu"
date: 2005-01-21
forum: General Help
---

### Post by schleyfox on 2005-01-21
I am having a bit of trouble getting webmin to work on my ubuntubox.  I seem to have an issue with the whole lack of root thing.  I am unsure of how to log on to this beast.  Any ideas?

---

### Post by machiner on 2005-01-22
You shouldn't be having any "root" issues. When you install Webmin (please - compile it yourself from the .tar download at the webmin site...1.170)
extract, cd to the extracted directory and run the following command:

sudo sh setup.sh /usr/local/webmin

Webmin defaults to the user "admin" you pick your password.

After it is installed ... open your browser goto:
127.0.0.1:10000
then logon with admin and whatever you chose as a password.

The webmin uname/password has nothing at all to do with SU on your linux box.

Good Luck

---


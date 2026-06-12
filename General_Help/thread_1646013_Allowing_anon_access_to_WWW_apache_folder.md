---
title: "Allowing anon access to WWW apache folder"
date: 2010-12-15
forum: General Help
---

### Post by ryanrobinson on 2010-12-15
Hi guys,

I have recently installed a LAMP server on Ubuntu 10.4 and I would like to have the /var/www folder writeable and accessible by my other computers on the LAN. I know I have to install Samba but how do I configure it so I can map network drives to the WWW folder and allow read and write access?

Thanks.

---

### Post by iansyngin on 2010-12-15
> **ryanrobinson said:**
> Hi guys,

I have recently installed a LAMP server on Ubuntu 10.4 and I would like to have the /var/www folder writeable and accessible by my other computers on the LAN. I know I have to install Samba but how do I configure it so I can map network drives to the WWW folder and allow read and write access?

Thanks.

i would do this

cd /var
sudo chmod o+w -R www

---

### Post by ryanrobinson on 2010-12-15
I have done that but as the files will be accessed by a mapped network drive I think something needs to be done in the Samba config file to allow the files to be browsed.

---


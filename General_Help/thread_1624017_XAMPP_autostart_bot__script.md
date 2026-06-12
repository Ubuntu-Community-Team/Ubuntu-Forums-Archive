---
title: "XAMPP autostart bot / script"
date: 2010-11-17
forum: General Help
---

### Post by KevzJD on 2010-11-17
I'm using XAMPP on ubuntu and everytime i boot up into ubuntu i have to keep running the command line "/opt/lampp/lampp start" is there anyway this can start automatically after i login? if not is there a way i can create like an executionable file where i just double click it and it runs that command?

Thanks

---

### Post by Korabza on 2011-09-07
Use the following command ...
sudo ln -s /opt/lampp/lampp /etc/init.d/lampp
sudo update-rc.d -f lampp defaults

---


---
title: "Libfeoffice doesn't work"
date: 2012-02-20
forum: General Help
---

### Post by Welly Wu on 2012-02-20
Hi. I made a mistake today. I had the Libreoffice PPA installed and I am using Ubuntu 11.10 64 bit. I changed the oneiric to precise and I tried to do sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade, but the newer version of Libreoffice does not start. None of the Libreoffice applications work. So, I removed the Libreoffice PPA and I typed in sudo apt-get remove libreoffice libreoffice-gnome. I tried to re-install Libreoffice by typing in sudo apt-get install libreoffice libreoffice-gnome, but Libreoffice still does not work. None of the Libreoffice applications work. It says this error message:

The application cannot be started. 
A general error occurred while accessing your central configuration.

What should I do to fix this problem? How can I get Libreoffice to work again?

Please help me as soon as possible. Thank you!

---

### Post by wildmanne39 on 2012-02-20
Hi, you can try this:
```
sudo apt-get --purge remove libreoffice
```
that will also remove the configuration files, then reinstall the original libreoffice.
Thanks

---

### Post by Welly Wu on 2012-02-20
I did that and I re-installed Libreoffice by typing in sudo apt-get install libreoffice. When I launch Libreoffice or Libreoffice Writer, it shows the Libreoffice window, but the application does not launch. What else can I do to solve this problem?

---

### Post by wildmanne39 on 2012-02-20
Hi, if you used this command:
```
sudo apt-get --purge remove libreoffice
```
with --purge in it then I do not have any more ideas.

---


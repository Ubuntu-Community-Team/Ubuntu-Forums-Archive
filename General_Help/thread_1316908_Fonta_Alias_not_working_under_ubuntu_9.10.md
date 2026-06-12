---
title: "Fonta Alias not working under ubuntu 9.10"
date: 2009-11-06
forum: General Help
---

### Post by dagonfire01 on 2009-11-06
Hi all I'm trying to get my font alias to work for Thai on Ubuntu 9.10. On OpenSUSE and Fedora the steps I did with editing the /etc/X11/fonts/75dpi or 100dpi Are working.

I have edited the font.alias under both the 75dpi and 100dpi directories. Not sure why the alias are failing to work. 

If anybody wise than me can show my errors I would be grateful.

Thanks ):P

---

### Post by Giblet5 on 2009-11-06
Did you run ```
mkfontdir
``` in those subdirectories afterwards?

---

### Post by dagonfire01 on 2009-11-06
Hi,

Yes I did the mkfontdir in both the 75dpi and 100dpi directory. After this I even tried to perform 

sudo update-fonts-alias 100dpi
sudo update-fonts-alias 75dpi
sudo fc-cache -vf

---


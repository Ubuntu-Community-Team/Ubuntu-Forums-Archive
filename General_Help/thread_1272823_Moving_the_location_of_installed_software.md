---
title: "Moving the location of installed software"
date: 2009-09-22
forum: General Help
---

### Post by dsarfati on 2009-09-22
Hi, I recently downloaded eclipse from the website and installed it on my desktop. 1) Where are the applications that are in the Applications bar located? and 2) How can I move my eclipse installation into the Programming subsections of Applications?

Thanks,

Daniel

---

### Post by JuergenF on 2009-09-22
Sounds like you don't want to move your 'installation' but just create a menu entry. Look at [this tutorial]("http://ubuntu-tutorials.com/2008/07/10/edit-the-applications-menu-with-two-clicks-ubuntu-804/")

BTW: even if you are the only user on your system, you IMHO shouldn't put 3rd-party binaries on the Desktop. Create a ~/bin directory for that.
If you want a multiuser install, put it into /usr/local and a link to the executable into /usr/local/bin

---

### Post by dsarfati on 2009-09-22
Great, that's exactly what I wanted! Thanks a lot

---


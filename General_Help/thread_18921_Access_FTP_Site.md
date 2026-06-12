---
title: "Access FTP Site?"
date: 2005-03-09
forum: General Help
---

### Post by Jonathan_ on 2005-03-09
I want to access a site via FTP. When I type in the FTP address it allows me to view the files/folders but I want to be able to edit/add/delete these files. In windows you go File>Log in as...

How do you do this in Linux?

Thanks

---

### Post by lordofkhemenu on 2005-03-09
[QUOTE=Jonathan Steel]I want to access a site via FTP. When I type in the FTP address it allows me to view the files/folders but I want to be able to edit/add/delete these files. In windows you go File>Log in as...

How do you do this in Linux?

Thanks[/QUOTE]
Quick and dirty in Gnome:
[color=SeaGreen]File | Connect to server[/color].
Select '*Custom location*' from the 'Service Type' drop down menu.
Enter [color=Red]ftp://yourusername:password@ftp.whatever.com[/color] in the URL field and connect.
Gnome should create an icon on the desktop for the new connection, As long as you have gnome-vfs installed, any network aware applications (gedit, screem, etc) will show the connection just as if it were a folder on your computer.

For a more permanent solution, create a new launcher on the desktop/where ever and select 'link' as the type. 

Don't forget to right click and 'unmount volume' when your done, if others will be using the computer, etc.

---

### Post by Jonathan_ on 2005-03-10
Thanks alot

---

### Post by lordofkhemenu on 2005-03-10
[QUOTE=Jonathan Steel]Thanks alot[/QUOTE]
No problem. "[Ubuntu]("http://www.ubuntulinux.org/support/documentation/faq/meaning-of-ubuntu/")", yanno?

---


---
title: "How do I change my computer name in Ubuntu 10.04?"
date: 2010-12-15
forum: General Help
---

### Post by bradRNstyle on 2010-12-15
During the installation I just named the computer "linux-pc."  Now I want to change it to something more identifiable on my network, like "joes-linux-deskopt" or something.  Where in Gnome do I fine the area to do this at?

Thanks!

---

### Post by NCLI on 2010-12-15
You need to edit the file /etc/hostname, and /etc/hosts. Press alt+F2, then enter this command:
```
gksudo gedit /etc/hostname
```
Do the same for /etc/hosts, making sure to only change your computer name.

---

### Post by tredegar on 2010-12-15
I don't think you can do this from the GUI, but it is easy from the terminal with the command **sudo hostname ....**

See **man hostname** for the options / details.

I strongly advise you to reboot as soon as you have changed the hostname, this is one of the (few) requirements for linux to reboot. Failure to do this may mean that you cannot login and will need a boot from a live CD (this has happened to me in the past, so I don't change the hostname without good reason).

---

### Post by Megaptera on 2010-12-15
I used the 'Change Host Name' option in Ailurus which has a GUI. Explanation & install guide here [http://www.liberiangeek.net/2010/06/easily-manage-ubuntu-10-04-lucid-lynx-ailurus/](http://www.liberiangeek.net/2010/06/easily-manage-ubuntu-10-04-lucid-lynx-ailurus/)

---

### Post by karthick87 on 2010-12-15
You need to edit the computer name in two files,
```
sudo gedit /etc/hostname
```
```
sudo gedit /etc/hosts
```
Restart your computer, and the name will have  been changed.

---

### Post by ajgreeny on 2010-12-15
> **Megaptera said:**
> I used the 'Change Host Name' option in Ailurus which has a GUI. Explanation & install guide here [http://www.liberiangeek.net/2010/06/easily-manage-ubuntu-10-04-lucid-lynx-ailurus/](http://www.liberiangeek.net/2010/06/easily-manage-ubuntu-10-04-lucid-lynx-ailurus/)
What a complicated way to do something so simple!

Two commands in terminal and two name changes in the files opened, and all is done with no need to download anything.

---

### Post by bradRNstyle on 2010-12-15
Wow, thanks for all the help everyone.  I did end up doing it the GUI way with Ailurus.  Command line is easier, however I love exploring new things, and Ailurus does a lot more than just changing a host name.  Yea Linux!

Thanks!

---

### Post by Megaptera on 2010-12-15
You're welcome!

---

### Post by karthick87 on 2010-12-15
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---


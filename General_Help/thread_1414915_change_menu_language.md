---
title: "change menu language"
date: 2010-02-24
forum: General Help
---

### Post by caslor on 2010-02-24
Hi to all friends here.
i have installed xbuntu 9.10 as my car pc os
when i installed it i choose Greek as default language.
The problem is that some scripts i have found use the english menu and i would like to change all my os menu to english .
i have installed a lot of packages... will efect them this change? 

thanks in  advance

---

### Post by zvacet on 2010-02-24
[Here]("http://xubuntublog.wordpress.com/2007/07/")

---

### Post by caslor on 2010-02-24
Ha ha i just login to write that i find out the solution :)
YES that is what i did and worked fine :)

Thanks for the quick reply my friend :) 

UBUNTU made linux so easy and friendly to new unix-users :) :))

---

### Post by caslor on 2010-02-24
ok i find out that  desktop in  shell is still under greek name   ''epifania ergasias''
How can i change this.. nothing with greek  names..
I dont want to reinstall ubuntu again and all the packages..that will be my last solution

the problem is that i follow this instructions to make a shutdown shortcut 

> create a luncher on the desktop

in terminal:
gedit ~/Desktop/shutdown.desktop
copy and paste this:
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Name[C]=shutdown
Exec=sudo shutdown -P now
Comment[C]=shutdown
Name=shutdown
Comment=shutdown


save the file and exit (Ctrl+s Alt+F4)

in terminal:
sudo visudo
add this line at the end of the file:
your_user_name ALL=NOPASSWD:/sbin/shutdown -P now


where your_user_name is your username
save and exit (Ctrl+o Enter Ctrl+x)

to shutdown double click on the shutdown icon on de desktop

and cant make it work because the different name in desktop.
in my other pc with english installation made it work from the first try

and i think that will have general problem with the greek  name for the desktop in the future if i want to follow instructions for anything else

---


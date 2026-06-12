---
title: "No applications found !! and another questions"
date: 2011-05-20
forum: General Help
---

### Post by evilheart on 2011-05-20
hi , i am new user to linux , i just installed ubuntu natty from windows few days ago , then switched to Xubuntu for better performance with my 512 ram .

now the application menu gives me "No application found" , but i can still open applications from terminal.
and updates are installed.

i tried to add new application menu but still the same , 
there isn't anything odd in "edit menu" , i choosed the default one  but still no applications found.

while running jdowanloader from terminal i noticed that "package manager file " or something like that doesn't exist ,

how can i fix the menu ? or at least how can i install its plugin?

when i switched for linux i was looking for performance and stability of the system on my relatively low spec pc , but Xubuntu freezes and hangs may be more than winXp "i still don't know why", and performance isn't that fast "swap memory 767 , ram 488 , nearly all the windows effects are disabled." , 

ubuntu software center also greatly slows the system when i run it
 
how can i can make Xubuntu faster than that? or at least stop freezing? how to fix ubuntu software center freeze??

---

### Post by linuxinstalledfromhdd on 2011-05-20
I've never been a fan of Xubuntu for this kind of stuff.  Maybe consider trying a better environment for the lower performance you have to work with, like:

sudo apt-get install lxde

That will take some time to install, and then you logout and select "sessions" and switch to LXDE. Login as usual.

---

### Post by evilheart on 2011-05-21
thanks , i tried LXDE , it seems faster than XFCE although a bit with little options.

i found the answer to my problem in this thread [http://ubuntuforums.org/archive/index.php/t-541964.html]("http://ubuntuforums.org/archive/index.php/t-541964.html")

i had to delete the application.menu file in home/.config and the system will use the default one.

---


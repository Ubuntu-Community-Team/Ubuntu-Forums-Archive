---
title: "Gnome3 crashed my Ubuntu :("
date: 2011-05-09
forum: General Help
---

### Post by mac4rfree on 2011-05-09
Hi Guys,
 
I tried to install Gnome3 in my Ubuntu 11.04.
 
Following are the commands i followed.
 
> sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell

 
But after the last command i was getting an error as following
> The following packages have unmet dependencies :

gnome3-session : Depends : gnome-session-bin (< 2.33)  but 3.0.1-0ubuntu1~build2 is to be installed.
                          Depends : gnome-session-common  (=2.32.1-0ubuntu20) but 3.0.1-0ubuntu1~build2 is to be installed.

E: broken packages
So, Now when i tried to reboot. it is not rebooting itself..
 
Now, i tried to login in safe mode and fixed the broken packages. But again, when i logged in, i dont have unity as well as gnome3..
 
Can somebody point me where i am doing wrong.. and What needs to be fixed in order to install gnome3?
 
Cheers!!!!!

---


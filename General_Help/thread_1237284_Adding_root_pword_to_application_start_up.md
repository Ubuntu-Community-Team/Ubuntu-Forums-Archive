---
title: "Adding root p/word to application start up?"
date: 2009-08-11
forum: General Help
---

### Post by VipX1 on 2009-08-11
EtherApe (as root) is to launch when I log in. It ask's for my root password because it's been run as root. _What script_ can I add to _what file_ so as that my root password will be in the application start up automatically? So as that I will not have to type my root password everytime EtherApe (as root) starts.

---

### Post by Barafu Albino Cheetah on 2009-08-11
you can edit your sudo settings 
type ```
visudo
``` and read the comments. Allow yourself to run anything you want without password. 
Just don't run with sudo a gui app not designed for it! Mozilla as an example.

---

### Post by VipX1 on 2009-08-11
"Uncomment to allow members of group sudo to not need a password"
I did uncomment the scipt in question. However, I do not have a group called sudo. Do I just create the sudo group myself in Users Settings? 
At present I am still being asked for the root password at boot up/Log in. I did a full reboot to test.
Thanks for the help by the way..

---


---
title: "fatal no screens found"
date: 2009-12-17
forum: General Help
---

### Post by bigchudds on 2009-12-17
hi guys hope you can help?
i have  two 9600gt graphics cards, sli configuration on my board.
i installed ubuntu with no problems, it was only when i installed nvidia drivers that i can longer get any access to the xserver screen.
i have had messages stating, fatal no screens found, i know it has to have something to do with the xconfig, i did take 1 card out from my system and logged in with no problem.

i hope you can point me in the right direction to configure sli , enable sli configuration..

thanks for any help you can give....

---

### Post by Darael on 2009-12-17
Hmm... if you can temporarily disable the driver (copy out your xorg.conf to a backup and use one specifying the nv driver instead of nvidia?) you should be able to use the NVidia X server setup tool (under system->administration) to configure it. I think!

---

### Post by jmagsho on 2009-12-18
I had the same problem after upgrading to the latest Nvidia driver.  The one in the repositories seems to be broken or at least incompatible with my graphics card.

Needless to say, I was able to load EnvyNG from a terminal window, run it in text mode and get my issue resolved by loading the recommended driver.

Here is what I installed to get EnvyNG working:

sudo apt-get intall envyng-qt envyng-core

---

### Post by bigchudds on 2009-12-18
Thanks for your helps guys solved the problem by inputting these commands,

sudo nvidia-xconfig --multigpu=on
sudo nvidia-xconfig --sli=on

---


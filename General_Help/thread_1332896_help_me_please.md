---
title: "help me please"
date: 2009-11-20
forum: General Help
---

### Post by dabackwoodboy on 2009-11-20
ok ive been trying to install the latest nvidia drivers on my freshly installed Ubuntu laptop and im hitting a brick wall. i am an obsolete noob so please be nice. ive read the guides on sudo commands to gain root access but i cant be doing something right because i keep getting the must be installed in root error i have the (NVIDIA-Linux-x86_64-190.42-pkg2.run) file on my desktop and my login name is (James) can anyone help out im really trying to give Linux a chance but im a lil slow so please please any one help

---

### Post by TheCowGod on 2009-11-20
open a terminal and type:
cd Desktop
chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run

that should work, but I would probably just stick with the drivers that are available from the restricted drivers manager.

---

### Post by theozzlives on 2009-11-20
> **dabackwoodboy said:**
> ok ive been trying to install the latest nvidia drivers on my freshly installed Ubuntu laptop and im hitting a brick wall. i am an obsolete noob so please be nice. ive read the guides on sudo commands to gain root access but i cant be doing something right because i keep getting the must be installed in root error i have the (NVIDIA-Linux-x86_64-190.42-pkg2.run) file on my desktop and my login name is (James) can anyone help out im really trying to give Linux a chance but im a lil slow so please please any one help

Hold down the shift button during boot, it'll take you to a menu. Select recovery mode and after a bunch of text, you'll come to another menu. Choose root prompt, go to the folder with the *.run file is, then do:
```
chmod +x <filename>
./<filename>
```
that should do it.

---

### Post by stonebit on 2009-11-20
If you click on the little green hardware icon in your notification area or goto System > System > Hardware Drivers (or something like that), an app will come up and allow you to auto install the Nvidia drivers from the ubuntu repository. Oh- make sure you have all the ubuntu repositories checked in software sources or the system won't be able to find the driver.

add repositories:
System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Ubuntu_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Ubuntu_Repositories)

add drivers: [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers)

---


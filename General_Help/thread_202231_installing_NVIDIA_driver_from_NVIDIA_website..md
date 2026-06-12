---
title: "installing NVIDIA driver from NVIDIA website."
date: 2006-06-23
forum: General Help
---

### Post by raha on 2006-06-23
Hi

I used to use SUSE all the time but only because of their new update system I decided to move to Ubuntu.

One of the most important things for me is 3D graphic so I tried to install the latest NVIDIA driver but I couldnt find anything that tell me how.

I need their latest drivers not nv or old versions.

How is it possible to do this on Ubuntu. it was such a simple task on SUSE. ](*,) 

Please help.

---

### Post by aysiu on 2006-06-23
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by raha on 2006-06-23
This link doesnt explain anything apart from : 
sudo apt-get install nvidia-glx nvidia-kernel-common

how do i compile the drivers from : [http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/NVIDIA-Linux-x86-1.0-8762-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/NVIDIA-Linux-x86-1.0-8762-pkg1.run)

---

### Post by aysiu on 2006-06-23
Dapper's nvidia-glx is version 1.0.8762 and Nvidia's website's version is 1.0-8762. Looks like the latest to me.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-glx&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-glx&searchon=name&subword=1&version=all&release=all)

---

### Post by raha on 2006-06-23
so, the question is that how can i install that ?
The link you gave me earlier doesnt explain how, i did indeed typed : sudo apt-get install nvidia-glx nvidia-kernel-common   but after a while downloading was finished but nothing happened.

---

### Post by tseliot on 2006-06-23
Read my guide, please:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by aysiu on 2006-06-23
[QUOTE=raha]so, the question is that how can i install that ?
The link you gave me earlier doesnt explain how, i did indeed typed : sudo apt-get install nvidia-glx nvidia-kernel-common   but after a while downloading was finished but nothing happened.[/QUOTE]
Then, I'd say the problem is with your package manager and not Nvidia.

First of all, [make sure you have the proper repositories enabled](http://www.psychocats.net/ubuntu/sources). Then can you post back here the output of these commands? ```
sudo aptitude update
sudo aptitude install nvidia-glx nvidia-kernel-common
```

---

### Post by echo $USER on 2006-06-23
Download the driver you want from Nvidia's site. Run > sudo /etc/init.d/gdm stopLog in to the text interface.  Change to the directory where the driver is, then run > sudo sh NVIDIA*follow the directions to install, then finally > sudo /etc/initd./gdm startDone.  All this can be found at nvidia's web site [http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)

---

### Post by raha on 2006-06-27
Thanks but how can I go out of the Gnome (Non-graphical) mode to install the NVIDIA driver ?

Thanks

---

### Post by Rui Pais on 2006-06-27
[QUOTE=raha]Thanks but how can I go out of the Gnome (Non-graphical) mode to install the NVIDIA driver ?

Thanks[/QUOTE]
hi,
log out gnome.
Press Ctr-Alt+F1 (or F2...F6)
then login on terminal and do:
```
sudo /etc/init.d/gdm stop
```

---

### Post by raha on 2006-06-27
Thanks, I am going to do it now, I hope it will work.

---


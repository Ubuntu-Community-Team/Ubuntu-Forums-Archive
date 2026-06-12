---
title: "Installing nvidia drivers"
date: 2006-05-14
forum: General Help
---

### Post by GhandiBurger on 2006-05-14
I downloaded the current drivers and when I try to install them, I get this message:

 ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).

and then:

ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find
         suggestions on fixing installation problems in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

How do I exit X?

---

### Post by Koybe on 2006-05-14
Press CTRL+ALT+F1, login and type :
sudo init 1
And retry installing.

But there is a package called nvidia-glx with the nvidia drivers ;)

---

### Post by GhandiBurger on 2006-05-14
ooo. Thank you for the nvidia glx package. How do I restart X?

---

### Post by Koybe on 2006-05-15
sudo /etc/init.d/gdm restart or reboot your computer ;)

---

### Post by KillrBuckeye on 2006-05-15
[QUOTE=Koybe]
But there is a package called nvidia-glx with the nvidia drivers ;)[/QUOTE]Unless they have been added within the last few days, the nvidia-glx package does NOT include the latest 8756 nVidia drivers.  I know because my 7900GT is only supported by 8756, and X wouldn't start when the nvidia-glx package was installed.  There are several threads about installing the 8756 drivers, so try searching around.  tseliot has written some scripts that automate the driver installation process, so you may want to give that a try!  If you want to install 8756 and have trouble, post here and I can try to help.

---

### Post by s0cket on 2006-05-15
[QUOTE=KillrBuckeye]Unless they have been added within the last few days, the nvidia-glx package does NOT include the latest 8756 nVidia drivers.  I know because my 7900GT is only supported by 8756, and X wouldn't start when the nvidia-glx package was installed.  There are several threads about installing the 8756 drivers, so try searching around.  tseliot has written some scripts that automate the driver installation process, so you may want to give that a try!  If you want to install 8756 and have trouble, post here and I can try to help.[/QUOTE]

Dapper has packages in the repo for 8756 and Breezy does not.  For whatever reason this confused the poo out of me for a day or two.  I needed Xorg 7 (xgl *cough* *cough*) so I just updated to Dapper.

---

### Post by tseliot on 2006-05-15
My script installs (automaticaly) the latest driver on Breezy and Dapper:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---


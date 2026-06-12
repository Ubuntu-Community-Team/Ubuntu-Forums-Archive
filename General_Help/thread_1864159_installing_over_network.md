---
title: "installing over network"
date: 2011-10-18
forum: General Help
---

### Post by gibson.nathan.2011 on 2011-10-18
hi, i currently use ubuntu. my friend asked me to fix his eee pc that runs windows xp. the system wont boot and i dont have a usb dvd drive or a big enough usb drive to put the boot disc on.

the eee has an option for boot to lan. my question is this, how can i have the disc in my ubuntu machine (wireless laptop) and access it via the eee to do the re-install? that is, assuming it is possible.

thanks for any help, and if you feel you may know a better solution- feel free to share.

---

### Post by blueridgedog on 2011-10-18
You would need a PXE boot server on the LAN with the eee pc.  You can google PXE boot server.  Here is a good link:

[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)

It is a bit complex, not impossible, and a great learning project.

---

### Post by Mark Phelps on 2011-10-18
If you're trying to boot the eee PC from your PC, I don't think that will work.

Found the info below on using the LAN boot option in the eee PC and it requires setting up an nfs server:

[http://codemonkey.org.uk/projects/eeepc/]("http://codemonkey.org.uk/projects/eeepc/")

---

### Post by gibson.nathan.2011 on 2011-10-18
now im really confused. the first method listed i got as far as this " apt-get install netkit-inetd tftpd-hpa dhcp3-server lftp" and i received this error message > You should explicitly select one to install.

E: Package 'netkit-inetd' has no installation candidate


as far as the second method, i dont know where to begin. my knowledge of setting up these sorts of things is limited.

EDIT: also, i am pretty sure i need to use a pxe server as that is one of the options presented in the eee bios.

---

### Post by gibson.nathan.2011 on 2011-10-18
also, is there anyway that i can access the cd drive of my laptop from the eee if i had them connected over an ethernet cord?

---

### Post by gibson.nathan.2011 on 2011-10-18
im running out of ideas, but does anyone know if i can put the recovery software on my ipod touch and use that as a usb drive? i have been searching, but havent found anyone attempting something similar.

---


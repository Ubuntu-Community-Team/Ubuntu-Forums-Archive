---
title: "Problem with the configuration server."
date: 2010-06-17
forum: General Help
---

### Post by kvv_1986 on 2010-06-17
TLDR; I have a problem with ubuntu 10.04, and not able to login. Read last three paragraphs. Thanks.

Hi,

I am some what of a newbie to Ubuntu. 

I am running Dell Studio 15 with Windows Vista, and I am having a problem with my Ubuntu 10.04 installation.

I have a separate ~15 GB partition for Ubuntu and Swap Space. This had 9.10 earlier, where my wireless didn't work, so it was almost completely useless for me. So for a long time, I moved back to Windows Vista. 

Recently, when I tried booting the Ubuntu 9.10, an error appeared which said that my file system could not be mounted. A recovery terminal or something appeared, and I could access the root. But all my personal files had disappeared (naturally, because file system could not be mounted). 

So, yesterday I formatted the 15 GB partition (I had backed up my data long back) and installed Ubuntu 10.04 in it. When I load the OS, a dialog box appears with the message : "There is a problem with the configuration server. /usr/lib/libgconf2-4/gconf-sanity-check exited with status 256".

Then, it takes me to the login screen, where an error message appears on the top right hand corner : "The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact the administrator."

When I try to login, I again get the dialog box as previously : "There is a problem with the configuration server. /usr/lib/libgconf2-4/gconf-sanity-check exited with status 256". Then it goes back to the login screen. The entire process repeats.

Help please.:confused:

Thanks.

---

### Post by linux-hack on 2010-06-17
you'll need to reconfigure your gnome desktop with this 

```
sudo dpkg-reconfigure xserver-xorg
```

and see if it still gives you the same error

---

### Post by kvv_1986 on 2010-06-17
I went to the recovery shell and type the above. Then, I rebooted but it didn't help.

---

### Post by linux-hack on 2010-06-17
> **kvv_1986 said:**
> I went to the recovery shell and type the above. Then, I rebooted but it didn't help.

try doing that with the gnome desktop : 
```

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

```

---


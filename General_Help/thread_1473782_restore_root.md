---
title: "restore root"
date: 2010-05-05
forum: General Help
---

### Post by Jpenguin on 2010-05-05
I was trying to upgrade FGLRX, but the old one wouln't uninstall.  I think I need to reintall Lucid.  Since I have seperate partitions for:: /, /urs, /boot, /boot & swap.  Can I ujust reinstall root?  I'm downloading 'ubuntu-10.04-desktop-amd64.iso' via torrent now

---

### Post by quadproc on 2010-05-05
> **Jpenguin said:**
> I was trying to upgrade FGLRX, but the old one wouln't uninstall.  I think I need to reintall Lucid.  Since I have seperate partitions for:: /, /urs, /boot, /boot & swap.  Can I ujust reinstall root?  I'm downloading 'ubuntu-10.04-desktop-amd64.iso' via torrent now
I am not sure what you mean by "reinstall root" so I will just say that you should be able to use sudo to get the necessary privilege.

If your fglrx was installed the usual way then you will find an uninstall file on your system.  Run it by doing this:
```
cd /usr/share/ati
sudo sh fglrx-uninstall.sh
```and furnish your password when it asks.

Note: I have found that the ATI install script can put duplicate entries into your xorg.conf file.  Therefore, if you have trouble with the new installation then check the xorg.conf file and fix it up if necessary.

quadproc

---

### Post by Jpenguin on 2010-05-05
> **quadproc said:**
> I am not sure what you mean by "reinstall root" so I will just say that you should be able to use sudo to get the necessary privilege.

If your fglrx was installed the usual way then you will find an uninstall file on your system.  Run it by doing this:
```
cd /usr/share/ati
sudo sh fglrx-uninstall.sh
```and furnish your password when it asks.

Note: I have found that the ATI install script can put duplicate entries into your xorg.conf file.  Therefore, if you have trouble with the new installation then check the xorg.conf file and fix it up if necessary.

quadproc


I meant, reinstall all files on the root partition.

ON karmoc, I created *.debs from FGLRX 9-12.  I upgraded to lucid aand now I want to uninstall, so I exited X and did 'sudo apt-get remove fglrx' butt it exited with a stattus of 1 (err)

I do have a backup of /home on another drive (just-in-case)

---

### Post by QIII on 2010-05-05
If you reinstall, when you get to the partition section, you can select  not to reformat whichever partitions you do not want to reformat.  But I  don't know what you have there or how it might inter-relate with other  things, so it would be hard for me to recommend whether or not you  should do that.
  
  As for installing the ATI driver when you get done, doing it via  Synaptic rather than from the AMD/ATI website would probably be much  easier.  The latest driver (10.4) and the Catalyst Control Center are  available  in the repos.  AMD/ATI has been making a habit of releasing their  latest drivers just in time to hit the Ubuntu repos at every new release  and making everyone else wait.

---


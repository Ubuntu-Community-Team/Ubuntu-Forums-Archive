---
title: "Series of issues in Ubuntu 10.04"
date: 2010-06-02
forum: General Help
---

### Post by Malkavie on 2010-06-02
Hi everyone,

Yeah, well I've experienced a series of issues since my last system restore, I used to have Win XP but I switched to Ubuntu 9.10 and I really liked it so, as soon as Lucid came out I copied to a CD to do a fresh install and everything went right until a week ago when I started with my issues and none has been able to solve, I have a couple of posts in some other forums but with no success, hope you guys can help me with this.

This is a fresh install of Ubuntu 10.04 performed a week ago and everything was working fine but these three issues, I do not have any programs installed but the ones that came with Lucid Lynx, I have not added any new repository, nothing, I installed my OS and use it, it is not even customized as I've been working a lot and have had no time to do it, I'm the only user of this computer.

1. Right after the install I had access to my folders from the Places menu, then, all the sudden I lost that access to Home Folder, Desktop, Documents, Music, Pictures and Downloads, I get the following error message "Could not open location file:///home/itzyolotl, no application is registered to handle as handling this file" so I do not have access to this folders, as I said this happened all the sudden as it was working fine a few days ago.

2. Everytime I reboot my system I loose the visual effects and the borders for my windows, so everytime I start my computer I have to go to System>Preferences>Appearance in order to activate them, again, this started to happen all the sudden as it used to work fine. This may be due to my graphic card, it is a Nvidia wich leads to another issue.

3. Every time I try to install and activate my graph card driver I get this message "SystemError: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-22_2.6.32-22.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-22_2.6.32-22.33_all.deb) Connection failed [IP: 91.189.88.30 80]" and it is not possible to download and activate my driver

4. I cannot update my system, there is no way to download certain files from the server, I've tried several servers all around the world and I can't download the same files, I've tried to go to the server main page "http://us.archive.ubuntu.com/ubuntu/lucid-updates/main" to manually download and install the files but the files are not in there. This happens when I type 'sudo apt-get update', 'sudo aptitude update', 'sudo aptitude safe-upgrade' and from the update manager, my systems fails to fetch due to a failed connection to [IP: 91.189.88.45 80] the following files:

failed apt -                 apt 0.7.25.3ubuntu9
failed libgtk2.0-common -         libgtk2.0-common 2.20.1-0ubuntu1
failed libgnome-window-settings1     libgnome-window-settings1 1:2.30.1-0ubuntu1
failed librsvg2-2 -            librsvg2-2 2.26.3-0ubuntu1
failed libsoup2.4-1 -            libsoup2.4-1 2.30.1-0ubuntu1
failed libevview2 -            libevview2 2.30.1-0ubuntu3
failed libgcr0 -            libgcr0 2.92.92.is.2.30.1-0ubuntu1
failed libgl1-mesa-glx            libgl1-mesa-glx 7.7.1-1ubuntu3
failed grub-common -            grub-common 1.98-1ubuntu6
failed gvfs -                gvfs 1.6.1-0ubuntu1build1
failed libhal-storage1 -        libhal-storage1 0.5.14-0ubuntu6
failed indicator-applet-session        indicator-applet-session 0.3.7-0ubuntu1
failed indicator-applet            indicator-applet 0.3.7-0ubuntu1
failed libpam-gnome-keyring        libpam-gnome-keyring 2.92.92.is.2.30.1-0ubuntu1
failed linux-headers-2.6.32-22        linux-headers-2.6.32-22 2.6.32-22.33
failed nautilus                nautilus 1:2.30.1-0ubuntu1
failed pm-utils                pm-utils 1.3.0-1ubuntu2
failed totem-plugins            totem-plugins 2.30.2-0ubuntu1
failed totem-mozilla            totem-mozilla 2.30.2-0ubuntu1

And the update manager has issues finding the Translation-en_US files, and all the ones listed above.

I'm not an expert user, I'm a very new unexperienced user (remember I started using  a linux Distro on February this year) which means I request absolute begginer talk, this are the specs of my computer:

AMD 64 Dual core processor 2.6GHz 
2 Gb memory card
120 Gb Seagate hard drive
512 Mb GeForce 8400 GS graphic card

Need anything else?

Thanks in advance guys, hope you can help me before I give up, I do not want to go back to MS Windows [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]  but, unfortunately it seems to be the only way to get my computer working as I want  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG](hope not) specially my graphic card, it was a bit expensive so I want it to work perfectly.

Malk

---

### Post by dino99 on 2010-06-02
use the main server for updating (remove us.)

gksu gedit /etc/apt/sources.list

---


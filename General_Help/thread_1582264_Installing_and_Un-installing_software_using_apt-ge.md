---
title: "Installing and Un-installing software using apt-get"
date: 2010-09-26
forum: General Help
---

### Post by sim085 on 2010-09-26
Hello, I am using ubuntu-server (10.04) as a virtual machine on VirtualBox. I have used sude apt-get install xubuntu-desktop to download the xubuntu graphical user interface on the freesh installation of ubuntu server. This worked fine and then I decided to un-install it. To do this I used the command sude apt-get remove xubuntu-desktop and then afterwards I used the command sudo apt-get autoremove. After I did these commands I do not get the gui anymore (which is good). However I noticed that the file size of the .vdi file did not decrease by much. Before I installed the gui it was arround 700MB, after it was more then 2GB, and after I un-installed the gui it is still over 2GB. Therefore I was wondering; does sudo apt-get remove <package name> really remove every file that has been downloaded and installed for that package?

---

### Post by pbrane on 2010-09-26
when apt-get downloads files for installation it caches them. You probably need to **sudo apt-get clean** to remove the downloaded packages.

**man apt-get** will explain the options to apt-get

---

### Post by ilovelinux33467 on 2010-09-26
Try this to remove xubuntu:

```
sudo apt-get remove a2ps abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview app-install-data-commercial aumix aumix-common catfish exaile exo-utils fortune-mod fortunes-min gigolo gimp gimp-data gnumeric gnumeric-common gnumeric-doc gtk2-engines-xfce libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libbabl-0.0-0 libexo-0.3-0 libexo-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0 libgimp2.0 libgoffice-0.8-8 libgoffice-0.8-8-common libgtkmathview0c2a libjpeg-progs liblink-grammar4 libmng1 libotr2 libots0 libpsiconv6 librecode0 libscim8c2a libsdl1.2debian-alsa libsexy2 libt1-5 libtagc0 libthunar-vfs-1-2 libwv-1.2-3 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad murrine-themes orage oss-compat pidgin pidgin-data pidgin-libnotify pidgin-otr psutils python-cddb python-mmkeys python-mutagen python-sexy ristretto scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird ttf-lyx usb-creator vim-runtime wdiff xchat xchat-common xfce-keyboard-shortcuts xfce4-appfinder xfce4-clipman xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xscreensaver xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme xubuntu-icon-theme xubuntu-plymouth-theme xubuntu-wallpapers
```

Taken from:
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---


---
title: "stupid question login logo help"
date: 2010-06-07
forum: General Help
---

### Post by 2ndconfused1 on 2010-06-07
I accidentally erased the last question I typed so I'll cut to the chase.  I have accidentally installed xfce to be the main login manager, I switched it back but the xfce icon is still over the login user name part I'm a perfectionist and I cant stand it, I already fixed the boot screen to be default again.  But "/usr/share/Icons/LoginIcons/apps/64/computer.svg" is no-longer the default icon and I don't know how to change it back to the said icon.  any help would be appreciated.  I did search for this and thats how I found the regular default icon.  

thx for your help anyone, sorry for long post

---

### Post by SlidingHorn on 2010-06-07
try using:

```
sudo dpkg-reconfigure gdm
```

that should allow you to choose gdm (gnome's default) as the login manager instead

---

### Post by 2ndconfused1 on 2010-06-07
this is what i got sorry but im not good with dpkg

     Code:
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more'

---

### Post by SlidingHorn on 2010-06-07
I'm sorry, I added a space edited the code above

---

### Post by 2ndconfused1 on 2010-06-07
I'm afraid that i was already using gdm so that did not help me. thank-you anyway, I noted that there was no xfce as a manager in the list, so I assume it has something to do with xfce as a desktop environment (this began after I installed it)
(the edited command worked by the way thx)
I am going to try something, will get back if it works

i went into Ubuntu Software Center and found "xubuntu-gdm-theme" installed so i think this is it.
it was that but now i have a computer as the icon... i dont know how to fix this there is no default gdm theme thingy like there was for xfce in the Ubuntu Software Center...

*to myself: i cant believe i made a topic over this....

---

### Post by SlidingHorn on 2010-06-07
well, if you no longer plan on using xfce, you can get rid of xubuntu's packages

```
sudo apt-get remove a2ps abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview app-install-data-commercial aumix aumix-common catfish exaile exo-utils fortune-mod fortunes-min gigolo gimp gimp-data gnumeric gnumeric-common gnumeric-doc gtk2-engines-xfce libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libbabl-0.0-0 libexo-0.3-0 libexo-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0 libgimp2.0 libgoffice-0.8-8 libgoffice-0.8-8-common libgtkmathview0c2a libjpeg-progs liblink-grammar4 libmng1 libotr2 libots0 libpsiconv6 librecode0 libscim8c2a libsdl1.2debian-alsa libsexy2 libt1-5 libtagc0 libthunar-vfs-1-2 libwv-1.2-3 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad murrine-themes orage oss-compat pidgin pidgin-data pidgin-libnotify pidgin-otr psutils python-cddb python-mmkeys python-mutagen python-sexy ristretto scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird ttf-lyx usb-creator vim-runtime wdiff xchat xchat-common xfce-keyboard-shortcuts xfce4-appfinder xfce4-clipman xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xscreensaver xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme xubuntu-icon-theme xubuntu-plymouth-theme xubuntu-wallpapers && sudo apt-get install ubuntu-desktop 
```

---

### Post by 2ndconfused1 on 2010-06-07
i edited my post above about that, yea i was doing that but through the software center, your way might be easier
wow did you memorize that list?

I'm at a loss, I don't know how to change my icon back now, i guess i have to live with it now. unless it is part of a theme, i changed the background of the login and also messed around with the theme on accident so it might be related to that. (i hope it is)

---

### Post by 2ndconfused1 on 2010-06-08
i have fixed the problem. what i did was change my login theme with this
code:
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**mv**[/COLOR] ~[COLOR=#000000]**/**[/COLOR]your-wallpaper-name.jpg [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]backgrounds

loged out and changed the theme back to ambiance and then went into the icons section of the theme and selected "LoginIcons"
at which point the icon returned to normal. i logged back in and used this 
code:
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**cp**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]applications[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktop [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow

to prevent the theme selection window to appear upon logout/reboot.

that is how i got my login theme to go back to normal.

thanks to SlidingHorn__for the help. even if it didnt help directly he reminded me of the terminal so that i could use the above commands to solve the problem.

im tired so i care less about my spelling/grammar XD

---

### Post by SlidingHorn on 2010-06-08
Glad you got it worked out...

I didn't memorize that list -- I stole it!  lol here's the link: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---


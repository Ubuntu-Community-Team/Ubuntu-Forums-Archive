---
title: "removing software"
date: 2009-12-09
forum: General Help
---

### Post by Achilles124 on 2009-12-09
I want gufw removed from my system because it starts from startup. And it is there that I have problems.

So I type:
***sudo apt-get remove gufw***

But that still leaves some files in the system

I try again. This time by typing
***sudo apt-get remove --purge gufw***

But then I type ***sudo locate gufw*** and I get this list:
/etc/gufw
/etc/gufw/gufw.cfg
/home/ecmpeek/.config/autostart/gufw.desktop
/home/ecmpeek/.mozilla/firefox/9ysdvgfm.default/ScrapBook/data/20091121084402/gufw@20ufw@20uncomplicated@20firewall@20screenshot@20ubuntu.png
/usr/bin/gufw
/usr/share/gufw
/usr/share/app-install/desktop/gufw.desktop
/usr/share/app-install/icons/_usr_share_icons_hicolor_48x48_apps_gufw_menu.png
/usr/share/applications/gufw.desktop
/usr/share/doc/gufw
/usr/share/icons/hicolor/48x48/apps/gufw_menu.png
/usr/share/lintian/overrides/gufw
/usr/share/locale-langpack/fr/LC_MESSAGES/gufw.mo
/usr/share/locale-langpack/nl/LC_MESSAGES/gufw.mo
/usr/share/man/man8/gufw.8.gz
/usr/share/menu/gufw
/usr/share/pixmaps/gufw
/usr/share/python-support/gufw.private
/var/lib/gufw
/var/lib/dpkg/info/gufw.conffiles
/var/lib/dpkg/info/gufw.list
/var/lib/dpkg/info/gufw.md5sums
/var/lib/dpkg/info/gufw.postinst
/var/lib/dpkg/info/gufw.postrm
/var/lib/dpkg/info/gufw.prerm
/var/lib/gufw/cfg_files
/var/lib/gufw/cfg_files/gufw.cfg_backup
/var/log/gufw_log.txt

And that pisses me off. I purged it, didn't I? But it is all there.
How can I remove everything of Gufw?

---

### Post by sliketymo on 2009-12-09
gufw is the GUI front-end for ufw.Open a terminal,and type "ufw" without the quotes.You can disable the firwall by doing:"sudo ufw disable". I don't beleive you can completely remove ufw.

---

### Post by FXEF on 2009-12-09
You might try **sudo apt-get clean** and **sudo apt-get autoclean**.

---

### Post by Achilles124 on 2009-12-09
I removed gufw with Synaptic manager (complete removal) and that works better.

There are still some files left though:
```
/home/ecmpeek/.config/autostart/gufw.desktop
/home/ecmpeek/.mozilla/firefox/9ysdvgfm.default/ScrapBook/data/20091121084402/gufw@20ufw@20uncomplicated@20firewall@20screenshot@20ubuntu.png
/usr/share/app-install/desktop/gufw.desktop
/usr/share/app-install/icons/_usr_share_icons_hicolor_48x48_apps_gufw_menu.png
/var/cache/apt/archives/gufw_9.10.4-0ubuntu1_all.deb
/var/lib/gufw
/var/lib/gufw/cfg_files
/var/lib/gufw/cfg_files/gufw.cfg_backup
/var/log/gufw_log.txt
```

Incredible but true. It is simply impossible to completely remove gufw from my computer.

```
Sudo rm /home/ecmpeek/.config/autostart/gufw.desktop

```
gives: file doesn't exist. ??????????? It is there, isn't it.

---

### Post by Achilles124 on 2009-12-09
btw, tried 

```
sudo apt-get clean
```

and the ```
sudo apt-get autoclean
```

They don't have any results.

---

### Post by Cheesemill on 2009-12-09
> **Achilles124 said:**
> I removed gufw with Synaptic manager (complete removal) and that works better.

There are still some files left though:
```
/home/ecmpeek/.config/autostart/gufw.desktop
/home/ecmpeek/.mozilla/firefox/9ysdvgfm.default/ScrapBook/data/20091121084402/gufw@20ufw@20uncomplicated@20firewall@20screenshot@20ubuntu.png
/usr/share/app-install/desktop/gufw.desktop
/usr/share/app-install/icons/_usr_share_icons_hicolor_48x48_apps_gufw_menu.png
/var/cache/apt/archives/gufw_9.10.4-0ubuntu1_all.deb
/var/lib/gufw
/var/lib/gufw/cfg_files
/var/lib/gufw/cfg_files/gufw.cfg_backup
/var/log/gufw_log.txt
```Incredible but true. It is simply impossible to completely remove gufw from my computer.

```
Sudo rm /home/ecmpeek/.config/autostart/gufw.desktop

```gives: file doesn't exist. ??????????? It is there, isn't it.

Are you using locate to find these files?
Locate doesn't perform a 'live' search, it uses a database which only gets updated once every 24 hours. This is why it's reporting files that are no longer there. You can force a refresh by using the following command:
```
sudo updatedb
```

---

### Post by Achilles124 on 2009-12-10
Yes, you are completely right. Forgotten all about it. Happened to me before.
Updated it and there were some files left but these were just logfiles.
Thank you for answering the question.
:)

---


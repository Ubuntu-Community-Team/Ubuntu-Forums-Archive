---
title: "Won't login after nautilus removed"
date: 2011-02-08
forum: General Help
---

### Post by SBushell on 2011-02-08
I been using Ubuntu (now 10.10) for some time, but I am still quite a n00b, so please excuse me if this question seems elementary.

I removed Nautilus long ago in favour of using Dolphin. Since that time, almost every update has cause issues of Nautilus opening at startup. Removing Nautilus again has never given me a problem (I usually run huge long script I found on the net that replaces it with Thunar) This time I ran ' sudo apt-get uninstall nautilus '. Now when I start up it comes to the login screen, I type my password, the screen flashes and the login screen comes back up... no error message just an endless loop of logins.

Is there any hope?

Thanks in advance for any suggestion.

---

### Post by ajgreeny on 2011-02-08
Gnome uses nautilus to produce the desktop you see, so I am surprised you have not had problems removing it before.

I would be interested to see the shell script you found, and exactly what it does, as presumably it must have replaced nautilus with thunar for the desktop.  I suspect it would have been safer to leave nautilus on the machine and just change the default file manager to open folders with thunar by opening nautilus, right clicking on a folder and choosing **Open with -other appliaction** and setting thunar as the chosen one.

The only other way I know of which used to work was this shell script
```
#!/bin/bash
echo '
Making sure Thunar is installed
'
sudo aptitude update
sudo aptitude install thunar
echo '
Downloading new .desktop files
'
mkdir temp
cd temp
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus-computer.desktop
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus.desktop
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus-folder-handler.desktop
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus-home.desktop
sudo chown root:root *.desktop
echo '
Making backup copies of old .desktop files
'
sudo cp /usr/share/applications/nautilus-computer.desktop /usr/share/applications/nautilus-computer.desktop.backup
sudo cp /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus.desktop.backup
sudo cp /usr/share/applications/nautilus-folder-handler.desktop /usr/share/applications/nautilus-folder-handler.desktop.backup
sudo cp /usr/share/applications/nautilus-home.desktop /usr/share/applications/nautilus-home.desktop.backup
echo '
Replacing old .desktop files with new .desktop files
'
sudo mv nautilus-computer.desktop /usr/share/applications/nautilus-computer.desktop
sudo mv nautilus.desktop /usr/share/applications/nautilus.desktop
sudo mv nautilus-folder-handler.desktop /usr/share/applications/nautilus-folder-handler.desktop
sudo mv nautilus-home.desktop /usr/share/applications/nautilus-home.desktop
cd ..
rmdir temp
echo 'Thunar should now be your new default file manager in Gnome'

```

---

### Post by SBushell on 2011-02-09
I am sorry, I guess all this time I've just been disabling nautilus, that is the script I used a couple times, this time though it looks like I completely removed nautilus. I was able to reinstall it using apt-get install nautilus. I also thought maybe thunar was causing a problem so I removed it but it is still giving me the same problems.

---

### Post by ajgreeny on 2011-02-09
Have you also seen the restorenautilus.sh shell script, which is attached?

---


---
title: "editing menu"
date: 2012-08-10
forum: General Help
---

### Post by GregoryF on 2012-08-10
In Lubuntu, I am trying to make KOL Mafia launch from the menu under games. I used root privleges to create the following file ( /usr/share/applications/KOLMafia.desktop)

[Desktop Entry]
Exec=/home/greg/KoLmafia-15.4.jar
Icon=/home/greg/myicons/kolmafia.png
Type=Application
Terminal=false
Name=KOLMafia
GenericName=KOLMafia
StartupNotify=false
Categories=Game

I made sure that the KoLmafia jar file was in the correct location, that it has permission to run as executeable, and set to run with openjdk java6 runtime. I also put a .png in the location specified.  Then I used "lxpanelctl restart". Now when I go to menu->games I see the icon with KolMafia next to it listed in the menu, but when I click on it, nothing happens. I tried running it without going through the menu->games and it worked great, but I would still like it to work on the menu. Any ideas where I may have gone wrong?
PS I just started using Lubuntu today, so extra explanation would be nice.

---

### Post by ajgreeny on 2012-08-10
I think your ```
Exec=/home/greg/KoLmafia-15.4.jar
``` line in the launcher file needs to be ```
Exec=java -jar /home/greg/KoLmafia-15.4.jar
``` This is needed in the menu and, for example, in the startup-applications list to tell the system what to use to run the file.

---

### Post by GregoryF on 2012-08-10
I see, just like launching it from the terminal. I changed it, and it works now. Thanks!

---


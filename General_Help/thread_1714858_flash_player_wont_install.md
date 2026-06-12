---
title: "flash player wont install"
date: 2011-03-26
forum: General Help
---

### Post by claire14 on 2011-03-26
hi  i lost flash player when i uninstalled wine and flash wont reinstall 
does anyone know how to fix it , i'm on ubuntu 10.10 64 bit laptop   , thank you if you can help  :)

---

### Post by MooPi on 2011-03-26
Go to Adobe flash player download page [http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.2_for_Linux_(.tar.gz)]("http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.2_for_Linux_(.tar.gz)") and download the install_flash_player_10_linux.tar.gz
Extract the contents (libflashplayer.so )and copy to ```
~/.mozilla/plugins
``` If you are using Chromium-browser open a terminal and ```
sudo cp libflashplayer.so /usr/lib/chromium-browser/plugins/
```
That should update your flash player properly.

---

### Post by lovinglinux on 2011-03-26
> **claire14 said:**
> hi  i lost flash player when i uninstalled wine and flash wont reinstall 
does anyone know how to fix it , i'm on ubuntu 10.10 64 bit laptop   , thnak you if you can help  :)

Get [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") extension for Firefox. It will install the latest beta flash version for you, according to your system architecture, will remove potentially conflicting plugins and apply some performance tweaks.

BTW, does your flash player installer file name ends with ".exe"?

---

### Post by claire14 on 2011-03-26
> **lovinglinux said:**
> Get [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") extension for Firefox. It will install the latest beta flash version for you, according to your system architecture, will remove potentially conflicting plugins and apply some performance tweaks.

BTW, does your flash player installer file name ends with ".exe"?

hi thankyou  , Flash-Aid fixed it , the files were the linux ones and none of them would install manually or through the ubuntu software centre , i installed them before , it said wrong architecture on the software centre install . all my players are back soooo its ok now and flash-aid is kooool , thankyou again  :)

---

### Post by lovinglinux on 2011-03-27
> **claire14 said:**
> hi thankyou  , Flash-Aid fixed it , the files were the linux ones and none of them would install manually or through the ubuntu software centre , i installed them before , it said wrong architecture on the software centre install . all my players are back soooo its ok now and flash-aid is kooool , thankyou again  :)

You are welcome.

---


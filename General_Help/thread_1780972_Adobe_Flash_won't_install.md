---
title: "Adobe Flash won't install"
date: 2011-06-12
forum: General Help
---

### Post by ebilbrough on 2011-06-12
I'm running Ubuntu 8.04 on a Dell Mini.

Last week I ran the update that was available and now sites that require Adobe Flash won't run and request an install.

I've searched the forums and tried several methods but can't seem to get Adobe Flash loaded.

Any help is greatly appreciated.

---

### Post by ivanovnegro on 2011-06-12
Oh man, this is an ancient system, maybe its not compatible with the newest Flash, if you install from repositories, your version reached end of life, no updates, so no newer Flash.

You might consider upgrade your system to 10.04 LTS or newer.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
```
mkdir ~/.mozilla/plugins
cd ~/.mozilla/plugins
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz 
tar -zxvf install_flash_player_10_linux.tar.gz
rm install_flash_player_10_linux.tar.gz
```assuming you are using 32bit

---

### Post by ebilbrough on 2011-06-12
pqwoerituytrueiwoq - many thanks, that worked.

I find it very frustrating when these updates about half the time cause more problems after their install.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
no problem manual flash install is not hard if you know a little about firefox's innards you probably should update the next lts if the reason you are not update is missing features the latest xubuntu has plenty of options

---


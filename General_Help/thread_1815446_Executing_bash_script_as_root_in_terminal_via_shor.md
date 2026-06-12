---
title: "Executing bash script as root in terminal via shortcut in Main Menu"
date: 2011-07-31
forum: General Help
---

### Post by spiralciric on 2011-07-31
Ok, this is the problem. I wrote bash script that uses zenity and a choice to install various programs, tested it and it works, but only when I call it from terminal. I wanted to add it in gnome main menu. The script is /home/eee/zenity.sh. In accessories I added an entry with command: ```
/home/eee/zenity.sh
```, but since there is no terminal it starts zenity, but it does not work. I have also tried ```
gksu gnome-terminal -x /home/eee/zenity.sh
``` and ```
gksu gnome-terminal -e /home/eee/zenity.sh
``` but that does not even start a terminal at all. Ok, so I dropped gksu and tried ```
gnome-terminal -e /home/eee/zenity.sh
``` that starts the terminal but when I come to the last step, it just exits the terminal without installing anything. Well, here is the code of the bash script I am using. I would appreciate any help.

```
#!/bin/bash

zenity --info \
--text="You will be presented with various cathegories of software with the most popular choices in each cathegory. \n Choose to install one or more apps in each list or live it blank. 11 lists await you..."

ans1=$(zenity  --list  --text "Chose web browser(s):" --checklist  --column "Pick" --column "options" TRUE "firefox" FALSE "google-chrome-stable" FALSE "chromium-browser" FALSE "midori" FALSE "icecat" FALSE "epiphany-browser" FALSE "swiftfox-i686" FALSE "opera" --separator=" "); echo $ans1 >> /home/eee/choice.txt

ans2=$(zenity  --list  --text "Chose audio player(s):" --checklist  --column "Pick" --column "options" TRUE "rhythmbox" FALSE "amarok" FALSE "audacity" FALSE "exaile" FALSE "xmms2" FALSE "banshee" --separator=" "); echo $ans2 >> /home/eee/choice.txt

ans3=$(zenity  --list  --text "Chose video player(s):" --checklist  --column "Pick" --column "options" TRUE "vlc" FALSE "totem" FALSE "mplayer" FALSE "smplayer" FALSE "kmplayer" FALSE "kaffeine" --separator=" "); echo $ans3 >> /home/eee/choice.txt

ans4=$(zenity  --list  --text "Chose Two-Panel file manager(s):" --checklist  --column "Pick" --column "options" TRUE "gnome-commander" FALSE "krusader" FALSE "bsc" FALSE "tuxcmd" FALSE "mc" --separator=" "); echo $ans4 >> /home/eee/choice.txt

ans5=$(zenity  --list  --text "Chose IM & VoIP software:" --checklist  --column "Pick" --column "options" TRUE "empathy" FALSE "pidgin" FALSE "gwibber" FALSE "emesene" FALSE "skype" --separator=" "); echo $ans5 >> /home/eee/choice.txt

ans6=$(zenity  --list  --text "Chose Cloud storage(s):" --checklist  --column "Pick" --column "options" TRUE "ubuntuone-client-gnome" FALSE "nautilus-dropbox" --separator=" "); echo $ans6 >> /home/eee/choice.txt

ans7=$(zenity  --list  --text "Chose Office Suite(s):" --checklist  --column "Pick" --column "options" TRUE "gnome-office" FALSE "libreoffice" FALSE "openoffice.org" FALSE "koffice" --separator=" "); echo $ans7 >> /home/eee/choice.txt

ans8=$(zenity  --list  --text "Chose Games and Emulators:" --checklist  --column "Pick" --column "options" FALSE "zsnes" FALSE "gmameui" FALSE "gens" FALSE "gnome-gammes" FALSE "playonlinux" --separator=" "); echo $ans8 >> /home/eee/choice.txt

ans9=$(zenity  --list  --text "Enable system preferences:" --checklist  --column "Pick" --column "options" FALSE "cups" FALSE "bluez" FALSE "smbclient" FALSE "brltty" FALSE "xsane" --separator=" "); echo $ans9 >> /home/eee/choice.txt

ans10=$(zenity  --list  --text "Chose among other popular apps:" --checklist  --column "Pick" --column "options" FALSE "gimp" FALSE "pitivi" FALSE "shotwell" FALSE "tuxpaint" FALSE "gpaint" FALSE "audacity" FALSE "cheese" FALSE "transmission-gtk" FALSE "googleearth-package" --separator=" "); echo $ans10 >> /home/eee/choice.txt

ans11=$(zenity  --list  --text "Chose among email apps:" --checklist  --column "Pick" --column "options" TRUE "thunderbird" FALSE "claws-mail" FALSE "evolution" FALSE "kmail" FALSE "seamonkey-mailnews" --separator=" "); echo $ans11 >> /home/eee/choice.txt

zenity --question \
--text="Are you sure you wish to proceed? You chose to install: \n $ans1 $ans2 $ans3 $ans4 $ans5 $ans6 $ans7 $ans8 $ans9 $ans10 $ans11"

apt-get install $ans1 $ans2 $ans3 $ans4 $ans5 $ans6 $ans7 $ans8 $ans9 $ans10 $ans11

```

---

### Post by tredegar on 2011-07-31
Try:
gksu apt-get install $ans1 .....
as your last step.

---

### Post by spiralciric on 2011-07-31
Great idea, it almost works. Now the installer starts, it gets to "After this operation, X MB of additional disk space will be used. Do you want to continue [Y/n]"
I type in Y, but that is the place where it hangs and no package gets installed.
Also the strange thing, when I chose only Thunderbird, it did install it without asking me that question.

---

### Post by tredegar on 2011-07-31
**man apt-get** :```
  -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable
           situation, such as changing a held package, trying to install a unauthenticated package or removing an essential
           package occurs then apt-get will abort. Configuration Item: APT::Get::Assume-Yes.

```

---

### Post by spiralciric on 2011-07-31
Interesting, I tried that with gksu but it did not work. When I put sudo instead, -y option works. I cannot tell why, but I am just glad this is solved. Thanks for your help!

---


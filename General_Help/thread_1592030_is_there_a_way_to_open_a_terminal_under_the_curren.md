---
title: "is there a way to open a terminal under the current directory your in?"
date: 2010-10-10
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-10
So for example, I go to PLACES -> DOWNLOADS and somehow open up a terminal for that rather than opening up a terminal to type "cd ~/Downloads"

I know its simple to do that but when your dealing with some crazy directory like:

/media/2TB-DATA/BackUps/Regular/Downloads/Pictures/Family/Me/HiDef/ 

or something, and ur already browsing through it using the file browser, it would be nice to be able to open up a terminal for that directory.

---

### Post by inameiname on 2010-10-10
[FONT=Arial][SIZE=3]sudo apt-get install nautilus-open-terminal[FONT=Verdana]
[/FONT]nautilus -q #restarts nautilus

It will add a context menu option for nautilus, so whenever you wish to open a terminal, just right click and select it, and it will open a terminal in the folder you are in.

There is a new invention, a terminal that can be installed which is embedded inside nautilus, and that can be installed by:

sudo add-apt-repository ppa:flozz/flozz
sudo apt-get update
sudo apt-get install nautilus-terminal
nautilus -q #restarts nautilus[/SIZE][/FONT]
[FONT=Arial][SIZE=3] 
Another option is if you are using Maverick, and nautilus-elementary, as the latest version of nautilus-elementary has a built-in terminal (based on flozz's work) that makes it even easier to open a terminal in the current directory.

[/SIZE][/FONT] [FONT=Arial][SIZE=3]sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update && sudo apt-get upgrade
nautilus -q #restarts nautilus[/SIZE][/FONT]

---

### Post by SeijiSensei on 2010-10-10
In KDE Dolphin, you can do this by hitting the "F4" key.  I think it works the same way in Nautilus.

---

### Post by formaldehyde_spoon on 2010-10-10
> **SeijiSensei said:**
> In KDE Dolphin, you can do this by hitting the "F4" key.  I think it works the same way in Nautilus.
No, unfortunately.  Just tried.

I always install both the packages inameiname mentions.  Very handy.

---

### Post by irv on 2010-10-10
Here is a bash scrip to do this. I put it in my .gnome2/nautilus-scripts directory under my user.
> #!/bin/bash
#########################################################
#                            #
# This are NScripts v3.4                #
#                            #
# Licensed under the GNU GENERAL PUBLIC LICENSE 3    #
#                            #
# Copyright 2007 - 2008 Christopher Bratusek        #
#                            #
#########################################################

if [[ -x /usr/bin/gksu || -x /opt/gnome/bin/gksu ]]; then
    sudotool=gksu
elif [[ -x /usr/bin/gnomesu || -x /opt/gnome/bin/gnomesu ]]; then
    sudotool=gnomesu
fi

wdir=$(echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed -e 's/file:\/\///g' -e 's/\%20/\\ /g')

$sudotool "gnome-terminal --working-directory=\"$wdir\"" 

---

### Post by irv on 2010-10-10
By the way I have all these scripts on my server for download. Here is a link: [http://wabasha-server.net/Nautilus%20Scripts/]("http://wabasha-server.net/Nautilus%20Scripts/")
Here is where you put them: home/user-name/.gnome2/nautilus-scripts. Here is what my directory looks like:
[ATTACH]171849[/ATTACH]

---

### Post by nothingspecial on 2010-10-10
Cheers, thanks for sharing :)

---


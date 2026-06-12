---
title: "game installation"
date: 2009-11-11
forum: General Help
---

### Post by EnioG on 2009-11-11
Hi anyone plzzzzzzzz help!

I was trying to install Enemy territory on my karmic koala following the guide on here:

[http://gwos.org/doku.php/guides:64bit:et_wolfenstein](http://gwos.org/doku.php/guides:64bit:et_wolfenstein)

I got up to the pathches which I downloaded onto my desktop and tried to use the commands:
cd ~/Desktop
unzip et-2.60b.zip
cd "Enemy Territory 2.60b/linux"
sudo cp -r * /usr/local/games/enemy-territory

My problem is that Im not able to unzip the file or use the last command because its not unziped. I tried extracting on the desktop which worked but dont know what to do next!!!!!
Also, being STUPID I followed the remaing instructions on the guide and ended up with enemy territory on the games list on the menu but it doesnt work saying:
Could not launch 'Enemy Territory: Wolfenstein'
Failed to execute child process "et" (No such file or directory)

As u can see Im a complete NOOB to linux and I need help

THANX!!!!!!!!!!!!!

---

### Post by michy99 on 2009-11-11
Make sure you have installed the zip and unzip packages.```
sudo apt-get install zip unzip
```

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
You say you unzipped them in the gui to the desktop... so then all you need to do is the last 2 commands again ```
cd "Enemy Territory 2.60b/linux"
sudo cp -r * /usr/local/games/enemy-territory
``` and that should put the game files in the right place so the link in the menu actually sees the "et" file it's looking for. Make sure the ```
cd "Enemy Territory 2.60b/linux"
``` name is correct. It's the name of the folder that you unzipped everything to. You can do this in the gui if you "sudo nautilus" and then you can just drag the contents of /home/user/Desktop/Enemy Territory 2.60b/linux to /usr/local/games/enemy-territory. Hope this helps.

---

### Post by EnioG on 2009-12-05
How can I erase everything i have done and re-install???

---


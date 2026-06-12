---
title: "aMSN skin"
date: 2010-12-27
forum: General Help
---

### Post by domoappo on 2010-12-27
I want to download a skin for aMSN. I downloaded the skin then extracted the files. The aMSN website then tells me I'm supposed to copy the extracted skin folder to one of the following locations: 
/usr/share/amsn/skins
 $HOME/.amsn/skins

[FONT=Verdana]Where exactly are those locations and how do I get to them? How do I do this?[/FONT]

---

### Post by Verbeck on 2010-12-27
$HOME/.amsn/skins = /home/username/.ams/skins
which means the .amsn folder in your home directory (press ctrl+H to see it and other folders starting a . (period))
if you save it there, the skin would be only available from your user account

but if you save it to /usr/share/amsn/skins, it would be available to all the users
and since it's a system wide change, it requires authentication. so from a terminal, run 
*gksu nautilus /usr/share/amsn/skins* to open the folder with root privileges

---

### Post by domoappo on 2010-12-27
Thank you so much, I got it working! :D

---


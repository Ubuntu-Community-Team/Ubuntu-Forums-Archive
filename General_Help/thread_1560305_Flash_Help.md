---
title: "Flash Help"
date: 2010-08-24
forum: General Help
---

### Post by borth92 on 2010-08-24
In Ubuntu and most other Linux distributions, Adobe Flash settings are stored in ~/.adobe and the cookies themselves in ~/.macromedia folders. I have these simlinked to /dev/null (effectively a black hole) so that anything trying to write to these folders doesn’t get an error message, but nothing ever gets written to disk. 

rm -rf ~/.adobe ~/.macromedia
ln -s /dev/null ~/.adobe
ln -s /dev/null ~/.macromedia

This setup, however, causes certain sites to become unstable and I have no idea how to undo it. Please help me undo the commands above...

---

### Post by borth92 on 2010-08-24
bump

---

### Post by Vaphell on 2010-08-24
just remove .adobe and .macromedia, they should be recreated as normal dirs with actual stuff inside
confirm it with ls -la (symlinks show their true targets)

if you want to get rid of those nasty flash cookies you can try 'BetterPrivacy' plugin for firefox. It removes all but really necessary files (at least i think so :))

---

### Post by borth92 on 2010-08-25
i cannot find those folders in my home directory. I cant create them cuz it says they exist but they simply are not there (even with ctrl+h)

---

### Post by borth92 on 2010-08-25
Thank You I got it.

Couldnt find the folders all i needed was to rm them through a terminal and all videos work again. I'll look into that plugin for the flash cookies. Thanks Much

---


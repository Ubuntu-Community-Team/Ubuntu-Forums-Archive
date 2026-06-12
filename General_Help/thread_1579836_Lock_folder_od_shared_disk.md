---
title: "Lock folder od shared disk"
date: 2010-09-22
forum: General Help
---

### Post by jodlajodla on 2010-09-22
Hello!
I need a folder on my network disk, which will be locked with password, and must be entered on all platforms from where the user come (Ubuntu, Win). 

Can I do that?

Thanks for all replies! :)

---

### Post by Sin@Sin-Sacrifice on 2010-09-22
You can change the file permissions via right-clicking the folder and changing options under the permissions tab. Or you can just ```
sudo chmod 000 /folder/path
``` so only root can get in. If you absolutely have to have a password on it you can encrypt the folder. ```
sudo apt-get install seahorse-plugin
```. That way you can just right-click the folder to encrypt it from the menu. You're going to have to make a GPG key. Google it.

---

### Post by jodlajodla on 2010-09-22
And then will need be password entered also in Win?

Thanks! :)

---

### Post by Sin@Sin-Sacrifice on 2010-09-22
You'll have to use truecrypt if you want it to work in windows. Seahorse is not compatible with Win.

---


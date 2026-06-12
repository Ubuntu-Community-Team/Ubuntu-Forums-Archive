---
title: "Login Password no longer matches Login Keyring"
date: 2010-11-18
forum: General Help
---

### Post by Cookie-Tux on 2010-11-18
Okay. I just updated to 10.10 (:D), but I have one problem. I changed my password a few days ago, and now whenever I log on, It comes up with the attached message, and I have to type in my *OLD* password to connect to wireless. What does this mean and how can I fix it? Thanks :)

---

### Post by ajgreeny on 2010-11-18
I'm not sure how the change of password may affect this but normally you need to right click in the network manager icon in your panel, Edit connections, highlight the wireless connection, choose Edit,and the make sure the boxes for "Autoconnect" and "Make available to all users" are checked.

If they already are checked, then you may need to search out the keyring files in your system and edit them, but there, I'm lost, I'm afraid, but the only two files I can find that I would wish to play around with are in ~/.gnome2/keyrings.  Perhaps you need to rename them and then make new ones once the old ones are gone.

---

### Post by mister_playboy on 2010-11-18
If you just delete the keyring files mentioned above, you should be able to get your current password and keyring sync'd when the the file is automatically recreated.  It will ask you for the password on the next keyring access, you can type the new one and it should stop bothering you.

This annoying issue has been in Ubuntu as long as I have used it...

---

### Post by Cookie-Tux on 2010-11-24
Sorry for late reply. I'll try that.

---

### Post by Cookie-Tux on 2010-11-24
Solved! thank you so much :)

---


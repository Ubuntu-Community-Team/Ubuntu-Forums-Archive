---
title: "Creating new folder?"
date: 2006-04-25
forum: General Help
---

### Post by Sonic5688 on 2006-04-25
i need to create a folder called Doom 3 in usr/local/games/, but when i right click, the new folder option is grey and unclickable. Whats going on?

---

### Post by dermotti on 2006-04-25
Its because you need root/sudo access to create folders outside of your home folder.

You could try typing **gksudo nautilus** from command line to get a root browser.

---

### Post by Sonic5688 on 2006-04-25
What does that mean? how do you sudo access?

---

### Post by aysiu on 2006-04-25
Another way to do it would be going to Applications > Accessories > Terminal and typing ```
sudo mkdir /usr/local/games
```

---

### Post by Sonic5688 on 2006-04-25
Thanks alot! Now maybe I can get Doom 3 running :)

---

### Post by robglinka on 2006-04-25
Hey, you might also need to set up permissions on that folder, so if you get an access denied error when you are setting up Doom 3, don't freak out.

---


---
title: "Turned on Computer after two Days and now I can't login"
date: 2011-02-24
forum: General Help
---

### Post by mwill295 on 2011-02-24
I'm having an issue that I hope someone can help with. I turned on my computer today (running Ubuntu 10.10) and it will go to the login screen where it shows the time at the bottom right and the restart and shutdown button, and also my computer name in the middle of the screen but it does not show my account name. My mouse and keyboard work fine there is just know where to login at. I'm still pretty new to ubuntu so I'm not to sure where to begin. Any help would be greatful. Thanks

---

### Post by TimEnid on 2011-02-24
try this
```
sudo dpkg-reconfigure gdm
```

if that doesnt work, try
```
sudo apt-get install gdm
```

---

### Post by mwill295 on 2011-02-24
I think I may have caused more damage, before I got your post I went into recovery mode and put my graphics back to default now it won't load up unless I go into low res graphics mode, and then once in there I cant get to the terminal (ctl alt f4). All it will show is a blinkin underscore.

---


---
title: "My desktop is gone?"
date: 2011-02-26
forum: General Help
---

### Post by evanm457 on 2011-02-26
I have ubuntu on my old laptop with a few music analisis software. I make music with reason on my new laptop so its a cool setup but recently I installed a dock that looks like a mac and as far as I know its called docklet. The dock was taking up way too much ram. So I tried uninstalling it. Now this is probably where it happened because next time i turned on my laptop the dock was gone but also the top and the bottom desktop taskbars are gone or whatever they are. My screen is completly bare from top to bottom and but fortunatly I do have a little search thing that pops up at the start that I can get any software by typing it in. Please help me :)

---

### Post by runeh76 on 2011-02-26
remove "docklet"

```
sudo apt-get autoremove --purge docklet
```


install gnome-desktop

```
sudo apt-get install gnome-desktop
```

---


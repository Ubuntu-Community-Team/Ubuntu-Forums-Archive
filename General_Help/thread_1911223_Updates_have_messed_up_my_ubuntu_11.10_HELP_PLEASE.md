---
title: "Updates have messed up my ubuntu 11.10 HELP PLEASE!!"
date: 2012-01-18
forum: General Help
---

### Post by block g raptor on 2012-01-18
**Updates have messed up my ubuntu 11.10 HELP PLEASE!!**             
                                                                Ive recently  installed updates in oneric, when i rebooted my gnome theme was gone, My  discs no longer mount in media folder, flash player was gone and my  video card was messed up. Ive manged to fix most of the problems after  many hour on google and in terminal. however I still cant open the my  computer location from the places menu (gnome classic view) also  Cd´s/DVD´s are not recognized / mounted Ive googled like crazy but cant  find a solution anywhere. I´m getting an error dialogue box when I click  on computer in the places menu : Could not open location 'computer://'  mode not supported

---

### Post by cariboo on 2012-01-18
It sounds like you did a partial update. Have you tried in a terminal:

```
sudo apt-get -f install
```

---

### Post by block g raptor on 2012-01-19
o] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gnome-applets-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 271 not upgraded.
paul@paul-0000000000000000000

---

### Post by block g raptor on 2012-02-08
still having this issue can anyone help ?

---


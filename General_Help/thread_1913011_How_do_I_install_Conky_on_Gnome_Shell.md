---
title: "How do I install Conky on Gnome Shell?"
date: 2012-01-21
forum: General Help
---

### Post by TheNerdAL on 2012-01-21
Trying to install it since it looks nice, can anyone help me? The .conkyrc file doesn't seem to work with gnome shell.

---

### Post by Frogs Hair on 2012-01-21
You may have done this already .
```
sudo apt-get install conky-all
``` 
```
sudo apt-get install lm-sensors
``` 
```
sudo sensors-detect
```
Answer yes to all questions .

post a link to the configuration you are trying to use . Normally the .conkyrc is placed in home / hidden but not in a folder unless the instructions or read-me state otherwise . Configurations with clock rings come with instructions most of the time but not always .

---

### Post by TheNerdAL on 2012-01-21
> **Frogs Hair said:**
> You may have done this already .
```
sudo apt-get install conky-all
``` 
```
sudo apt-get install lm-sensors
``` 
```
sudo sensors-detect
```
Answer yes to all questions .

post a link to the configuration you are trying to use . Normally the .conkyrc is placed in home / hidden but not in a folder unless the instructions or read-me state otherwise . Configurations with clock rings come with instructions most of the time but not always .

I used this one that I found from wikihow: [http://www.ferns16.plus.com/MyLinuxRamblings/conkyrc](http://www.ferns16.plus.com/MyLinuxRamblings/conkyrc)

---

### Post by Frogs Hair on 2012-01-21
The .conkyrc doesn't work for me either and can't see any obvious  reason why , but it would take time to go through it all . Conky does start but it is the default black box . 

I have a number of configurations I found @ Gnome Look that work with the Gnome Shell maybe you can find one like there . Most come with instructions , which makes life easier unless you choose something complicated .

---

### Post by TheNerdAL on 2012-01-21
> **Frogs Hair said:**
> The .conkyrc doesn't work for me either and can't see any obvious  reason why , but it would take time to go through it all . Conky does start but it is the default black box . 

I have a number of configurations I found @ Gnome Look that work with the Gnome Shell maybe you can find one like there . Most come with instructions , which makes life easier unless you choose something complicated .

I'd love to see them.

---

### Post by Bobhuber on 2012-01-21
Try loading screenlets. Its has a number of  desktop widgets  including a system monitor and is very user friendly .

---


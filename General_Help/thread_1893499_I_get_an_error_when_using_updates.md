---
title: "I get an error when using updates"
date: 2011-12-10
forum: General Help
---

### Post by blueshead on 2011-12-10
I get an error when using updates

"Type 'Cairo-Dock-PPA' is not known on line 54 in source list /etc/apt/sources.list"

I went to the sources list to remove it, but could not.

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Any suggestions?

---

### Post by bluexrider on 2011-12-10
easy to do

```
sudo gedit /etc/apt/sources.list
``` and save
then
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by blueshead on 2011-12-10
Thank you.. All working now..  :D

Also Ubuntu Software Center was not working..  It is now..

---

### Post by Rubi1200 on 2011-12-10
Glad you got things sorted out after the good support from bluexrider.

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy :)

---

### Post by bluexrider on 2011-12-10
Glad to help

---


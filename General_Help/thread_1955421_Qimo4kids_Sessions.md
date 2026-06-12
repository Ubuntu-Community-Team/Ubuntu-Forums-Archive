---
title: "Qimo4kids Sessions"
date: 2012-04-09
forum: General Help
---

### Post by blackangelpr on 2012-04-09
Greetings everyone, currently i found out a video about qimo4kids and found that it is a great solution to let kids play safely on the home computer without the worry they will delete something important since i am funning ubuntu 11.10 i found the following way to install the session

"sudo apt-get install qimo-session"

then log out and went to the gimo4kids session but my background changed to blue instead of leaving the default qimo theme ...


any suggestion will be appreciated by this newbiew :) 


thanks in advance..

):P

---

### Post by pjman on 2012-04-09
I did a search for "qimo" on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and found [http://packages.ubuntu.com/oneiric/all/qimo-wallpaper](http://packages.ubuntu.com/oneiric/all/qimo-wallpaper)

Try:

```
sudo apt-get install qimo-wallpaper
```

Hopefully that helps :p

---

### Post by blackangelpr on 2012-04-09
> **pjman said:**
> I did a search for "qimo" on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and found [http://packages.ubuntu.com/oneiric/all/qimo-wallpaper](http://packages.ubuntu.com/oneiric/all/qimo-wallpaper)

Try:

```
sudo apt-get install qimo-wallpaper
```Hopefully that helps :p

Thank for the answer: i had already done that but the issue is to be more spesific when i log in to the qimo session i cand see the background but a couple of secconds later it turns blue and a keyboard its displayed on the screen... if i try to edit the backgtround i just can see the ubuntu options ... its seems like a background over another one :( other than that everything its fine

---

### Post by blackangelpr on 2012-04-12
had solve the issue like this:

```
 
cd /usr/share/xsessions

sudo rm qimo.desktop   
//this remove it from the log in screen

sudo apt-get --purge remove qimo-session  
// thanks to some one in ubuntu that send me this code since its deletes the session data... as well could
// used to delete gnome, genome clasic etc... 
 
```:guitar:  Ubuntu Rocks

---


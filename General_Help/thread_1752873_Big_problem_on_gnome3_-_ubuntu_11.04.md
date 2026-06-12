---
title: "Big problem on gnome3 - ubuntu 11.04"
date: 2011-05-08
forum: General Help
---

### Post by Gladiator-prog4me on 2011-05-08
Hello 

i have install gnome 3 on ubuntu 11.04

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
```

and i try :

```
sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard

```


and i faces a problem !! 

1- right click in mouse and scrol not working !
2- so slowly and some times friezed !
3- i can't do any think :( 

every think is unusual  :(

please see the photo in attachment .

---

### Post by Gladiator-prog4me on 2011-05-08
??

---

### Post by Gladiator-prog4me on 2011-05-09
up

---

### Post by dino99 on 2011-05-09
read the doc on top of this ppa to know what/how/which_order you need to install some other ppa

[https://launchpad.net/~jbicha/+archive/ppa](https://launchpad.net/~jbicha/+archive/ppa)

---

### Post by Gladiator-prog4me on 2011-05-09
> **dino99 said:**
> read the doc on top of this ppa to know what/how/which_order you need to install some other ppa

[https://launchpad.net/~jbicha/+archive/ppa](https://launchpad.net/~jbicha/+archive/ppa)

hi, 

i don't understand do you mean install this ppa  ? or what' ? 

thank you

---

### Post by matthewbpt on 2011-05-09
I would recommend a distro where Gnome 3 is officially supported if you want things to work properly. Fedora 15 which is released quite soon will have Gnome 3 by deafault. I am using Gnome 3 on Arch and it is working very well without any need for hacks / installing aternative repositories etc. Until Ubuntu have Gtk 3 in the repos it won't be a smooth experience to use Gnome 3 ...

---

### Post by bmbaker on 2011-05-09
> **Gladiator-prog4me said:**
> hi, 

i don't understand do you mean install this ppa  ? or what' ? 

thank you
there is a bit of a problem with some of the updates so i also use 
the testing ppa
```
[FONT=Courier New][SIZE=2]sudo add-apt-repository ppa:[B]ricotz/testing
sudo apt-get update && sudo apt-get dist-upgrade
  [/B] [/SIZE][/FONT]
```

this should fix you up :-)
if not then post back :-)
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]

---

### Post by Gladiator-prog4me on 2011-05-09
> **bmbaker said:**
> there is a bit of a problem with some of the updates so i also use 
the testing ppa
```
[FONT=Courier New][SIZE=2]sudo add-apt-repository ppa:[B]ricotz/testing
sudo apt-get update && sudo apt-get dist-upgrade
  [/B] [/SIZE][/FONT]
```

this should fix you up :-)
if not then post back :-)
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]

i'am re-install ubuntu , so if this not working .. how to back the unity ? thank you

---


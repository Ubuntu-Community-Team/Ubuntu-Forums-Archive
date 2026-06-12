---
title: "epic"
date: 2012-02-12
forum: General Help
---

### Post by penka on 2012-02-12
hello guys - I have a dumb problem - I tried to change the login picture and now it simply doesn't start so in a way I've done what I wanted... but I don't know how to launch the terminal from the ubuntu launching screen. I'm sure this one's easy for you

---

### Post by savanna on 2012-02-12
"It simply won't start" - *what* won't start? Does the machine boot, can you login, ...? A bit more detail please :-)

---

### Post by penka on 2012-02-12
> **savanna said:**
> "It simply won't start" - *what* won't start? Does the machine boot, can you login, ...? A bit more detail please :-)

the machine starts, it shows the ubuntu icon with the loading bar but it goes only so far. doesn't get to the login screen. :)

---

### Post by penka on 2012-02-12
I think I should launch a os cd or somth I just wondered if there's any other way guess not thanks anyway savanna

---

### Post by raja.genupula on 2012-02-12
look for this
*What to do if things go wrong* 
in the below link 
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by penka on 2012-02-12
> **raja.genupula said:**
> look for this
*What to do if things go wrong* 
in the below link 
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

Hi Thanks for the tip - I opened the terminal, logged as root, and wanted to open the *** conf of the unity -greeter - 
gksu gedit /etc/lightdm/unity-greeter.conf
and i got
(gksu:1586): Gtk-WARNING **: cannot open display 
hmm.. i feel really bad (stupid) for trying to change that damn picture. :(

---

### Post by sleepyhollows on 2012-02-12
> **penka said:**
> Hi Thanks for the tip - I opened the terminal, logged as root, and wanted to open the *** conf of the unity -greeter - 
gksu gedit /etc/lightdm/unity-greeter.conf
and i got
(gksu:1586): Gtk-WARNING **: cannot open display 
hmm.. i feel really bad (stupid) for trying to change that damn picture. :(

If you used Alt-f1 or ctrl-alt-f1 (as I usually find it is), you are on the console, and need to use 'vi' instead of 'gedit', and you need to use 'sudo' instead of 'gksu'

---

### Post by Elfy on 2012-02-12
If you've not used vi try nano

```
sudo nano -B /etc/lightdm/unity-greeter.conf
```

Edit file, then Ctrl+O to save and Ctrl+X to exit

-B makes it create a backup first

---


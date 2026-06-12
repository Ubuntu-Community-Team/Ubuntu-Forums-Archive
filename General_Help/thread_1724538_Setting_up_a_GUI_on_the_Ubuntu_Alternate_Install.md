---
title: "Setting up a GUI on the Ubuntu Alternate Install"
date: 2011-04-08
forum: General Help
---

### Post by linuxuser12345 on 2011-04-08
Hey, I am still, of course, trying to fix this little 2GB netbook, and I am now wondering, how do I get a GUI installed after I install Ubuntu Desktop Edition (Alternate Install)?

Please help me out soon, as I am trying to fix this netbook asap! Thank you! :)

---

### Post by sanguinoso on 2011-04-08
What do you mean by GUI? Are you talking about Gnome or KDE? As in the desktop environment? If so type: ```
sudo apt-get install gnome-desktop
```

---

### Post by techunit on 2011-04-08
Installing Ubuntu on a two gigabyte netbook really isn't going to work satisfactory. I urge you to look at products like Lubuntu or Peppermint Os which will run much better on such a small amount of space.

The alternate install gernerally installs a GUI it is just used when the computer has insufficient ram to use the live environment.

If you have a command prompt you should look at these commands to see how much space you have.

```
free
```

this should tell you how much free space you have access to. You will need about 700MBs free to be safe to install Xubuntu-Desktop. 
```
sudo apt-get install xubuntu-desktop
```
Gnome won't run very well with the amount of ram available. I hope you prevented the installer from putting a swap partition on the computer as it will likely eat up a 200MB chunk.

Good Luck

---

### Post by techunit on 2011-04-08
> **sanguinoso said:**
> What do you mean by GUI? Are you talking about Gnome or KDE? As in the desktop environment? If so type: ```
sudo apt-get install gnome-desktop
```
I seriously doubt that he will have enough room to do that as gnome takes up about 900MBs of space to install. Please tell him to run the ```
free
``` command to see how much free space he has access to.

---

### Post by sanguinoso on 2011-04-08
> **techunit said:**
> I seriously doubt that he will have enough room to do that as gnome takes up about 900MBs of space to install. Please tell him to run the ```
free
``` command to see how much free space he has access to.

2GB HDD? I thought he was talking about RAM. If he's talking about HDD then you're absolutely correct.

---

### Post by linuxuser12345 on 2011-04-08
> **sanguinoso said:**
> 2GB HDD? I thought he was talking about RAM. If he's talking about HDD then you're absolutely correct.

lol! 2GB SSD

---

### Post by nothingspecial on 2011-04-08
You are going to want xinit and slim for a start.

Or you could just use it cli style.

---


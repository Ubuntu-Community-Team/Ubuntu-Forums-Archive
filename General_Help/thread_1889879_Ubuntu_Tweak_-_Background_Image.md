---
title: "Ubuntu Tweak - Background Image"
date: 2011-12-02
forum: General Help
---

### Post by Richiegs on 2011-12-02
After I removed Ubuntu Tweak and deleted ts file in the config folder, the same background image I chose to display in Ubuntu Tweak still appears during startup of the PC. Is there a way to fix it? Thanks

---

### Post by stinkeye on 2011-12-02
If your using 11.10 the setting is in 
```
gksu gedit /etc/lightdm/unity-greeter.conf
```

the default setting is
```
background = /usr/share/backgrounds/warty-final-ubuntu.png
```

---

### Post by Frogs Hair on 2011-12-02
I use Ubuntu Tweak and when I search for the location of the current background image it is in the backgrounds folder that I created . Ubuntu Teak allows you to navigate to a folder and select a background image .

I have discovered by using Ubuntu Tweak in the past that if the image is moved to a different folder or deleted the background image reverts to default .

---

### Post by Richiegs on 2011-12-02
> **stinkeye said:**
> If your using 11.10 the setting is in 
```
gksu gedit /etc/lightdm/unity-greeter.conf
```

the default setting is
```
background = /usr/share/backgrounds/warty-final-ubuntu.png
```

I am using Ubuntu 10.04. The reason I removed ubuntu Tweak was that I suspected it casued "Signal not detected" in my monitor.

---

### Post by Richiegs on 2011-12-03
> **Frogs Hair said:**
> I use Ubuntu Tweak and when I search for the location of the current background image it is in the backgrounds folder that I created . Ubuntu Teak allows you to navigate to a folder and select a background image .

I have discovered by using Ubuntu Tweak in the past that if the image is moved to a different folder or deleted the background image reverts to default .

After I removed Ubuntu Tweak, the background image did not return to the system's default image. Is there a way to fix it?

---

### Post by oldtimer7777 on 2011-12-03
> **Richiegs said:**
> After I removed Ubuntu Tweak, the background image did not return to the system's default image. Is there a way to fix it?

sudo apt-get install bleachbit
sudo bleachbit

Clean your system out, and do a power cycle of your computer.

---


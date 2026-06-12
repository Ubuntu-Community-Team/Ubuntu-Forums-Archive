---
title: "Startup Programs"
date: 2012-08-22
forum: General Help
---

### Post by rickm1945 on 2012-08-22
I have a desktop calendar appointment schedule and I have to manually start.Is it possible to have it start up when I boot and how do I accomplish that.

---

### Post by JRV on 2012-08-22
Click on the icon at the top far right.
Select Startup Applications and add it.

---

### Post by Frogs Hair on 2012-08-22
You can open startup application and select add and enter the application name. I have alacarte installed so I copy and paste the command from the  application properties in the Main Menu available after installing alacarte . The comment section is optional.

In the command section sometimes the path to where the application is installed is needed which differs from app to app this is why I copy and paste the command. If I was using the same application I could simply post the command for you. 
```
sudo apt-get install alacarte
```

---

### Post by vasilbelarus on 2012-08-22
If you want to have full access to auto-starting apps (many of them hidden by default) put this to your terminal: ```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop

```

---

### Post by rickm1945 on 2012-08-29
> **JRV said:**
> Click on the icon at the top far right.
Select Startup Applications and add it.
Where can I access the the program to get its properties?

---


---
title: "Admin password error"
date: 2011-01-23
forum: General Help
---

### Post by JLB1092 on 2011-01-23
Requesting help with admin pasword issue. I was trying to load the drivers for Lexmark printer Lexmark-08Z-series-driver-1.0-1.i386.deb.sh.....system prompts me for my admin password, I entered it correctly and the system refuses to recognize it. I have not changed my admin password since initially installing Ubuntu.I had used it earlier to load and configure my system to recognize/operate a CAC reader.  I wonder if I inadvertantly changed something when prepping the system for the CAC reader (which works well now) and somehow changed my admin password.....or if the instructions I used changed something....I am a Ubuntu novice. .I did not have a admin password problem prior to following the instructions located at  [http://zxq9.com/dodcac/U10.4-LTS-32/Ubuntu10.4-LTS-32.html]("http://zxq9.com/dodcac/U10.4-LTS-32/Ubuntu10.4-LTS-32.html.......For")  for configuration of CAC Reader.

---

### Post by khjinn on 2011-01-23
Is it cap-sensitive? 

Make sure you're getting it right.

---

### Post by Hippytaff on 2011-01-23
Linux is case sensitive :-)

---

### Post by JLB1092 on 2011-01-23
Thanks. I am certain that I am using the correct pwd.

---

### Post by Hippytaff on 2011-01-23
Is the sudo password the same as your user password? you can try doing
```

passwd

```
and changing the password

---

### Post by JLB1092 on 2011-01-23
Thanks. I opened a terminal window and successfully changed my root admin password. However, when I try to load the Lexmark driver, the system does not recognize it. I am at a loss....

---

### Post by JLB1092 on 2011-01-23
Additionally, I just used the new password to conduct a standard update...worked with no problem. So password is good, but the Lexmark driver loader is not recognizing my admin password to allow me to load the driver.

---

### Post by Krytarik on 2011-01-24
Try to run the installer from within the "Root Terminal", it's in "Applications -> System Tools". You may have to "unhide" it before, right-click at the menu bar, then choose "Edit Menus".

---


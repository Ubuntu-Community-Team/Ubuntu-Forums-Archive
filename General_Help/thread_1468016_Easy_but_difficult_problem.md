---
title: "Easy but difficult problem"
date: 2010-05-01
forum: General Help
---

### Post by saini7002 on 2010-05-01
Dear Friends,
                   I accidentally removed battery and sound notifiers from my panel in lucid lynx.I tried to restore them by clicking on add to panel but there was nothing like "notification applet".What should I do to restore these icons.Please help.

---

### Post by Skorzen on 2010-05-01
In Lucid, I think it is called "Indicator Applet".

---

### Post by dino99 on 2010-05-01
sudo apt-get install ubuntu-desktop
sudo apt-get install -f

sudo dpkg --configure -a

---

### Post by saini7002 on 2010-05-01
Thanks Skorzan for coming forward..but the indicator applet only restores the "email" notifier i.e. notifier about "chat,broadcast,and set up mail"...but battery and sound icons are not being restored.

---

### Post by saini7002 on 2010-05-01
hi dino99,
             I followed your steps but nothing happened...battery and sound icons are still missing..plz help.

---

### Post by fyo on 2010-05-01
In earlier versions, the battery indicator was called "Battery Charge Monitor" and you added it to the panel by right-clicking on the panel,  selecting "Add to panel" and then adding the "Battery Charge Monitor" item.

(and the sound thing was called "Volume Control")

---

### Post by saini7002 on 2010-05-01
Yes in earlier versions it was so..but after that it was converted to "notification applet" but in ubuntu 10.04 i cant find any launcher for battery and sound...

---

### Post by marclol on 2010-05-01
I dont know about sound but batty, go into System -> Preference -> Power Management -> General

Choose always display Icon, restart computer. Done;

---

### Post by saini7002 on 2010-05-01
@marclol....thanks for the reply pal...but still there is no battery icon..

---

### Post by saini7002 on 2010-05-01
@marclol...thanks pal..your reply has helped me in recovering the battegy icon when i made it default...plz help for sound icon also.

---


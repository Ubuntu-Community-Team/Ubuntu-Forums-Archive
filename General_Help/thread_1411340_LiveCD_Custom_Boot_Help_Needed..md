---
title: "LiveCD Custom Boot Help Needed."
date: 2010-02-19
forum: General Help
---

### Post by appzattak on 2010-02-19
Hey all,

I'm making a custom LiveCD based on 9.10. I have it all done except a couple things. I need to figure out how to delete the option at start that says "Install Ubunut" & "Boot first HDD". I would also like to remove the icon from the dekstop that says "install ubunutu"

Any guidance would be greatly appreciated.

--Steve

---

### Post by appzattak on 2010-02-20
anyone?

---

### Post by appzattak on 2010-02-21
one more time.......

---

### Post by Clownox on 2010-02-26
> **appzattak said:**
> Hey all,

I'm making a custom LiveCD based on 9.10. I have it all done except a couple things. I need to figure out how to delete the option at start that says "Install Ubunut" & "Boot first HDD". I would also like to remove the icon from the dekstop that says "install ubunutu"

Any guidance would be greatly appreciated.

--Steve

i hope i can help..
"install ubuntu & boot first hdd" for this you need to change isolinux, you can find it at extracted cd find isolinux folder and change isolinux.cfg

for "install ubuntu" on desktop, maybe its /usr/share/applications/ubiquity-gtkui.desktop 
you can change the content and also change the icon,

i have completly change linux mint 8 (althougt its not ubuntu but have same structure)
just ask me, i will try my best

---


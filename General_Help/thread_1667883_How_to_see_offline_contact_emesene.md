---
title: "How to see offline contact emesene"
date: 2011-01-15
forum: General Help
---

### Post by mozartripper on 2011-01-15
Hi i want to see my offline contacts to be able to send them offline messages in emesene but i don't find the option in preferences

---

### Post by Mashvv on 2011-01-15
Go to 
Contacts >>Show >> Contacts Offline

---

### Post by mozartripper on 2011-01-15
there's no contact tab showing up in preferences as you can see. is it possible that it dosen't show up because i use ubuntu notebook remix (10.10) ?

---

### Post by narcisgarcia on 2011-02-14
I'm installing Emesene on Cibercafes.
How to setup to show offline contacts as default for any account?

---

### Post by narcisgarcia on 2011-02-14
Answering to myself; Patching Emesene:

```
cat /usr/share/emesene/Config.py | sed -e "s/'showOffline': False/'showOffline': True/g" > /tmp/emesene_Config.py
sudo mv /usr/share/emesene/Config.py /usr/share/emesene/Config.py.original
sudo mv /tmp/emesene_Config.py /usr/share/emesene/Config.py

```

---

### Post by MrGloOP on 2011-03-04
Hi all !
As I've installed Ubuntu Netbook Edition 10.10, I had the same problem as Mozartripper.

Thank you Narcisgarcia, your script was really helpfull !!!

I just complete the answer: if (like me) you already have an account with the "Remember me" option checked, you must rename / delete your emesene1.0 folder in "/home/*you*/.config/" to see the effect of that script.

That's all folks.

---


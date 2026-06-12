---
title: "KDE Wallet"
date: 2010-05-05
forum: General Help
---

### Post by Magnificence on 2010-05-05
Hi, I'm using Kubuntu 10.04 at the moment.

Every time I log in, KDE Wallet asks me to give a password so that Kopete can access my login password to login. Is there any way you can 'grant permission' to access the wallet for certain applications so that I don't have to fill in my password every time?

---

### Post by AndreeeCZ on 2010-05-05
Yes, go to settings - system settings - advanced - kde wallet and disable it. I am not using english version of kubuntu, so the steps are just roughly translated.

---

### Post by Magnificence on 2010-05-05
But if I disable it, will I still get a message when a new program want to access the wallet? :)

---

### Post by lovinglinux on 2010-05-05
Go to "System Settings >> Advanced User Settings >> KDE Wallet", select the Access Control tab, right-click on Kopete and delete it. When Kwallet asks again if you want to allow Kopete to access the wallet, make sure you click the option to always allow.

---

### Post by Magnificence on 2010-05-05
Ok thanks! I appreciate it!

---

### Post by Magnificence on 2010-05-05
Now ok, I did both. I unchecked the checkbox about it should prompt.
But when I log in, Kopete still want me to give my password, while Amarok will ask for acces (where I can say: Always allow).

So I still need to give my password every time I log in.

---

### Post by lovinglinux on 2010-05-05
> **Magnificence said:**
> Now ok, I did both. I unchecked the checkbox about it should prompt.
But when I log in, Kopete still want me to give my password, while Amarok will ask for acces (where I can say: Always allow).

So I still need to give my password every time I log in.

Have you clicked the apply button after deleting the Kopete line from Kwallet?

---

### Post by Magnificence on 2010-05-05
Yes, actually, I emptied the whole list too.

---

### Post by lovinglinux on 2010-05-05
> **Magnificence said:**
> Yes, actually, I emptied the whole list too.

Try to close the wallet and open it again or even reboot. Perhaps this helps.

---

### Post by Magnificence on 2010-05-05
I don't know exactly what made the difference, but after like 10 times of relogging Kopete gave me the opportunity to click Alway Allow and didn't request me to fill in a password anymore.
I thing that the difference of the last time was that I closed Kopete before I relogged. Anyway, thanks for your time. :)

---


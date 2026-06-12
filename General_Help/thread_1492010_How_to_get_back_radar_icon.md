---
title: "How to get back radar icon?"
date: 2010-05-24
forum: General Help
---

### Post by larrylamsy on 2010-05-24
[FONT="Arial"][SIZE="3"]Hi, please help.  I accidentally removed the icon of “wireless network” from the top right task bar. The icon just looks like a radar detection. How can I get it back? Many thanks. - Larry [/SIZE]:)[/FONT]

---

### Post by mhgsys on 2010-05-24
open a terminal and type:

```
gconftool-2 --recursive-unset /apps/panel
```

and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) (login) and type:

```
sudo /etc/init.d/gdm stop
```

```
sudo /etc/init.d/gdm start
```

Panels and icons will be restored to original after doing this..

---

### Post by migs73 on 2010-05-24
Or if you are like me and prefer not to use terminal try this;
Right click on the panel where you removed it from, click on 'add to panel' then  scroll down to 'Notification Area' select it and then click add. After this three small bars appear on the panel. I think if the wireless indicator does not appear straight away it will on next boot.

---

### Post by larrylamsy on 2010-05-24
[SIZE="4"]Dear mhgsys, 

Thank you very much! It works. 

Larry [/SIZE]:P

---

### Post by mhgsys on 2010-05-24
Your absolutely welcome larry.

Please mark your thread as solved.

(Go to thread tools > Mark this thread as solved)

---


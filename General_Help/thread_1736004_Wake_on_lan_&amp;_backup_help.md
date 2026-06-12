---
title: "Wake on lan &amp; backup help"
date: 2011-04-22
forum: General Help
---

### Post by wizardob on 2011-04-22
Hi guys
First post so be gentle.
Got Ubuntu10 installed and it sees both win7&XP machines. I now need to set the server so it will go to sleep and wake on lan. What do I do /Use? 

Also need a program to backup both pc's to server hopefully an single button action to perform the task as I'm not very techy.

So a nice Gui would be a great help

Need a dummies guide I'm afraid

---

### Post by Rebelli0us on 2011-04-22
You can wake up a windows machine from ubuntu with this command

```
wakeonlan 0C:1D:FF:B8:C2:88
```

where letter/number string is the MAC address

.. and you can set the windows machine to auto-suspend after X minutes of inactivity through the power options in control panel.

---

### Post by wizardob on 2011-04-23
Thanks Fella!):P

---


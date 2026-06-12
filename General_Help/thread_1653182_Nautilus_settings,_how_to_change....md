---
title: "Nautilus settings, how to change...?"
date: 2010-12-26
forum: General Help
---

### Post by Spyderkid on 2010-12-26
I would like to change the setting on nautilus which is /usr/bin/cautious-launcher I don't want this setting how do I remove/disable it...?

---

### Post by wojox on 2010-12-26
That's a security feature. There for we can't really tell you on here how to disable it. Why do you ask? :confused:

---

### Post by Spyderkid on 2010-12-28
Aparrently I need to disable it to run DVD's from the disk on wine, because it says its read only so I can't make it excutable.

---

### Post by Spyderkid on 2010-12-29
Aparrently I need to disable it to run DVD's from the disk on wine, because it says its read only so I can't make it excutable. apparently I need to go to bin then propertiese and change something to do with "open with".

[Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump][Bump]

---

### Post by mcduck on 2010-12-29
> **Spyderkid said:**
> Aparrently I need to disable it to run DVD's from the disk on wine, because it says its read only so I can't make it excutable.

You don't need to make the file executable. It's not the .exe file you are executing, but Wine instead.

(and diabling such feature wouldn't change anything, anyway. optical medias are always read-inly fileysystes, no permissions can change that.)

So, instead of trying to click the .exe file to run it you should right-click it and choose to open it with Wine. That way it makes no difference if the .exe file has execute permissions or not.

---

### Post by Spyderkid on 2010-12-29
When I try to do that it say I need to make it executable but I can't because it says its a read only file-system because its a DVD-ROM


(that's what im doing anyway opening it with "wine windows program loader")

---

### Post by mc4man on 2010-12-29
> that's what im doing anyway opening it with "[COLOR="Blue"]wine windows program loader[/COLOR]

What mcduck was telling you to do - 
right click on any .exe - open with - other application -> use a custom command
For the command simply use 
wine

This will create a new r. click option named 'wine', use that instead of wine windows program loader

( If you wanted to change 'wine windows program loader' then you need to edit the Exec= line in /usr/share/applications/wine.desktop to remove the cautious launcher crap, ie., to this 

```
Exec=wine start /unix %f
```

---


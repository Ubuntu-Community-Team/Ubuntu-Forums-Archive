---
title: "how can I add an application to the &quot;open with&quot; menu ubuntu 11.10"
date: 2011-10-23
forum: General Help
---

### Post by acron1 on 2011-10-23
I went through this thread and still have no clue what to do: 

[http://ubuntuforums.org/showthread.php?t=1849973&page=1](http://ubuntuforums.org/showthread.php?t=1849973&page=1)

I am trying to add TrueCrypt in the "open with" menu without success...
Any advice will be greatly appreciated.
Thanks

---

### Post by jamesisin on 2011-10-23
Right click on the file type in question.

Choose Open With --> Other Application or Open with Other Application.

Ensure the **Remember this application for "[your file type]" files** check box is checked.

Select your preferred application from the list (if it doesn't appear in the list you'll have to use "Use a custom command" and you can get that command from the Properties dialog of a desktop icon for that application).

This will load that application into the Open With menu for that file type.

---

### Post by acron1 on 2011-10-23
> **jamesisin said:**
> Right click on the file type in question.

Choose Open With --> Other Application or Open with Other Application.

Ensure the **Remember this application for "[your file type]" files** check box is checked.

Select your preferred application from the list (if it doesn't appear in the list you'll have to use "Use a custom command" and you can get that command from the Properties dialog of a desktop icon for that application).

This will load that application into the Open With menu for that file type.

TrueCrypt doesn't appear on the list... furthermore the ability to "Use custom command" **went away in 11.10**... back to square one...

---

### Post by satanselbow on 2011-10-23
Open the  .desktop file in /usr/share/applications and see if the "Exec" line has a  "%F" appended to it - if it is missing tag it on ;)

You will have to open as root ie:

```
gksu gedit /usr/share/applications/<filename>.desktop
```

---

### Post by acron1 on 2011-10-23
> **satanselbow said:**
> Open the  .desktop file in /usr/share/applications and see if the "Exec" line has a  "%F" appended to it - if it is missing tag it on ;)

You will have to open as root ie:

```
gksu gedit /usr/share/applications/<filename>.desktop
```

Thanks brother.

---

### Post by dalanicolai on 2011-11-03
This is another way how to fix it (discovered it when Texmaker wouldn't show up in the open with menu). You can add %U behind the comment in the application properties in the main menu (you can install the main menu via the software center, then find it with the dash). Now the application will show up in the open with menu under file properties. Maybe the **method described earlier** in this thread is **cleaner** but I first saw this thread after I found the method described here.

---


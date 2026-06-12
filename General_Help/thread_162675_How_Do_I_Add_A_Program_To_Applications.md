---
title: "How Do I Add A Program To Applications?"
date: 2006-04-19
forum: General Help
---

### Post by Mark76 on 2006-04-19
I want to add **gnometab** to my list of applications.  I ripped it (is that the right word?) off of the SPM, but it doesn't appear in "Add applications".  Do I have to do that depackaging thing in the Terminal?  And, if so, what's the command again?

---

### Post by aysiu on 2006-04-19
Add Applications and Synaptic Package Manager are essentially the same thing. Add Applications has a simpler interface and doesn't display *all* the programs.

---

### Post by Mark76 on 2006-04-19
So I have to keep going into the Usr/Bin file every time I want to use gnometab (or any other program that's not in the Apps) then?

---

### Post by ronmarley1 on 2006-04-19
[QUOTE=Mark76]So I have to keep going into the Usr/Bin file every time I want to use gnometab (or any other program that's not in the Apps) then?[/QUOTE]
If I'm understanding you correctly, you have installed an application and want a shortcut to it in the Applications menu.  Some programs will add one for you.  Others you will need to add manually.  To add a shortcut manually, click on Applications -->System Tools -->Applications Menu Editor.  Click on the sub-menu you want to add the application to, for example, Sound and Video, and then click the New Entry button at the bottom.  Give the application name, the command to open it, and choose an icon if you want and you are all set.

---

### Post by aysiu on 2006-04-19
[QUOTE=Mark76]So I have to keep going into the Usr/Bin file every time I want to use gnometab (or any other program that's not in the Apps) then?[/QUOTE] The launchers for applications are usually in /usr/bin, but that doesn't mean you have to go to /usr/bin to launch the application.

For example, the launcher for my Firefox is /usr/bin/firefox (which is actually just a pointer to my real launcher--/usr/local/bin/firefox). If I Alt-F2 and type ```
firefox
``` Firefox opens.

Likewise, I can just create a launcher for the command ```
firefox
```

Windows behaves this same way. In Windows, my Firefox would be in C:\Program Files\Mozilla Firefox\firefox.exe, but I don't have to go to that folder every time I want to launch Firefox. I just Win+R and type ```
firefox
``` or create a launcher icon for it.

---


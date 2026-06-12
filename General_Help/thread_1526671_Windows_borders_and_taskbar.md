---
title: "Windows borders and taskbar"
date: 2010-07-08
forum: General Help
---

### Post by agamjain on 2010-07-08
I had downloaded some themes from the gnome website and had also downloaded compiz. There seemed to be some graphics issue, so I uninstalled compiz and also removed the theme. Now, when I restarted my computer the taskbar was gone and there were no borders on any of the windows. The close, minimise and maximise buttons were also not there. Therefore, I am not able to minimize, close or move any window.
Please help me.

---

### Post by arubislander on 2010-07-08
When you right click on your desktop and the preferences window comes up, click on Visual Effects (the last tab) and make sure that the first radio button is selected (None). That should restore your window borders.
--
EDIT: just tried the above in your situation, and since compiz is not installed everyting on the last tab is grayed out.

If you press ALT-F12 and type ```
metacity
``` in the box and press enter you should regain your window borders. I'll continue testing to tell you how to make this permanent.

---

### Post by arubislander on 2010-07-08
OK, did some testing in a virtual machine.

What happened is the following. You uninstalled Compiz without first disabling the Visual Effects (see my previous post). So the window manager that is in charge of drawing the window borders and such is no longer available. If you really don't want compiz installed the easiest way to go about it is:
1. reinstall compiz.
2. disable all Visual Effects in the Appearance Preferences dialog
3. uninstall compiz.

(Of course you may omit the last step if all you want to do is disable compiz)

---

### Post by agamjain on 2010-07-08
> **arubislander said:**
> OK, did some testing in a virtual machine.

What happened is the following. You uninstalled Compiz without first disabling the Visual Effects (see my previous post). So the window manager that is in charge of drawing the window borders and such is no longer available. If you really don't want compiz installed the easiest way to go about it is:
1. reinstall compiz.
2. disable all Visual Effects in the Appearance Preferences dialog
3. uninstall compiz.

(Of course you may omit the last step if all you want to do is disable compiz)
I started facing certain more issues. Some programs stopped working altogether. So, I deleted the user account and created another one. But now the problem that I am facing is that my whole system has gone slow. Programs are taking a lot of time to load and open.

---

### Post by arubislander on 2010-07-09
What programs stopped working? Do these programs work now?

Are the programs just taking longer to draw on screen or is it overall slowness. Is some process taking up all your processor time?

Can you open a terminal and say ```
top
```

That should give you an idea what processes is hogging your CPU if that is the cause.

---

### Post by agamjain on 2010-07-09
Ubuntu Software Center had stopped working and so had Mozilla Firefox. Also I could not access any help files. Plus I could not open the Windows option in System panel. But when I deleted the account, things are working fine to a certain extent.
The windows are taking long to draw and the applications are running slower. Even the download speed has decreased.

---

### Post by arubislander on 2010-07-14
That's weird.

Maybe you could start a new thread asking about that, if you haven't already done so. This one is already marked solved, and I doubt there'll be a lot of folks looking at it who could help you.

---


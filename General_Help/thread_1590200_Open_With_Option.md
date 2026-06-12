---
title: "Open With Option"
date: 2010-10-07
forum: General Help
---

### Post by FahadMKS on 2010-10-07
When I try to open a file using the option "Open With" a lot of applications including the Wine applications is listed there.
I removed some of them using the button remove, but in case of the Wine Applications mentioned there, I am not able to do that.
The fact is that, I have uninstalled the Application WINE itself

---

### Post by WorMzy on 2010-10-07
Open nautilus and browse to ~/.local/share/applications, you can delete the erroneous/duplicate/defunct entries from there.

---

### Post by FahadMKS on 2010-10-07
Can you explain the steps, it is because I didnt get you correctly.

---

### Post by WorMzy on 2010-10-07
[LIST=1]
[*]Press Alt+F2
[*]Type ```
nautilus .local/share/applications
```
[*]Look at the list of files for the ones that you don't want and select them
[*]Press Del on the keyboard or right-click on the files and choose "Move to wastebasket"
[/LIST]

The wine applications will probably have names like "wine-extension-html.desktop".

---

### Post by FahadMKS on 2010-10-07
That was Awsome Dude....... that really worked.

Now I have the issue resolved.

Great Great thanks.

---


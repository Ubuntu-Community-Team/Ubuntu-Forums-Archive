---
title: "Opening an .sh file for installation"
date: 2010-10-13
forum: General Help
---

### Post by Sakomono on 2010-10-13
Hi. I am new to Ubuntu. I tried to install DrRacket on my computer, and it's an .sh file. Do any of you know how to go about doing this? I tried Gedit, and it couldn't detect the character encoding.

---

### Post by dino99 on 2010-10-13
it might be an installer, so try to double-click on that .sh file

[http://blog.gmane.org/gmane.lisp.scheme.plt](http://blog.gmane.org/gmane.lisp.scheme.plt)

---

### Post by 0N3 on 2010-10-13
In a terminal type:

chmod +x filename.sh

./filename.sh

---

### Post by Sakomono on 2010-10-13
> **dino99 said:**
> it might be an installer, so try to double-click on that .sh file

[http://blog.gmane.org/gmane.lisp.scheme.plt](http://blog.gmane.org/gmane.lisp.scheme.plt)

I double-clicked it, and it opens Gedit which then displays a message saying:

"gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

I tried the chmod +x, and it said the file could not be found.

---

### Post by 0N3 on 2010-10-13
Make sure you type the exact filename

---

### Post by 0N3 on 2010-10-13
if its in your downloads folder make sure to change the terminal directory

eg.. cd Downloads

---

### Post by dino99 on 2010-10-13
find it with nautilus "search"

---

### Post by 0N3 on 2010-10-13
where did you download the sh file to?

---

### Post by windfix on 2010-10-13
Or just right-click it, go to properties, and tick "Allow Executing File as Program" box under Permissions

---

### Post by Sakomono on 2010-10-13
Ahhh, thank you so much. It worked. I have a lot to learn.

Thank you very much, fine people.

---


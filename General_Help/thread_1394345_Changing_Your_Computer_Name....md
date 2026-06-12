---
title: "Changing Your Computer Name?..."
date: 2010-01-30
forum: General Help
---

### Post by VcDeveloper on 2010-01-30
During installation you were asked for a compture name.  How do you change this name after installation.  I'm using VBox and I did a clonehd and I need to change it.

---

### Post by Exp HP on 2010-01-30
I was wondering how to do this myself, so I looked it up.

[Here's what I found]("http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/").

To summarize what it says:

Type in the following command:
 gksudo gedit /etc/hostname
  After typing in your password, the **hostname** file will open in gedit, containing a single line: Your computer name. Change it, Save, and restart the computer.

---

### Post by VcDeveloper on 2010-01-30
Thank you very much!  I appreciate your help!

---

### Post by pbrane on 2010-01-30
you may need to edit /etc/hosts as well. There should be an entry like this:
```
127.0.0.1 your.hostname
```

---

### Post by VcDeveloper on 2010-01-30
Thanks pbrane!  I'm on it.....

---

### Post by mkp123 on 2010-05-12
[COLOR=black]Everyone wants to edit their computer name after using a name for a long time. During the time of installation of an operating system the software ask to enter the name of the computer. Then we enter a name and that is the name of our computer. The naming process of the computer is very important because if there contain a lot of such computers with same company, then there is a possibility of interchanging with them.[/COLOR][COLOR=black][FONT=&quot][/FONT][/COLOR]

---


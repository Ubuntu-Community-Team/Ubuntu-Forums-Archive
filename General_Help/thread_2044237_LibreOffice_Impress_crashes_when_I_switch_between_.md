---
title: "LibreOffice Impress crashes when I switch between tags in my workspace"
date: 2012-08-19
forum: General Help
---

### Post by jtantico1 on 2012-08-19
Hello all,

I'm using the 3.5 version of Libre Office and for some reason, I'm completely unable to switch between the workspace tabs (view buttons) in Impress. By default, Impress is in the Normal tab, which works fine. But, if I try to go into Outline view for example, the program immediately closes. I then get a window asking me if I want to file an error report. This happens anytime I try to switch views, so it definitely wasn't just a one time thing.

I searched the forums and saw that Impress has had several bugs. I couldn't find any example of this happening though, so I don't know if this is something that's wrong with the program or if it's something wrong with my system.

---

### Post by Rexilion on 2012-08-19
Start the program in a terminal and see if you get any crash output. You could use that information to look for any open bugs.

---

### Post by olsman037 on 2012-08-19
Did you try to uninstall libreoffice-gtk (or libreoffice-gnome) ? It solves the bug for me. Libreoffice is ugly now, but I can use it!

---

### Post by olsman037 on 2012-08-19
[https://bugs.freedesktop.org/show_bug.cgi?id=49191](https://bugs.freedesktop.org/show_bug.cgi?id=49191)

---

### Post by jtantico1 on 2012-08-28
> **Rexilion said:**
> Start the program in a terminal and see if you get any crash output. You could use that information to look for any open bugs.

How do I do this? Searching I was able to determine that a terminal is for running commands without using a GUI, but I don't know how to use it. Sorry, not super tech savy :p

---

### Post by jtantico1 on 2012-08-28
> **olsman037 said:**
> Did you try to uninstall libreoffice-gtk (or libreoffice-gnome) ? It solves the bug for me. Libreoffice is ugly now, but I can use it!

Same question as above... how I do I uninstall libreoffice-gnome? Sorry for the stupid questions and the prolonged delay. Even just guiding me to a link on how to do this would be great!

---

### Post by Rexilion on 2012-08-29
Open a terminal, and type:

```
libreoffice
```

press enter, and reproduce the issue. You can usually locate your terminal from the applications menu under tools or utility's.

To install an application, you need to fire up synaptics (I think...). Should be there in the application menu too...

---


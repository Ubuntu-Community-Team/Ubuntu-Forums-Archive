---
title: "Execute .EXE file without WINE"
date: 2011-09-27
forum: General Help
---

### Post by Einfachlacm on 2011-09-27
Hi,

I work in a company that develops applications for learning languages &#8203;&#8203;on Windows and Apple. We also need to adapt our applications (EXE) to the main Linux distributions (Ubuntu and Fedora & co). Is it possible to encapsulate the application EXE in Wine in a DVD so that the user must do nothing in addition to double click to open the application? The idea is that the user does not even have to install Wine just to put the DVD and double click on the file.

Do you have any ideas?

Thank you for your answers.

---

### Post by jwbrase on 2011-09-27
Well, you could include Wine on your DVD (no need to "encapsulate" the executable) and have a shell script that executes the *.exe using the Wine copy on the DVD. However, there may be licensing issues with Wine (since Wine is under the LGPL I *think* you should be fine, but I'm not certain of this).

---

### Post by Einfachlacm on 2011-09-28
Thanks for your answer jwbrase.

Do you know more precisely how can I do that or where can i get more information? I would be a good solution.

---

### Post by Mark Phelps on 2011-09-28
> **Einfachlacm said:**
> Thanks for your answer jwbrase.

Do you know more precisely how can I do that or where can i get more information? I would be a good solution.

Go to the Wine website [http://www.winehq.org/]("http://www.winehq.org/") and check there.

---


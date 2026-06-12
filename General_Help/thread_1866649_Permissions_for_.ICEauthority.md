---
title: "Permissions for .ICEauthority"
date: 2011-10-21
forum: General Help
---

### Post by kernco on 2011-10-21
After upgrading to 11.10, I couldn't log in to either Unity or KDE, both giving me an error that there were insufficient permissions to modify ~/.ICEauthority. Actually, I remember seeing this error when logging into the Gnome 2 desktop on 11.04, but I would just dismiss the dialog and it would continue normally.

I switched to a tty and saw that ~/.ICEauthority was owned by root and the permissions were -rw------.  So, with alarm bells sounding in the back of my head, I did chmod 777 on it.

So I can now log in. Yay. Now comes my questions. What is this .ICEauthority? Did I just open a massive security hole in my system? What was the right way to fix this?

---


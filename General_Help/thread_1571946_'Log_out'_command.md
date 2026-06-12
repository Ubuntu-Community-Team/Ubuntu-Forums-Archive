---
title: "'Log out' command?"
date: 2010-09-10
forum: General Help
---

### Post by Pipps on 2010-09-10
In the Application Finder menu there is an entry for 'Log out'. It is described as enabling 'log out from the xfce desktop'.

Executing this opens the window which gives options for shutdown, restart, suspend, hibernate, etc. 

What is the command for launching this 'log out' window?

I would like to be apply it to a custom keyboard command.

---

### Post by ubulal on 2010-09-10
xfce4-session-logout --logout
EDIT: That logs you out immediately! Without --logout it displays the selection dialog.

---

### Post by Pipps on 2010-09-13
That's brilliant! Thank you! :)

---


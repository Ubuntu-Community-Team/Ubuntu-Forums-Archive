---
title: "Su command and authentication failure"
date: 2011-05-09
forum: General Help
---

### Post by magodiafano on 2011-05-09
Hello I have a big problem... I have complete the installation of a program... and I need to use this command " su -c "make install" ".
The problem is that when I use the password it says "su: Authentication failure".
I tried to change the password in users and groups but it doesnt work... what's the problem?

---

### Post by mcduck on 2011-05-09
That's normal, "su" would require you to have root user's password, while Ubuntu doesn't enable loggin in as root so such password doesn't exist. Instead Ubuntu uses "sudo" (which asks for your password, not the target user's like "su" does).

Replace the "su" with "sudo" in your command ("sudo make install"), or use "sudo -i" to start a root session in a terminal.

Here's a great document to read: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Edit: I also highly recommend using Checkinstall when installing things from source, it makes your life a lot easier by turning the compiled program into a .deb package and installing that through the package management. Which means your compiled program can also be cleanly uninstalled using the package management tools... :) To use Checkinstall just install the "checkinstall" package, and when compiling programs run "sudo checkinstall" instead of "sudo make install".

---


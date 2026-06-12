---
title: "software notification -- no password required to install"
date: 2012-10-13
forum: General Help
---

### Post by Silvernail on 2012-10-13
I'm confused. Somewhere I have missed something in upgrading to 12.04.

When I click applications > software center and try to install an apt, I can not because I am not root. Use to be it would ask for password.

I have to got to a terminal and type 'sudo software-center' to install.

When I receive a software update notification and view the list, then click 'install', the changes are installed with out asking for a password.

I would like to have a GUI that ask for a password when I want to install something.

What do I need to reconfigure?
Dave

---

### Post by Rexilion on 2012-10-13
You can use gksu for this.

---

### Post by Cheesemill on 2012-10-13
This is a feature, not a bug :)

From 11.10 onwards you don't need your password to update already installed packages, you only need to supply a password to install new packages that don't currently exist on your system.

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)

---

### Post by Silvernail on 2012-10-13
Then the question becomes.
How do I enter a password when I click on 'Applications > Software Center' and have selected a new program to install?

The link was an interesting read. Explained some things I had wondered about.  Thanks

Dave

---


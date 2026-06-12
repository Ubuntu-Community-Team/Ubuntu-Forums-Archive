---
title: "Protecting the grub menu"
date: 2012-06-06
forum: General Help
---

### Post by community on 2012-06-06
I need to protect the grub menu shown at the boot up time from editing its contents.Can anybody post a method to do so?Better to ask for password while attempting to edit the same.

---

### Post by blackbird34 on 2012-06-06
Are you looking for [_this_]("https://help.ubuntu.com/community/Grub2#Password_Protection") ?

( [https://help.ubuntu.com/community/Grub2#Password_Protection](https://help.ubuntu.com/community/Grub2#Password_Protection) )

---

### Post by ashikthomas on 2012-06-07
[COLOR=#000000][FONT=Times New Roman]
Command: **password** username password

[COLOR=#000000][FONT=Times New Roman]Define a user named user with password clear-password.

[/FONT][/COLOR]
see [GRUB]("http://www.gnu.org/software/grub/manual/grub.html") [MANUAL]("http://www.gnu.org/software/grub/manual/grub.html")

[/FONT][/COLOR]

---

### Post by ashikthomas on 2012-06-07
What I did on my lap to make it secure was first put the grub password. Then I configured grub colors such that everything other than the menu is set to black/black color (hidden). Only the menu is set visible.

---

### Post by community on 2012-06-11
Thanks for that particular documentation link.

---


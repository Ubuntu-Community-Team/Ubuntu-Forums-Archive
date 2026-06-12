---
title: "wine"
date: 2012-05-28
forum: General Help
---

### Post by jmore9 on 2012-05-28
Anyone have any ideas on how i can access this folder ?  using Ubuntu 12.04

[email]jeff@jeff-desktop:~/.wine[/email]$ cd drive_c
[email]jeff@jeff-desktop:~/.wine[/email]/drive_c$ ls
Program Files  users  windows
[email]jeff@jeff-desktop:~/.wine[/email]/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
[email]jeff@jeff-desktop:~/.wine[/email]/drive_c$ cd Program_Files
bash: cd: Program_Files: No such file or directory
[email]jeff@jeff-desktop:~/.wine[/email]/drive_c$

---

### Post by fozturk on 2012-05-28
You can let auto complete to fill in the folder for you. 
After typing "cd " type the first two letters "Pr" (pay attention to capital letters) and press "Tab" key. It will automatically fill in the rest of the name. 
If you want to type it by yourself, It should be "Program\ Files" with a backslash before the space.

---


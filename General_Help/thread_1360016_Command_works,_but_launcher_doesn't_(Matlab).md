---
title: "Command works, but launcher doesn't (Matlab)"
date: 2009-12-20
forum: General Help
---

### Post by m4lte on 2009-12-20
Hi there,
I would like to create a launcher on my desktop for an application (matlab).

On the application website* they recommend the following syntax:
setsid ~/Applications/Matlab_2008/bin/matlab -desktop
If I enter this in a terminal, the applications starts like expected, however if I create a launcher on the desktop and enter this line in the "command" field, nothing happens when I click it.

What am I doing wrong??

* [http://www.mathworks.com/support/solutions/en/data/1-1B5ZV/index.html?solution=1-1B5ZV](http://www.mathworks.com/support/solutions/en/data/1-1B5ZV/index.html?solution=1-1B5ZV)


**SOLUTION**
I changed the command to just 
matlab -desktop
following advice from this website [http://www.mathworks.com/support/solutions/en/data/1-9A6FYK/index.html?solution=1-9A6FYK](http://www.mathworks.com/support/solutions/en/data/1-9A6FYK/index.html?solution=1-9A6FYK).
However I still wonder why the first command worked from the terminal but not from the launcher.

---

### Post by pbrane on 2009-12-20
try using the full path instead of ~ ( tilde ). i.e., /home/your_home_dir/Applications/...

the tilde expands to the current home directory of the user that called the command.

---

### Post by dcstar on 2009-12-20
> **m4lte said:**
> 
..........
However I still wonder why the first command worked from the terminal but not from the launcher.

Because the "Command Line" is a shell program that does a lot of things - including expanding "~" to the current user's home directory.

If you do not use the shell, you do not get its features.

---


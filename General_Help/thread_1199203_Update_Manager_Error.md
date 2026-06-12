---
title: "Update Manager Error"
date: 2009-06-28
forum: General Help
---

### Post by manji_kun on 2009-06-28
For some weeks i have been getting an error message when i try to run update manager, i check the status of the files and they seem to be fine, but i get the same message each time.

[SIZE=3]E: dpkg was interupted, you must manually run sudo dpkg --configure-a' to correct the problem.                                           [/SIZE]

can someone tell me what this means? and how i can get it to install properly?

---

### Post by WRDN on 2009-06-28
What happens if you run "sudo dpkg --configure-a" from the Terminal?

---

### Post by manji_kun on 2009-06-28
im pretty new to Ubuntu, i don't have the feel for it just yet, so i don't know my way around enough to do much of anything, except log on and browse the web.

---

### Post by michy99 on 2009-06-28
Click on Applications in the top left corner. Then click Accessories, then Terminal. Enter this command in the terminal:```
sudo dpkg --configure -a
```It will ask for your password. Type your user password in and press enter. (You will not see anything when you type it in.) If you get any errors, post them in a reply.

---

### Post by manji_kun on 2009-06-28
after that 

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
Name@ubuntu:~$ 

is what pops up

i've been pointing and clicking a little bit and i got to the dpkg force help window, but pointing and clicking could screw something up, and i'd rather not go back to windows.

---

### Post by Steelmourne on 2009-06-28
If you've run the command does update manager still show errors?

---

### Post by manji_kun on 2009-06-28
okay, i got it working, but apparently i have a "broken file" but everything else downloaded and everything downloading fine, thanks for the help guys, hope i'll be able to point and click till i figure out Ubuntu a lot more.

---


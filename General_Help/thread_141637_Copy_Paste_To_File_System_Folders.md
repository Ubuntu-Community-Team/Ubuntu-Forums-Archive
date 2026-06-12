---
title: "Copy Paste To File System Folders"
date: 2006-03-08
forum: General Help
---

### Post by noumaan on 2006-03-08
May be I sound way too stupid to ask such a silly question. But I am an absolute newbie into the computing world. I am trying to install a keyboard layout for my local language. The keyboard layout is offered by a well known institute. It is a simple text file called 'ur'. In the instructions I am told to copy paste this file into /etc/x11/xkb/symbols/ folder When I try to drage the file from Desktop to symbols folder I reciever an error stating that I do not have permission to write in this folder. 

In windows we use account for administrator and for other users. We usually solve such a problem by logging in our admin account. I know my root password, but the login screen that comes during startup doesn't accept root as the username. 

How do I copy paste this file and how do I deal with this situation in future.

---

### Post by Sutekh on 2006-03-08
Use **sudo** to do those things you want to do as root.

[Ubuntu Wiki - RootSudo](wiki.ubuntu.com/RootSudo)

Copying a file from your Desktop to /etc/X11/xkb/symbols/ using the terminal
```
sudo cp ~/Desktop/ur /etc/X11/xkb/symbols/
```~/ equates to /home/<your username>

(Cap sensitive, so check if its x11 or X11)

A note on using the terminal and tricky folder/file names.  Use the auto-completion capability by presing TAB.  Start typing the first one or two letters of the command and try pressing TAB.  If there is a unique file starting with those letters, TAB will finish the typing for you.

---

### Post by noumaan on 2006-03-08
Dear Sutekh

Thank you for replying so quickly. It worked, thanks a lot.

---


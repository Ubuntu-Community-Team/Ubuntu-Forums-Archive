---
title: "How to have a Local Install have Precedence Over a System Wide Install?"
date: 2012-01-05
forum: General Help
---

### Post by haziz on 2012-01-05
[SIZE=2]I have a shell account on a Linux server (running Ubuntu 8.04) with user level permissions (but no root priveleges). The system has Git 1.5.x installed. I wish to run a more current version of git. I can compile from source and install in my home directory but would like the git commands to invoke my local, more current install, rather than the older system wide installation of Git.
 
How do I go about doing this?
 
Thanks.
[/SIZE]

---

### Post by Paddy Landau on 2012-01-06
When you type a command, Linux searches the path for that command.

To find your current path, enter:
```
echo ${PATH}
```You will want to add your new Git folder to the front of the path (because Linux searches the path from left to right).

Let's assume your new folder is [FONT=Courier New][SIZE=2]/home/haziz/newgit[/SIZE][/FONT] for the purposes of illustration.

To add a new folder to the front of the path, use the following command:
export PATH="/home/haziz/newgit:${PATH}"

Where do you put this command? Well, if you want it only when you are using a terminal, edit your file [FONT=Courier New][SIZE=2]~/.bashrc[/SIZE][/FONT] (note the dot in the name) and add the command to very end. (You will have to close your terminal and reopen it.) If you want it throughout your session, not just in a terminal, edit your file [FONT=Courier New][SIZE=2]~/.profile[/SIZE][/FONT] and add it to the very end. (You will have to log out and in again.)

---


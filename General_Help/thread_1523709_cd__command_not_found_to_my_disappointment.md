---
title: "cd / command not found to my disappointment"
date: 2010-07-04
forum: General Help
---

### Post by Jart44 on 2010-07-04
Greetings,
I have an issue with the terminal command cd/ .
I have many downloads that I usually try to get from Synaptic Package Manager and Ubuntu Service Center. It seems I cannot access any cd/ command from the terminal. Here are some examples:

cuda@cuda-desktop:~$ sudo vim /etc/passwd
sudo: vim: command not found
cuda@cuda-desktop:~$ sudo cd~/Desktop
sudo: cd~/Desktop: command not found
cuda@cuda-desktop:~$ cd/
bash: cd/: No such file or directory
cuda@cuda-desktop:~$ sudo cd /
sudo: cd: command not found
cuda@cuda-desktop:~$ sudo cd / usr/local
sudo: cd: command not found
cuda@cuda-desktop:~$ sudo cd /var/www
sudo: cd: command not found
cuda@cuda-desktop:~$ sudo cd~ /Desktop
sudo: cd~: command not found
cuda@cuda-desktop:~$ 

Here is a variety of verified commands, that seem to work for others. I need access to them for a program I am running. Command to these files is never found. What am I doing wrong?

Thanks for lookin,

---

### Post by Elfy on 2010-07-04
Just use cd - no need for sudo.

cd ~/Desktop

and make sure there's a space after cd

---

### Post by balaknair on 2010-07-04
Insert a space after cd like in cd<space>directory_name, and do not use sudo or insert spaces in the directory path(like you seem to have done in *cuda@cuda-desktop:~$ sudo cd / usr/local* 
It should be 
*cuda@cuda-desktop:~$ cd /usr/local*
$ cd /
$ cd ~/Desktop
$ cd /usr/share/themes

To install vim type in
*sudo apt-get install vim*
and type in your password when prompted, or just use Ubuntu software Centre to install Vim

---

### Post by dcstar on 2010-07-04
> **forestpiskie said:**
> Just use cd - no need for sudo.

cd ~/Desktop

and make sure there's a space after cd

Yep, Linux is **not** DOS which does idiotic things like allowing commands without explicit delimiters.

---

### Post by gordintoronto on 2010-07-04
I think cd is an internal (built-in) command. Sudo works for external commands. You never need sudo to change to a directory.

---

### Post by Jart44 on 2010-07-04
Thanks all for the quick replies,
From balaknair >"Insert a space after cd like in cd<space>directory_name, and do  not use sudo or insert spaces in the directory path" did the trick!
Solved==

This forum never ceases to impress.

---


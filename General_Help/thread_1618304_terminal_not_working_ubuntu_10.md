---
title: "terminal not working ubuntu 10"
date: 2010-11-10
forum: General Help
---

### Post by pravypandu on 2010-11-10
Hi,can any one help me please,i am getting problem with terminal.when i am open the terminal getting error(There was a problem with the command for the terminal-text was empty or contain only white space)-help me please????:confused:

---

### Post by dino99 on 2010-11-10
can you write a command inside the terminal ? Are you using gnome or else ?

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by wojox on 2010-11-10
> **pravypandu said:**
> Hi,can any one help me please,i am getting problem with terminal.when i am open the terminal getting error(There was a problem with the command for the terminal-text was empty or contain only white space)-help me please????:confused:

Have you previously edited your profile?

---

### Post by pravypandu on 2010-11-10
No its not working just it show white blank screen.i am new to ubuntu

---

### Post by pravypandu on 2010-11-10
yes i am using gnome

---

### Post by garvinrick4 on 2010-11-10
When you hit ctrl/alt/F4 do you get the terminal.
ctrl/alt/F7 to get back to GUI

---

### Post by dino99 on 2010-11-10
reboot in recovery mode (hold "shift" key down at end of process bios to see the grub menu if its hidden)

if your new terminal windows hang, scrutinize your ~/.bashrc and ~/.profile files!

---

### Post by efflandt on 2010-11-10
Right click on Applications and click **Edit Menus**.  Click on Accessories > Terminal > Properties and see what it shows for Command: (typically **gnome-terminal**).

Or if the terminal opens, but complains, the window title is your system prompt (is terminal window title at top blank?).  Did you change anything in ~/.bashrc or ~/.profile or create a ~/.bash_profile?  In other words if you are able to open a terminal or go to a console (like Alt+Ctrl+F2 and login) what is shows for **echo $PS1** (typically **\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$** unless you changed that).

Note that if you do go to a text console, you can get back to X with Alt+F7.

---

### Post by garvinrick4 on 2010-11-10
If OP can get to terminal, can he not just log-in, purge,clean and reinstall gnome-terminal

---


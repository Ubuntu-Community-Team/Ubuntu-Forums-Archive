---
title: "Capture Synaptic Packages?"
date: 2011-02-03
forum: General Help
---

### Post by Lucrin on 2011-02-03
Ok this is kind of a weird question but say I installed Ubuntu on one computer and used the synaptic package installer to install all the software I needed. Now I wanna install Ubuntu on another computer and I want to set it up with the same software. So my question is, is there a way to export your current packages installed so you can import it to the new computer and have it install to match that "template" for lack of a better word? Thanks.

---

### Post by Sazhen86 on 2011-02-03
Hi

running dpkg --get-selections from the command line will give you a list of packages that are currently installed.  You can redirect the output to a file like this:

# dpkg --get-selections > package_list

On the other machine you should then be able to use 

# cat package_list | dpkg --set-selections  package_list

to set the selection state, followed by

# apt-get dselect-upgrade

to install the selected packages.

Note, you will need to be root or use sudo for the last two commands.

---

### Post by Lucrin on 2011-02-05
Thanks! :) Marked the thread solved.

---


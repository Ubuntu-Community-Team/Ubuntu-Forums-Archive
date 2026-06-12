---
title: "What happens I if issue a command twice?"
date: 2010-06-06
forum: General Help
---

### Post by dryder on 2010-06-06
Hi

A fairly basic question but one I am not able to check.

If, as an example, I issue a command:
sudo apt-get install build-essential libx11-dev libxi-dev
and it tells me xx bytes will be used,
and after that again:
sudo apt-get install build-essential libx11-dev libxi-dev
and again it tells me xx bytes will be used, do I get a second installed copies or does it overwrite what I did first?

Many thanks for answering this elementary question.

David

---

### Post by sparklyprgs on 2010-06-06
Unless I'm missing something, if you've already successfully installed the packages from the first command, the second command should output something like:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
etc

---

### Post by ajgreeny on 2010-06-06
I think you may need to close the terminal and reopen it before it is aware that the application is already installed.  This is rather like making changes to your .bashrc file that affect terminal sessions,eg adding another alias, if that is where you keep them, but are not shown in the terminal until you close and reopen.

Of course, I could be wrong!

---

### Post by dryder on 2010-06-07
Hi,

I have closed terminal and re-opened it. But it did not say:
build-essential is already the newest version.

Just did it.

Hence the question ... :P

David

---

### Post by dino99 on 2010-06-07
good point, i've not paid much attention to this missing comment, but i think you have found a bug, report it on launchpad against apt:

ubuntu-bug apt

---


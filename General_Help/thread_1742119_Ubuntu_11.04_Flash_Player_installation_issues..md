---
title: "Ubuntu 11.04 Flash Player installation issues."
date: 2011-04-28
forum: General Help
---

### Post by Zach G on 2011-04-28
Hi, I've just installed Ubuntu 11.04, and now I'm trying to install Adobe Flash Player.
Buuuuuuuut, I seem to be having problems, when I go in and try to install it through Ubuntu Software Center, as soon as I hit install, I get this..

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details;
The following packages have unmet dependencies:

flashplugin-installer: Depends: ia32-libs (>= 2.2ubuntu18 but it is not going to be installed


So, what exactly do I have to do to get this working?

---

### Post by Zach G on 2011-04-28
Someone, please help...

---

### Post by Zach G on 2011-04-28
SOLVED.

Using the commands.

sudo add-apt-repository ppa:sevenmachines/flash                                   and
sudo apt-get update && sudo apt-get install flashplugin64-installer

---

### Post by madjr on 2011-04-28
or just install flash  from software center, works well

---

### Post by oldos2er on 2011-04-28
Only 32-bit flash is available in the repositories.

There's also FlashAid, which installs the proper flash version for your architecture. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by befranken on 2011-08-07
Thank you Zach G!!!

Solved it for me.

---

### Post by Spyderkid on 2011-08-07
TOP TIP....

install ubuntu restricted extras from the software centre, it has all these thing that you will need like flash palyer, MP3 support etc....

---


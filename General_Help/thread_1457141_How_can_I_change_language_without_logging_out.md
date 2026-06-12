---
title: "How can I change language without logging out?"
date: 2010-04-18
forum: General Help
---

### Post by JustSomeGuy805 on 2010-04-18
Hello, I need a little assistance. I need to create a simple way to change the language of my system without logging out.  I would like to make it so that a user can just click on something and the language of the whole system will change.

I've disabled the traditional gdm gui login screen by adding the keyword 'text' to the kernel line so that it boots to a command line. I then start gnome by using startx and I've noticed that I can log out of gnome back into the command line, then change the environment LANG variable to the new desired language, run startx again and everything is in the new desired language.

I need a programmable way to only restart gnome(not a reboot) so that I can make a script that a user can just click on and it will set the LANG variable then restart gnome(*preferably* preserving all open applications, but if not, doesn't matter). Any help or suggestions would be appreciated. Thanks.

Also, maybe there is a program already out there that will do this for me that someone could suggest?

---

### Post by JustSomeGuy805 on 2010-04-18
anyone?

---


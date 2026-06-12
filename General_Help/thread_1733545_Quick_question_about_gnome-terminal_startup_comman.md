---
title: "Quick question about gnome-terminal startup commands"
date: 2011-04-19
forum: General Help
---

### Post by Nethos on 2011-04-19
I would like to set up a command to run when I start up the terminal, but have the terminal stay open for use when it's finished. I was trying to get my terminal to run *fortune* whenever I start it just for cosmetic value, so I tried changing the launcher command to *gnome-terminal --command=fortune*, but that makes it just output the fortune result and then terminate. Any way to keep the window open?

Thanks in advance for any help!

---

### Post by hwttdz on 2011-04-19
I think you can put it in one of your .bashX files.  i.e. .bashrc, of course then it would run any time you open a new tab.  You could get clever with scripting and see if it's run since login, and don't if it already has.  

Anyways, have a gander here: [http://www.thegeekstuff.com/2008/10/execution-sequence-for-bash_profile-bashrc-bash_login-profile-and-bash_logout/](http://www.thegeekstuff.com/2008/10/execution-sequence-for-bash_profile-bashrc-bash_login-profile-and-bash_logout/)

---


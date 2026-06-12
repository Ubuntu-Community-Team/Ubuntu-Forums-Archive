---
title: "Autofs and encrypted home directory in 9.10"
date: 2009-11-06
forum: General Help
---

### Post by the_tazinator on 2009-11-06
With my recent install of 9.10 I chose the option of encrypting my home directory. In doing this I noticed that now autofs does not start when I log in. I can start it by doing sudo /etc/init.d/autofs start and everything works fine. Since this was a fresh install, I wiped out the machine and reinstalled without encrypting the home dir and again configured autofs the same way. Everything worked great and I didn't need to start autofs after I logged in. I then encrypted the home dir the way I use to do it by using ecryptfs and autofs still worked fine.

Now to try to fix the known problem. I again did a fresh install of 9.10 with the home dir encrypted with the option during installation. Again, I configured autofs, rebooted and autofs did not start when I logged in.

Any ideas? I just started work on this so if I find any other info I will be sure to provide updates.

---

### Post by the_tazinator on 2009-11-06
I figured it out. When I was using ecrpytfs, it was not encrypting the entire contents of my home directory where as if I use the auto encryption during installation it does encrypt the entire home directory, including my autofs config file. oops. I created a dir called /foo and moved my config file to it and everything works again.

For those who may be running something similar, I also have a credentials file that stores the user and pass that I am able to keep in the home dir so it is encrypted and locked to only my user account.

---


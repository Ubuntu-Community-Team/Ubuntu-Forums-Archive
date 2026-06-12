---
title: "no internet, no root password"
date: 2006-02-17
forum: General Help
---

### Post by mistshadow2k4 on 2006-02-17
Kubuntu worked great as a live cd and I had no problems. But as soon as I went to install it to my hard drive it became a different story. First off, it failed to configure my adsl connection, something it had virtually no trouble with running as a live cd. Then after I clicked "do not configure the network at thsi time" I had to input a name for the computer and a user account. There was no way to give it a root password. Once it finished installing I couldn't sudo root! Naturally I couldn't configure my ethernet card either as I couldn't become root - there was no root on the system. Any ideas on how to fix this?

---

### Post by gingermark on 2006-02-17
Have a look here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Basically sudo a command and use your password. Same goes for when you're asked for your password in Control Centre or whatever - use the user and password you set up on install.

There is also a section on that page for reverting back to a "traditional" root account.

---

### Post by Jucato on 2006-02-17
you can also try to configure your ADSL through:
```
sudo pppoeconf
```
in a terminal.

---

### Post by mistshadow2k4 on 2006-02-18
Thanks, guys. :)

---


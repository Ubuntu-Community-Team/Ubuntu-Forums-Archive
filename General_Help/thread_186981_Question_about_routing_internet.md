---
title: "Question about routing internet"
date: 2006-06-02
forum: General Help
---

### Post by scpike on 2006-06-02
This is kind of a random question and probably something that could be answered for any linux distro in the same way, but I'm using dapper so I figured the best help would be here.

Ok so this laptop has dapper installed, and connects to my home wireless network just fine. What I want to do is emulate the functionality of a router within the laptop, and be able to connect a tower via ethernet cable to the laptop and share the wireless connection with it.  The tower doesn't have a wireless card, but i do have extra ethernet cables laying around.  Is this possible? If so how would I do it.  thanks

---

### Post by Ramses de Norre on 2006-06-02
Firestarter can be used to configure this, in firestarter pick edit > preferences > network settings.
I never used it myself so I can't tell you how exact to do it (DHCP would be the easiest I guess, turn on the second ethernet card in network-admin too).

---

### Post by scpike on 2006-06-02
when I try to run firestarter i get
> A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.

so i tried
> sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
firestarter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up firestarter (1.0.3-1.1ubuntu4) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)


so any help on this would be appreciated, also do i need a crossover ethernet cable or can ubuntu handle switching it in software so a regular cable is fine.

---

### Post by Jason_25 on 2006-06-02
Check out this thread from yesterday.  You don't need firestarter.

[http://www.ubuntuforums.org/showthread.php?t=186156&highlight=masquerade](http://www.ubuntuforums.org/showthread.php?t=186156&highlight=masquerade)

---

### Post by scpike on 2006-06-02
but I do need a crossover cable instead of a regular ethernet cable?

---

### Post by Jason_25 on 2006-06-02
If your not using a hub or a switch between them, then generally you will need a crossover cable.  On more modern ethernet cards, I think you can use a regular ethernet cable because the cards are capable of reversing the wiring internally.  Try it and see, it couldn't hurt.

---


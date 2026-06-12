---
title: "Possible unmet dependencies"
date: 2012-05-13
forum: General Help
---

### Post by kjbox on 2012-05-13
I am new to ubuntu (using 12.04 on an Asus zenbook UX31, dual boot with windows 7).

I have been trying to set a web address protocol to be associated with a paticular programme that runs under wine. Things went a bit wrong and I ended up having to un-install and re-install Firefox. Still can't get the association setting right - but that will be the subject of a later question!

Not sure if what I did is the cause of my current problem but, on start-up I have strted to get an error icon in the task bar. It says:

"An error occured, please run Package Manager from the right click menu or apt get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Encounted a section with no Package: header, E:Problem with mergelist/var/lib/apt/lists/archive.ununtu.com_ubuntu_dists_precise_universe i18n_Translation-en, E:The package lists or status file could not be parsed or opened.). This usually means that your installed packages have unmet dependencies."

I cannot find Package Manager in any right click menu and could not runit from a terminal.

Clicking 'Show Updates' option in the error message gave the same error information under a cation "Could not initialize the package information"

When I try to open Ubuntu Software Center or Ubuntu One the window appears for a second or so then disappears and is replaced by an option to send a report of the crash. When I try to send the report I get a window saying reporting failed as the package source could not be determined.

Firefox and everything else seems to work ok.

Help please on how to find out what dependencies are unmet and how to correct the problem.

Thanks in advance

---

### Post by zvacet on 2012-05-14
Of course you can not find package manager because it is not there.I don´t know who give this "smart idea" but package manager is not on CD any more.You will have to install it by typing in terminal

```
sudo apt-get install synaptic
```

I think you will not be able to install it until you solve your current problem.Run in terminal

```
sudo apt-get -f install
```

That should fix your problem.After that install synaptic.

---


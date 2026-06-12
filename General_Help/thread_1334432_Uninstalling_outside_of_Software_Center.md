---
title: "Uninstalling outside of Software Center"
date: 2009-11-22
forum: General Help
---

### Post by Nanofuture on 2009-11-22
General question:  how do you uninstall a program that you did not install through the software center?  Should I just delete all the files for the program or is there a particular extension that I should be looking for?  Note:  I am running 64 bit Ubuntu 9.10.

---

### Post by fluxbuntu on 2009-11-22
sudo aptitude purge $(deborphan --find-config)
this will purge all old config files for old programs

You may need to install deborphan via apt-get before running this. 

If you compiled something from source and this doesn't work, then yes, delete the installed files.

---

### Post by emigrant on 2009-11-22
eventhough you didn't install through software center, i belive you still can remove them from the software center. 
or else you can remove from the command line:

[http://www.cyberciti.biz/faq/howto-delete-remove-software-using-apt-get-command/](http://www.cyberciti.biz/faq/howto-delete-remove-software-using-apt-get-command/)

---

### Post by fragos on 2009-11-22
I'd recommend Synaptic which can be installed from the software center.

---

### Post by SuperSonic4 on 2009-11-22
```
sudo make uninstall
``` works on nice code but you'll still need to ```
rm -rf '/dir/of/program/' '/dir/of/settings'
```

As usual be *very* careful with rm

---

### Post by Nanofuture on 2009-11-22
When I go into the package manager / terminal and search packages the only packages I see for the program are from the software center's install packages (this is the reason why I want to remove what I currently have installed:  the same program is available supported from the software center).  More specifically, I am trying to uninstall Nexuiz and I see the following packages in the package manager: nexuiz, nexuiz-music, nexuiz-data, nexuiz-server, nexuiz-server-dbg, and nexuiz-dbg.  When I search through the terminal using dkpg --list I do not see anything with nexuiz in it.

---


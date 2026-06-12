---
title: "uninstalling question!"
date: 2006-02-23
forum: General Help
---

### Post by KCMiller3 on 2006-02-23
If i have installed a program by ./configure, make, and make install....what do i need to do to uninstall it? 

After I installed the program i deleted the original folder that I expanded the tar file into (and also configured and made).  Was i not supposed to do this or is there another folder to run "make uninstall" from?  Is the easiest thing to do just redownload the tar file and reconfigure it and the remake it and then do the uninstall?  What am i missing here?  Thanks for the help in advance. 

~Kevin

---

### Post by nanotube on 2006-02-23
hey
i suppose doing what you say and 'make uninstall' (if that is even available - it may not be) is the best thing at this point.

but for the future - install package "checkinstall" from synaptic, and then after you build, instead of "make install" use "checkinstall". this tool will keep track of what files are installed, and enable you to subsequently uninstall the program using synaptic/apt-get! magic! :)

---

### Post by nanotube on 2006-02-23
hmm, actually, you could probably even use checkinstall to uninstall this one - just reinstall it with checkinstall, and then uninstall the package with synaptic.

---

### Post by KCMiller3 on 2006-02-23
you are awesome...just the advice i needed.  thank you so much!

~Kevin

---


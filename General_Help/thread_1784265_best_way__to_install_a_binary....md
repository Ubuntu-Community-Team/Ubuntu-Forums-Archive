---
title: "best way  to install a binary..."
date: 2011-06-16
forum: General Help
---

### Post by nethero on 2011-06-16
I just compiled john the ripper and I have the binary files in a folder on my desktop.  According to the installation instructions included with john the ripper, I don't do sudo make install; I just run the application from this folder.  So my question is....

What is the best way to install these?  Should I make a folder named "Applications" in my home folder and keep it there?  I should just manually copy this to /usr/bin, right?  Thanks.

---

### Post by sisco311 on 2011-06-16
[uhelp]community/CheckInstall[/uhelp]

---

### Post by wildmanne39 on 2011-06-16
> **sisco311 said:**
> [uhelp]community/CheckInstall[/uhelp]
Hi, thanks for the link that looks like a great program.

---

### Post by nethero on 2011-06-17
Thanks for telling me about that program sisco311.  However, there is no sudo make install step for this program.  [Here is a link]("http://www.openwall.com/john/doc/INSTALL.shtml") about how to compile/use john the ripper.  All you do is type "make clean <system here>".  If I compile and try to install using sudo checkinstall, I get this message...
```

make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

---

### Post by sisco311 on 2011-06-17
Oh, I see... It's a single binary. I keep my scripts in ~/bin (bin directory in my home). If memory serves, if ~/bin exists, it's added automatically to the PATH. But if you want to *install* it system wide, then simply copy it to /usr/local/bin.

---

### Post by nethero on 2011-06-18
Okay.  Thanks for the information.

---


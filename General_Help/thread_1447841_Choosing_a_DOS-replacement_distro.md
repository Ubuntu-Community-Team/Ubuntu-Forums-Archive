---
title: "Choosing a DOS-replacement distro"
date: 2010-04-05
forum: General Help
---

### Post by Pingster on 2010-04-05
I'm looking for a Linux distro that I can use instead of DOS for speed and flexibility.  These are the main features I'm looking for.


[LIST]
[*]Boots directly to a command line
[*]Easy to install to hard drive
[*]Small, fast, etc.
[*]Has standard programs, especially bash, gcc, and Vim
[*]Live media
[/LIST]
What are the pros and cons of the distros you've used like this?

---

### Post by mickObrian on 2010-04-05
I'd recommend Arch, it installs with just the terminal, no desktop environment and you build it from there, it has great documentation such a beginners guide ([http://wiki.archlinux.org/index.php/Beginners%27_Guide](http://wiki.archlinux.org/index.php/Beginners%27_Guide)) and a giant user repository, I'd try it out.

---

### Post by kmsalex on 2010-04-05
there's also free DOS
[http://www.freedos.org/](http://www.freedos.org/)

---

### Post by Pingster on 2010-04-06
I downloaded Arch Linux and it's very close to what I want.  I'm so glad you suggested it.  I love their philosophy of simplicity and the fact that it has no official GUI.

The only thing lacking in Arch is gcc.  The OS I use is not going to be connected to the internet so it needs to have bash, gcc, and Vim preinstalled.

---

### Post by MisfitI38 on 2010-04-06
> **Pingster said:**
> ..The only thing lacking in Arch is gcc..

GCC is in there. It is not lacking; you are mistaken.
Bash is the default shell. And, Vi is included with many vim-like features by default.
Looks like you're all out of excuses. ;)

---

### Post by Pingster on 2010-04-06
It's easily possible that I'm mistaken.
In Ubuntu, to compile a .c file I use** cc** *myprogram.c*
From the Arch live CD the **cc** command is invalid.  Am I complaining about the wrong thing?

---

### Post by MisfitI38 on 2010-04-06
GCC will be installed if the base-devel group is selected during installation..this should work on both the core and netinstall images.
Do you need cc in the live environment?

---

### Post by dominiquec on 2010-04-06
You could also install Ubuntu as a minimal command-line system only.

---

### Post by Pingster on 2010-04-07
> GCC will be installed if the base-devel group is selected during  installation..this should work on both the core and netinstall images.

> You could also install Ubuntu as a minimal command-line system only. 	

Good tips.
I guess I wasn't very clear in my first post.  I would like to be able to use gcc on the live CD.

---


---
title: "where to put software libraries that I manually compiled"
date: 2011-06-23
forum: General Help
---

### Post by quickk on 2011-06-23
Hi everyone, 

    I was wondering if there was some sort of standard as to where I should put software libraries that I manually compile. For example, I want to use[this minimum perfect hash library]("http://sourceforge.net/projects/cmph/").   By default, "make install" will put the library files in /usr/local/lib.   However, whenever I do a clean install of the OS, I have to recompile and reinstall.   Is there a standard way of getting around this?

For example, can I use the ~/.local folder for this purpose?   

Does anyone know of a good resource that I can use to learn more about ubuntu's various configuration files, folder structure, etc?

Thanks!

---

### Post by gizmo720 on 2011-06-23
/usr/local is the standard place to put programs that aren't part of the system. I don't think there is any standard of where to put it in your home directory, but most people I know create ~/bin. As long as you add it to your path variable, it does not matter where you put it.

---

### Post by idoitprone on 2011-06-23
In some cases people put it in /opt 

that is the folder just for manually compiled programs
change your .bashrc to include the folder in your $PATH

---

### Post by quickk on 2011-06-23
Thank you for the suggestions.  I will put my programs in /opt, as this is where my compilers install themselves too.   

On a side note, is there a way to specify in my bashrc where I put shared library files?   Currently, I add a line to /etc/ld.so.conf and then run ldconfig, but then I would have to redo this if I reinstall the OS.

---


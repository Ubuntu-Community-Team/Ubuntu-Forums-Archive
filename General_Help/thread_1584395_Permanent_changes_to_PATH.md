---
title: "Permanent changes to PATH"
date: 2010-09-29
forum: General Help
---

### Post by arnie001 on 2010-09-29
Hello

I have recently installed NS2, a network simulator. After installation, I need to add append some directory locations to PATH environment variable. Apparently, this can be done temporarily by doing-

PATH=$PATH:/home/pereira/Downloads/ns-allinone-2.34/bin:/home/pereira/Downloads/ns-allinone-2.34/tcl8.4.18/unix:/home/pereira/Downloads/ns-allinone-2.34/tk8.4.18/unix

However on restarting the terminal, these additions will not be there. How do I make the changes permanent? On some Google search, some suggestions were to make changes to bash_profile or .profile located in home directory(Could not find this one).

Secondly, I have to add some variables permanently to env. I did this temporarily by

LD_LIBRARY_PATH=/home/pereira/Downloads/ns-allinone-2.34/otcl-1.13:/home/pereira/Downloads/ns-allinone-2.34/lib
export LD_LIBRARY_PATH
TCL_LIBRARY=/home/pereira/Downloads/ns-allinone-2.34/tcl8.4.18/library
export TCL_LIBRARY 

and then typing env reflects these changes. How to make these additions permanent? 

Thanks in advance.

---

### Post by lloyd_b on 2010-09-29
The best place for per-user customization is in the file ~/.bashrc.  Just modify the PATH in there (followed by "export PATH").

This is also the proper place for those other environment variables.

Note that changes will not be reflected immediately after changing .bashrc - you'll need to close the terminal window and open a new one before the changes take effect.

Lloyd B.

---

### Post by WorMzy on 2010-09-29
You can make system-wide changes to PATH by adding what lloyd suggested to /etc/environment.

e.g.
```
PATH=$PATH:/usr/local/bin
export PATH
```

I'm not too sure about the "export PATH" part. It may or may not be necessary, but it doesn't hurt to include it anyway.

---


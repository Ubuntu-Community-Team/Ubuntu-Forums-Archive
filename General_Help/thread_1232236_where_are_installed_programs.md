---
title: "where are installed programs"
date: 2009-08-05
forum: General Help
---

### Post by franar on 2009-08-05
hi people, a simple question. setting up the avant navigator i got to include my applications manually, but i don't know where ubuntu install aplications (like c:\programs files\ in windows

---

### Post by Scienceman123 on 2009-08-05
Generally in /usr. Alternately, enter "which <program>" in a terminal without quotations.

---

### Post by credobyte on 2009-08-05
Almost all applications can be found @ [COLOR=Blue]/etc[/COLOR] ( eg. [COLOR=Blue]/etc/apache2[/COLOR] ) !

---

### Post by Cheesemill on 2009-08-05
> **credobyte said:**
> Almost all applications can be found @ [COLOR=blue]/etc[/COLOR] ( eg. [COLOR=blue]/etc/apache2[/COLOR] ) !
 
No they're not. The configuration files are in /etc, the binaries are usually in /usr/bin

---

### Post by slakkie on 2009-08-05
dpkg -L package_name tells you where stuff has been installed by the application. config, libs, binaries, etc.

---

### Post by credobyte on 2009-08-05
> **Cheesemill said:**
> No they're not. The configuration files are in /etc, the binaries are usually in /usr/bin

Application files can be all over the root ( / ) directory ( with a few exceptions ), so .. depends on what you need ( Avant .. dock ? ).

---

### Post by franar on 2009-08-05
thanks for the help.
i need to know where are the installed programs by me. like VLC player, Amarok etc etc. not necesary the system programs

---

### Post by credobyte on 2009-08-05
You can try finding it with:
```
whereis <name>

```

---

### Post by franar on 2009-08-05
thanks You all

---

### Post by mcduck on 2009-08-05
> **franar said:**
> thanks for the help.
i need to know where are the installed programs by me. like VLC player, Amarok etc etc. not necesary the system programs

Unlike in Windows, Linux doesn'ät installk programs into singl directory. Instead files are put into different places based on the file's purpose. For example you'll find system-wide configuration files in /etc, icons and images in /usr/share/pixmaps and /usr/share/icons, all documentation for your programs in /usr/share/doc and so on.

Anyway, pretty much every user-level program will install it's executable file in /usr/bin. So that's where you'll find all the executables  for your launchers.

***

If you need to find where programs are located you can use the "whereis"-command credobyte suggested, and it will list all the directories where that program has files. Or if you just need to find the executable, use the "which"-command and it will tell you exactly that. Although, like I said, you'll almost always find the executable in /usr/bin anyway.. ;)

---

### Post by slakkie on 2009-08-05
> **mcduck said:**
> Unlike in Windows, Linux doesn'ät installk programs into singl directory. Instead files are put into different places based on the file's purpose. For example you'll find system-wide configuration files in /etc, icons and images in /usr/share/pixmaps and /usr/share/icons, all documentation for your programs in /usr/share/doc and so on.

Anyway, pretty much every user-level program will install it's executable file in /usr/bin. So that's where you'll find all the executables  for your launchers.


That is NOT true. ./configure --prefix=/path/to/stuff and it will make install everything in /path/to/stuff. You can add several prefixes to the configure line to define where binaries go, where lib stuff goes, where manpages go, etc etc. I can install vmware in /opt/vmware and make sure it does not put files elsewhere.

Non-root users can install programs in their homedir, and use them. I can compile FF3.5 as a user if my admin doesn't want to install it system wide. I can use my homedir, eg /home/myuser/firefix.

---

### Post by mcduck on 2009-08-05
> **slakkie said:**
> That is NOT true. ./configure --prefix=/path/to/stuff and it will make install everything in /path/to/stuff. You can add several prefixes to the configure line to define where binaries go, where lib stuff goes, where manpages go, etc etc. I can install vmware in /opt/vmware and make sure it does not put files elsewhere.

Non-root users can install programs in their homedir, and use them. I can compile FF3.5 as a user if my admin doesn't want to install it system wide. I can use my homedir, eg /home/myuser/firefix.

I didn't say it would be *impossible* to install things into a single directory, of course that's possible. But it's not happening as long as you use any package management tools, and I really, really doubt the OP was asking about compiling programs.. :D

So, unless you specifically decide to install things differently, they will be put into standard locations, just like I said.

---


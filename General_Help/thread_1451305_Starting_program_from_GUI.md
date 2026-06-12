---
title: "Starting program from GUI"
date: 2010-04-10
forum: General Help
---

### Post by Filippo Neri on 2010-04-10
Hi,
I am totally green to Ubuntu.
How is it possible to start program from Nautilus?
Can I start programs from GUI or just from the command line?
 
Thanks in advance

---

### Post by RudolfMDLT on 2010-04-10
Your question is a little vague? :)

What program do you want to start in nautilus?

Depending on the program and your version of Ubuntu, by pressing ALT + F2, you can open the run dialog, and all commands you entered in terminal should work... but I'm not sure that's what you are asking.

Post back,

Rudolf

---

### Post by Filippo Neri on 2010-04-10
For example I've downloaded the install program of VMware Player. This program has a .pl extension. In the Windows world I can install VMware player if I double click the install.exe in Windows Explorer and the install starts immediately. 
 
I just wanted to know if is it possible to start a program from Nautilus or it can be done only from the command line.

---

### Post by warfacegod on 2010-04-10
Look for programs with the .deb file extension. Those behave essentially like .exe files for Windows.

---

### Post by howefield on 2010-04-10
Try opening a terminal, (Applications > Accessories > Terminal) and type

```
./vmware-install.pl
```

This should start the vmware installer, follow the questions to the end.

---

### Post by Gunman1982 on 2010-04-10
> **warfacegod said:**
> Look for programs with the .deb file extension. Those behave essentially like .exe files for Windows.
They behave more like the .msi (microsoft software installer) files. 

Executable files don't have to have an ending like .exe .bat .com or whatever, it depends on the executable permission bit. You can set that via right-click on the file, properties->permissions and ticking the executable checkbox.

Easiest way to use programs in ubuntu is: Check the software center if it is available there, install it, start it by using the starter in the application menu.

---

### Post by howefield on 2010-04-10
Just in case you are unaware, you might also want to look at Virtualbox, a virtual machine application similar to vmware, but installable via Synaptic Package Manager, (or by downloading the .deb package from virtualbox.org

---

### Post by warfacegod on 2010-04-10
> **Gunman1982 said:**
> They behave more like the .msi (microsoft software installer) files. 

Executable files don't have to have an ending like .exe .bat .com or whatever, it depends on the executable permission bit. You can set that via right-click on the file, properties->permissions and ticking the executable checkbox.

Easiest way to use programs in ubuntu is: Check the software center if it is available there, install it, start it by using the starter in the application menu.

The bottom line is this: double clicking a .deb in Ubuntu will generally install it. Just like double clicking an .exe file in Windows will also generally install it.

I don't think I ever installed anything in Windows that wasn't an .exe unless it was an update Hotfix which were .msi, if memory serves.

---

### Post by RudolfMDLT on 2010-04-10
LOL! :)

How stuff gets installed on Ubuntu:

1) deb packages: Really nice little files you download, double click, enter your password and bingo. :) If the program needs something extra - called a dependency, usually this gets installed automatically aswell if it can be found. You can download debs manually, or you can search the Ubuntu library of programs - called a repository - using apt, Synaptic or the software install utility.

2) Source Compilation: By downloading the source code and compiling from source, the program that you need. -> done in terminal,

3) Script Compilation: That isn't the official term, but as far as I know how some apps install. VMware is one of them. VMware uses a program called a script to do a "customized" install on your system. Sometimes these scripts are used to set variables at compile time that you would have to set by hand otherwise. -> done in terminal.

4) Java "executables": Some programs are "interpreted", not compiled or "installed". You just run them from where they are. The Mozilla email client and organizer are such applications. Download the zip file, extract, and run the program.

Although the above isn't technically correct it should  give you some head way on what to expect.

Post back if you have any issues. :)

Rudolf

PS: Coming form a windows world, if you have some spare time, google batch files, and see what handy things you can do in windows using scripts. In terminal, you are actually in an environment called BASH - Born Again SHell - and scripts are just a recipe of commands that BASH executes.

---

### Post by Filippo Neri on 2010-04-11
Thanks for the detailed explanation.
Ubuntu is totally different from Windows but it is interesting :P

---

### Post by bobbob94 on 2010-04-11
Especially being new to ubuntu, I'd recommend installing things through the ubuntu software centre option in the menu wherever possible. It might not have everything you need but it'll definitely have most things you need, and doing it that way is just a case of clicking the install button.

---

### Post by bbqau on 2010-04-11
forgive me if this is a little late, but if the file is .pl extension then that means its perl correct ?

so to launch it wouldn't you need to run via terminal perl file.pl ?

---

### Post by RudolfMDLT on 2010-04-11
Yes, you could run it in terminal, but nautilus does support running scripts: [http://linuxhelp.blogspot.com/2006/05/running-scripts-from-within-nautilus.html](http://linuxhelp.blogspot.com/2006/05/running-scripts-from-within-nautilus.html)

Rudolf

---


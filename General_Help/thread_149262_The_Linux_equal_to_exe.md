---
title: "The Linux equal to exe?"
date: 2006-03-23
forum: General Help
---

### Post by MetalMike on 2006-03-23
One thing I am having a hard time wrapping my head around is the Linux equivalent of Windows exe’s. I download applications, decompress them, then what – is there a single file that will launch the app? A friend of mine told me online that there really isn’t an equivalent but then he disconnected. My question stands, wtf?

---

### Post by aysiu on 2006-03-23
There isn't really an equivalent.

First of all, in Windows a setup.exe is something that you download separately--then you double-click it to install the program.

Finally, there's a program .exe that you use to launch the program.

In Ubuntu, you generally install programs using apt-get or Synaptic Package Manager, and everything is downloaded and installed for you (not separate setup.exe).

Once a program's installed, it has an executable binary that lives in /usr/bin or /usr/sbin. You don't need to know where it lives, though. You can just run it from Alt-F2 (the "Run" dialogue) by just typing the name of the application (*firefox*, for example).

That's the same as in Windows, actually. In Windows, I can do Win+R and type *firefox* and Firefox will launch. I don't have to go C:\Program Files\Mozilla Firefox\Firefox.exe

For more info, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Q4U on 2006-03-23
Think of it in this way:

In Linux (better: in Debian and derivatives like Ubuntu) the software comes distributed in .deb packages that need to be installed in your system with the classic command: sudo dpkg -i name-of-package.deb. This command will unpack (you would say unzip in windows) the software package, install various files in the system so that your system can start the program once you invoke it (either via the command line or by clicking on the menu item, if it creates one).

So there is only one additional step, the installation. This in windows can sometimes be skipped (for the simpler programs), but not always. Hope this clarified the matter a little. Q

---

### Post by Barrakketh on 2006-03-23
> **MetalMike]One thing I am having a hard time wrapping my head around is the Linux equivalent of Windows exe&#8217 said:**
> 
It depends.  If you download a source archive, there is no executable in them.  If you download a pre-compiled application, you generally "know" they are executable.  If you're not sure whether it is or not, you can use the "file" command on the file.  It'll return something like this:
> /usr/bin/k3b: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
Note that applications need to have the executable bit set to be launched (most archives have them set that way).

Another thing to know is that scripts written in Python, Ruby, Perl, etc. can be executed like you think is an ".exe".  The first line in the file will look like "#!/usr/bin/perl", and if it's set to be executable you can run it like any other program.  If you use the "ls" command, executable files are colored green.
[quote=aysiu]I can do Win+R and type firefox and Firefox will launch. I don't have to go C:\Program Files\Mozilla Firefox\Firefox.exe
That's not always true.  There is a branch in the registry with keys that contains the command name (in your example, firefox) and the application that the command firefox will launch (C:\Program Files\Mozilla Firefox\Firefox.exe).  You can change either the key or it's value to get different results :)

---

### Post by NoWhereMan on 2006-03-23
.exe is the suffix for windows executables; in linux (unix-like OSes) there's no suffix, and instead there's what in dos/windows call an attribute (here, a permission).
There we just have read-only, system, archive, hidden.
In unix, while we don't have the hidden attribute (files becoming with a . are hidden), we have much more options and attributes, which can be also applied only to a specific group of users...
btw, one of these permissions is the executable one.
You can apply the executable permission to a file (*whatever* file) by left clicking on it choosing properties and then digging around the options :)
the most quick way is opening a terminal and typing

```
chmod +x myfile
```
Text files can be executable as well as binaries, if they start with the code
```

#!/path/to/interpreter
```

for instance, while in dos/win you have interpreted batch files (*.bat or in 2k/xp also *.cmd), you can make a script executable using the internal shell scripting language writing

```
#!/bin/bash
```

at the very beginning of the file

what's nice in this approach is that you can set the interpreter to whatever interpreter you want, so you can have either
```
#!/bin/python
```
or
```
#!/bin/ruby
```
etc without having to associate any new extension somewhere in a registry or whatever :P

binary files need these permissions as well :)

hope this helps :)
bye

**edit**: I've posted at the same time of Barrakketh :P

---

### Post by MetalMike on 2006-03-23
Ok, it is all very clear now and with Adept things are ultra-easy. :) Thanks for all the help.

---

### Post by az on 2006-03-23
This is free-libre open source software.  The interface for the software development is at the source code level, and not at the executable binary level.  There is no stable ABI.

There is the lack of convenience in terms of installing things willy-nilly, but there are a lot of benefits, in making things simpler for development as well as ensuring a layer of security - packages get uploaded to the repositories in source code form and then compiled by the autobuilders.  This ensures that they are GPL compliant and means that they are easily audited by lots of people. 

I trust the packages from the repositories more than a binary-only package from any 'ol website.

---


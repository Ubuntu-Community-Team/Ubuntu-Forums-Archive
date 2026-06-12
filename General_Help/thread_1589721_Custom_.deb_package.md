---
title: "Custom .deb package"
date: 2010-10-06
forum: General Help
---

### Post by oflannabhra on 2010-10-06
OK, here's the background: headless Ubuntu 10.04.1 64-bit

I found a great utility that is not available in any repositories, so I downloaded the .deb package and installed it with ```
sudo dpkg -i package.deb
```
Everything runs fine on the install. However, when I try to run the command the package was supposed to install, I get a "command not found" error. I'm guessing I need to change some PATH info, except I have no idea how to do that, or where to do it. I also have no idea what directory the package installed to. 

If that's not the problem, I'm guessing it has some dependencies that I don't have installed (I'm pretty sure I have all dependencies installed, however). Would dpkg give me an error in that case?

---

### Post by oldos2er on 2010-10-06
As far as I know, dpkg does not handle dependencies. You should use gdebi (which *does* handle dependencies) instead.

---

### Post by sisco311 on 2010-10-06
Hi and welcome to the forums!

> **oflannabhra said:**
> OK, here's the background: headless Ubuntu 10.04.1 64-bit

I found a great utility that is not available in any repositories, so I downloaded the .deb package and installed it with ```
sudo dpkg -i package.deb
```
Everything runs fine on the install. However, when I try to run the command the package was supposed to install, I get a "command not found" error. I'm guessing I need to change some PATH info, except I have no idea how to do that, or where to do it. I also have no idea what directory the package installed to. 


You can list the files installed by the package:
```
dpkg-query -L package-name
```

> **oflannabhra said:**
> 
If that's not the problem, I'm guessing it has some dependencies that I don't have installed (I'm pretty sure I have all dependencies installed, however). Would dpkg give me an error in that case?


Yep (if you don't use any --force-* option), dpkg throws an error if dependencies are not met. I prefer to use gdebi for installing deb packages. gdebi lets you install local deb packages resolving and installing its dependencies (if they are available from your repos).

---

### Post by oflannabhra on 2010-10-06
Just installed gdebi and installed the package. Did not need any other dependencies installed, and I still get the "command not found" error. Thanks for the info on gdebi though, it looks much better than dpkg.

---

### Post by srs5694 on 2010-10-06
The dpkg program does check for dependencies, and if they're not met, it will refuse to install the package unless you override that with the appropriate command-line option. What dpkg does *not* do is to automatically download and install unmet dependencies. Thus, if the package installed without complaint, unmet dependencies are not the problem.

You can learn what files were installed from a package (say, "package") by typing "dpkg -L package". With any luck that'll help you find the program file in question. They usually go in a directory with "bin" in the name, as in /bin, /sbin, /usr/bin, or /usr/sbin. It could be your package installed the program binary/ies to some obscure or obsolete location. If so, adjusting your PATH variable should do the trick. For instance, if the binaries are in /usr/obscure/bin, you'd type:

```

export PATH=$PATH:/usr/obscure/bin

```

That will only work for your current login session, though. To make it permanent, you'll need to add that line to your ~/.bashrc or some other bash startup script.

---

### Post by oflannabhra on 2010-10-06
> **srs5694 said:**
> The dpkg program does check for dependencies, and if they're not met, it will refuse to install the package unless you override that with the appropriate command-line option. What dpkg does *not* do is to automatically download and install unmet dependencies. Thus, if the package installed without complaint, unmet dependencies are not the problem.

You can learn what files were installed from a package (say, "package") by typing "dpkg -L package". With any luck that'll help you find the program file in question. They usually go in a directory with "bin" in the name, as in /bin, /sbin, /usr/bin, or /usr/sbin. It could be your package installed the program binary/ies to some obscure or obsolete location. If so, adjusting your PATH variable should do the trick. For instance, if the binaries are in /usr/obscure/bin, you'd type:

```

export PATH=$PATH:/usr/obscure/bin

```

That will only work for your current login session, though. To make it permanent, you'll need to add that line to your ~/.bashrc or some other bash startup script.

Yep, it was my path info. thanks specifically for the dpkg -L option which was where I was getting lost. For some reason this package installs to /usr/local/
You folks are awesome!

---


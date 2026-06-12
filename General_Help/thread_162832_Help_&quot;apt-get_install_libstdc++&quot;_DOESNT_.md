---
title: "Help &quot;apt-get install libstdc++&quot; DOESNT WORK."
date: 2006-04-19
forum: General Help
---

### Post by medya on 2006-04-19
as you know to install RealPlayer , we neeed to install that libstdc...
I used to install it by this command :

sudo apt-get install libstdc++

but this time (after months being far from ubuntu) it gives me this error :
```
fred@ubuntu:/media/d/linux/Download/RealPlayer$ sudo apt-get install libstdc++
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package libstdc
```

---

### Post by croak77 on 2006-04-19
You want libstdc++5. There is no 'libstdc++'.

---

### Post by Donnut on 2006-04-19
update your repositories and run update.

---

### Post by Nequeo on 2006-04-19
Try running 'sudo apt-get update' first. Looks like the cached copy of the package list is gone.

---

### Post by medya on 2006-04-20
I tried the "sudo apt-get update"
after hours of downloading, it still gave some errors at the end.
> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


and I still get the same error when I try to install libstdc+ ...

I am supsectious it is because of automatix, automatix, already took shit in my FireFox and broked it for me ...

---

### Post by croak77 on 2006-04-20
you typed 'apt-get install libstdc++5' right?

---

### Post by medya on 2006-04-20
[QUOTE=croak77]you typed 'apt-get install libstdc++5' right?[/QUOTE]
yep

---

### Post by Danny Boy on 2006-04-28
I'm having the same problem, it's wreaking havoc with Automatix. Automatix says everything is installed but it's not because it cannot grab libstdc++5 from the repostitory. Even when I try to manually install something using apt-get install what ever I cannot install it. 

Is there a way to get the libstdc package from somewhere and install it like we were doing with [mstt fonts]("http://ubuntuforums.org/showpost.php?p=960184&postcount=20") for a while there? 

First I did: sudo apt-get update 

Everything went well

Then I did: sudo apt-get install libstdc++5

Here is the output in terminal. 

```
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bmp-docklet: Depends: beep-media-player but it is not going to be installed
  libstdc++5: Depends: gcc-3.3-base (>= 1:3.3.6-8ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---


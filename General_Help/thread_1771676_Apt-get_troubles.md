---
title: "Apt-get troubles"
date: 2011-05-30
forum: General Help
---

### Post by Krenair on 2011-05-30
This is the error I get when removing gnome-session:
> alex@alex:~$ sudo apt-get remove gnome-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 ubuntu-desktop : Depends: gnome-session but it is not going to be installed
                  Recommends: banshee-extension-ubuntuonemusicstore but it is not going to be installed
                  Recommends: gnome-accessibility-themes but it is not going to be installed
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
And this is what happens when I do apt-get -f install:
> alex@alex:~$ sudo apt-get -f install
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  xulrunner-2.0-mozjs
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-session
Suggested packages:
  desktop-base
The following packages will be upgraded:
  gnome-session
1 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
Need to get 0 B/11.8 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 250821 files and directories currently installed.)
Preparing to replace gnome-session 3.0.1-0ubuntu1~build2 (using .../gnome-session_3.0.2-0ubuntu3~natty1_all.deb) ...
Unpacking replacement gnome-session ...
dpkg: error processing /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb (--unpack):
 trying to overwrite '/usr/share/xsessions/gnome-shell.desktop', which is also in package gnome-shell 3.0.1-0ubuntu1~build1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-session_3.0.2-0ubuntu3~natty1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea how I can fix this? I've had it for a few days and nobody in #ubuntu on Freenode has been able to help me. :(

---

### Post by flick on 2011-05-30
Following link may help : especially check out the part about gnome3-session.

[http://joneslee85.wordpress.com/2010/11/01/howto-install-gnome-shell-on-natty-narwhal-11-04/](http://joneslee85.wordpress.com/2010/11/01/howto-install-gnome-shell-on-natty-narwhal-11-04/)

---

### Post by Krenair on 2011-05-30
I want to get rid of Gnome, not install it.

---

### Post by Krenair on 2011-05-30
Oh, and it tells me to use apt-get -f install every time I try to install something with apt-get.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Don't try to install Gnome 3 unless you really know what you are doing or you want to help with development. Stick with Classic Ubuntu or Gnome 2. Here's a good explanation why:

[http://www.techdrivein.com/2011/05/do-not-install-gnome-shell-in-ubuntu.html](http://www.techdrivein.com/2011/05/do-not-install-gnome-shell-in-ubuntu.html)

---

### Post by Krenair on 2011-05-30
I am **not trying to install Gnome 3**.
I have tried the instructions in the link you posted, but this happened:
> alex@alex:~$ sudo apt-get install ppa-purge
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 gnome-session : Depends: gnome-session-common (= 3.0.1-0ubuntu1~build2) but 3.0.2-0ubuntu3~natty1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by linuxinstalledfromhdd on 2011-05-30
What are you trying to do? ::)

---

### Post by Krenair on 2011-05-30
I'm trying to find a way to fix the error which is described by what I've already posted.

---

### Post by linuxinstalledfromhdd on 2011-05-30
What did you install that caused this error?  Backtrack a bit.

---

### Post by Krenair on 2011-05-30
No idea. This is a lot more recent than when I installed Gnome.

---

### Post by linuxinstalledfromhdd on 2011-05-30
You are going to have to wait then, because if you don't know what you "might" have done recently to make changes to your system or configuration, it could be anything.  Let's wait and see if someone else has had this exact same thing happen to them.  That would be the only way I can think of at this point. If you somehow remember, post it.

---


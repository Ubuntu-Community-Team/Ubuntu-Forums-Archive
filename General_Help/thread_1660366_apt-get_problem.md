---
title: "apt-get problem"
date: 2011-01-05
forum: General Help
---

### Post by Jeroen De Dauw on 2011-01-05
I have a Kubuntu 10.10 install on which I can't update my packages due to some fail conflict between pidgin and pidgin-facebookchat. I can't even remove the stuff via apt-get due to this conflict...

sudo apt-get remove pidgin
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 finch : Depends: pidgin-data (>= 1:2.7.9) but 1:2.7.7-1ubuntu0+pidgin1.10.10 is to be installed
 pidgin-libnotify : Depends: pidgin (< 1:3.0) but it is not going to be installed
                    Depends: pidgin (>= 1:2.6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  pidgin-data
The following packages will be upgraded:
  pidgin-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
24 not fully installed or removed.
Need to get 0B/8,589kB of archives.
After this operation, 463kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 236445 files and directories currently installed.)
Preparing to replace pidgin-data 1:2.7.7-1ubuntu0+pidgin1.10.10 (using .../pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb) ...
Unpacking replacement pidgin-data ...
dpkg: error processing /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/pidgin/protocols/16/facebook.png', which is also in package pidgin-facebookchat 1.69
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How can I resolve such a conflict?

---

### Post by Jeroen De Dauw on 2011-01-05
The helpful people at the #Kubuntu channel on freenode helped me out; "sudo dpkg -r pidgin-facebookchat" solved the problem :)

---

### Post by bonfire89 on 2011-01-13
> **Jeroen De Dauw said:**
> The helpful people at the #Kubuntu channel on freenode helped me out; "sudo dpkg -r pidgin-facebookchat" solved the problem :)

thanks, this helped me

---

### Post by Zorael on 2011-01-14
For future reference, in cases like these you may want to use [**aptitude**](apt://aptitude) instead of apt-get. It's a bit slower but much, much better at resolving dependencies. I usually use apt-get to update package lists from repositories, and then aptitude to upgrade, install and remove them.

I'm not sure it's installed by default anymore, so you may have to grab it first.
```
$ sudo apt-get install aptitude

$ sudo apt-get update
$ sudo aptitude full-upgrade
```
When upgrading packages, you can call it to do a safe or a full upgrade. Basically the latter is more aggressive and will offer to remove packages if it needs to, to resolve the dependencies. That's what you needed here with pidgin-facebookchat.

Excerpts from the man page;
```
       **safe-upgrade**
           Upgrades installed packages to their most recent version. Installed
           packages will *not* be removed unless they are unused (see the section
           “Managing Automatically Installed Packages” in the aptitude reference
           manual). Packages which are not currently installed may be installed to
           resolve dependencies unless the --no-new-installs command-line option
           is supplied.

           [B]It is sometimes necessary to remove one package in order to upgrade
           another[/B]; this command is not able to upgrade packages in such
           situations. Use the full-upgrade command to upgrade as many packages as
           possible.

       **full-upgrade**
           Upgrades installed packages to their most recent version, removing or
           installing packages as necessary. This command is less conservative
           than safe-upgrade and thus more likely to perform unwanted actions.
           However, it is capable of upgrading packages that safe-upgrade cannot
           upgrade.
```
So the safe way is to use safe-upgrade when upgrading on a regular basis (if you upgrade via the terminal), and when it becomes obvious that some dependency conflict is holding back packages, use full-upgrade to resolve it.

---


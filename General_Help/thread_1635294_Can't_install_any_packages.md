---
title: "Can't install any packages"
date: 2010-12-01
forum: General Help
---

### Post by talibith on 2010-12-01
Recently I have been having trouble with ubuntu 10.04 LTS and can't install any packages. Every time I try it comes up with this error message:

The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:
python2.4-gobject python2.4-cairo libdesktop-agnostic-vfs-gio libdesktop-agnostic-cfg-gconf libdesktop-agnostic-fdo-glib python2.4-numeric

And i believe that the command installs a package, and you would have to enter the name of the package, which I don't know how to do since I am a linux noob.

I believe there is a problem with python because it says something about python in the details and i try to reinstall python but it gives me the same error. I have one third party repository but I have no idea how to remove it.

Thanks for the help

PS if it helps anything I am running an XPS M170.

---

### Post by oldos2er on 2010-12-01
Can you copy and paste all the output from ```
sudo apt-get install -f
``` here?

---

### Post by ClarNik on 2011-01-05
> **oldos2er said:**
> Can you copy and paste all the output from ```
sudo apt-get install -f
``` here?

So, I'm having the same problem. So, what happens if talibith or I run your code and get all this?


[COLOR="SeaGreen"][COLOR="Cyan"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hplip-cups gtk2-engines-equinox
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  pidgin-data
The following packages will be upgraded:
  pidgin-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/8,589kB of archives.
After this operation, 463kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 318135 files and directories currently installed.)
Preparing to replace pidgin-data 1:2.7.7-1ubuntu0+pidgin1.10.10 (using .../pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb) ...
Unpacking replacement pidgin-data ...
dpkg: error processing /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/pidgin/protocols/16/facebook.png', which is also in package pidgin-facebookchat 1.67.1-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/COLOR]
[COLOR="Black"][/COLOR]

I'm not sure what it means, due to me not being the brains of this computer. I usually run to my boyfriend if I'm having issues with this thing. Thank you in advance and I hope for both our sakes that this gets settled, nothing is updating.

---

### Post by kiddykoff on 2011-01-06
don't worry Clarnik, i'm having a similar problem right now, and i've been using linux for a couple years now.

i'm looking for a solution right now but, next time you paste something from the terminal use the CODE '#' tags.

check out [http://ubuntuforums.org/showthread.php?t=1660030](http://ubuntuforums.org/showthread.php?t=1660030) it looks like you're having the problem as me and a couple others

---

### Post by oldos2er on 2011-01-06
ClarNik, maybe there's something here that can help: [http://code.google.com/p/pidgin-facebookchat/issues/detail?id=905#c20](http://code.google.com/p/pidgin-facebookchat/issues/detail?id=905#c20)

---

### Post by kiddykoff on 2011-01-07
It would be easier to install pidgin from the standard ubuntu repository until the issue is resolved with the pidgin ppa package

---


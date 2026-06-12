---
title: "How do I remove &quot;residual config&quot; through the Terminal?"
date: 2012-02-12
forum: General Help
---

### Post by Sevenleafbranch on 2012-02-12
The Synaptic Package Manager has the option to selection all of the unused packages in "Not Installed (Residual Config)" section.

What I want to know is how do I do this in the Terminal?

I have used the usual commands: apt-get clean/autoclean/autoremove but some unused packages still remain and show up in the Synaptic Package Manager and the Terminal:

$ sudo apt-get clean && sudo apt-get autoremove --purge -y $(dpkg -l | grep '^rc' | awk '{print $2}')
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  *(list of packages)*
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

How can I use the same function that the Synaptic Package Manager has but in the Terminal?

---

### Post by Leppie on 2012-02-15
try the command without the autoremove options:
```
$ sudo apt-get clean && sudo apt-get --purge -y $(dpkg -l | grep '^rc' | awk '{print $2}')
```
autoremove is used to give apt-get control over what is selected for deletion, however you are providing your own list...

---

### Post by imachavel on 2012-02-15
from here what do I do?:

danel@danel-Dimension-4700:~$ sudo apt-get clean && sudo apt-get --purge -y $(dpkg -l | grep '^rc^ | awk '(print $2)')
> 

I have no desire to remove every selected package that exists that isn't installed, as I would have to download it again, and it takes up a very very small amount of memory on the drive. But wouldn't opening synaptic package manager from the GUI, then selecting each package to uninstall do the trick? And I'm guessing the auto remove options would remove just about everything else

---

### Post by Leppie on 2012-02-16
an error seems to have creeped in:
```
$ sudo apt-get clean && sudo apt-get purge -y $(dpkg -l | grep '^rc' | awk '{print $2}')
```


I would normally go for the autoremove thing, but you were saying that you wanted to delete all unused packages.

---

### Post by Gremlinzzz on 2012-02-16
bleachbit is a good cleaning program:popcorn:

---

### Post by Sevenleafbranch on 2012-02-18
None of the commands worked. They all did the same as the command I used. I ended up using aptitude.

Is there any commands to achieve what I am asking?

---

### Post by Syock on 2012-11-25
```
sudo apt-get purge $(dpkg -l | grep '^rc' | awk '{print $2}')
```
seems to work for me. What errors are you facing? Can you try see if
```
dpkg -l | grep '^rc' | awk '{print $2}'
```
gives you the list of packages with residual config?

---

### Post by wujastyk on 2013-04-08
Worked well for me.  Ubuntu 13.04 beta, Gnome 3.6.

I couldn't use synaptic because when I clicked on the select window for "residual config" synaptic always crashed.

Thanks!

> **Syock said:**
> ```
sudo apt-get purge $(dpkg -l | grep '^rc' | awk '{print $2}')
```
seems to work for me. What errors are you facing? Can you try see if
```
dpkg -l | grep '^rc' | awk '{print $2}'
```
gives you the list of packages with residual config?

---

### Post by sgage on 2013-05-01
There seems to be a bit of confusion as to what the different options for apt-get actually do:

The 'autoremove' option is used to remove packages that were installed as dependencies of another package that has since been removed (so long as no other package depends on them). 

If a package has "residual config", it means that the package was indeed uninstalled, but any configuration files were left behind, such that if you reinstall the package, it will be configured as it was. The 'purge' option uninstalls a package AND its configuration files, if any. This does NOT, BTW, include user's configuration data in their own home directory - it applies to system-wide configuration (e.g., stuff in /etc or /usr/share). 

The 'clean' option simply deletes the package deb files from /var/cache/apt - it doesn't uninstall anything, or remove any configuration data. Then you have to re-download the package if you want to reinstall it.

Alas, I do not know of a way to remove residual config from the command line. I use Synaptic. The Janitor in Ubuntu Tweak will also deal with residual configs.

---

### Post by Irihapeti on 2013-05-01
> **sgage said:**
> Alas, I do not know of a way to remove residual config from the command line. I use Synaptic.

The command given in post #7 seems to work. I ran into the problem of synaptic crashing when trying to remove residual configs and was glad to find an alternative.

---

### Post by sgage on 2013-05-01
Yes - I somehow got a wrong impression that it wasn't working for folks. I will certainly add it to my file of tips and tricks!

You'd think there would be a simple apt-get option that would do the trick, but in its absence, that code will get the job done.

---


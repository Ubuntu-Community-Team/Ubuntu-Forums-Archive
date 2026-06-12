---
title: "update manager has critical errors."
date: 2010-01-17
forum: General Help
---

### Post by hockey97 on 2010-01-17
ok, when I in terminal use the command sudo apt-get check 

I get this error:
```
sudo apt-get check
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libdatetimex-easy-perl (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

Update manager :
```

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing libdatetimex-easy-perl (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

```

That is what update exactly spits out. For about 3 months now I couldn't get update manager to work. It had different errors before hand.
Now These are new errors I just got. 

Every time I boot into ubutnu I always get asked to manually run fsck.

Which I do and then starts the computer.

How would I fix this? 

Should I reinstall ubuntu? If so what can I do to backup all files.

backup files like my website and mysql databases and mostly everything.
I need the same graphics driver which is nvidia. cuz I remeber when I was installing it or finding one that work it was hard task to do.

I just don't want to spend alot of time re-configuring my computer.

I just want to never really handle old stuff I done already before.

Since I am trying to finish up making my own website. I have very little time to fool around with the OS or reinstalling alot of programs etc.

I have so far reinstalled ubuntu 6 times. I don't want to have to do another one.

---

### Post by john newbuntu on 2010-01-17
MOVE the offending file out of the way.  i.e.
```
sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages /tmp

```

Then run:
```
sudo apt-get update
```

---


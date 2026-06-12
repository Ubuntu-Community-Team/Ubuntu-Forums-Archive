---
title: "Ubuntu 11.04 update manager woes"
date: 2011-05-21
forum: General Help
---

### Post by louissiuol on 2011-05-21
when i attempt to run the update manager i receive the following error message

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

any help would be much appreciated thanks

---

### Post by sanderd17 on 2011-05-21
Can you try the alternative way to update the packages:

```

sudo apt-get update
sudo apt-get upgrade

```

If this works, then you have a problem with the update GUI itself (and not with the backend). Give us the output of those commands and then we will see what's possible.

---

### Post by louissiuol on 2011-05-21
hey thanks for the help, when i type in update i get this

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages

well i get more than that but this seems to be the interesting bit

---

### Post by sanderd17 on 2011-05-21
was there really a space in the word "binary" if yes, that could be the problem.

Go in the software center to edit-> software sources and look if you can see what source uses that address. You may need to click the "edit" button to see the addresses of the sources. If you see the one with the space, delete that space.

---

### Post by louissiuol on 2011-05-21
thank for the help i re-entered the request and this time there was no space it may have been an error in me copying and pasting it

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages

---

### Post by louissiuol on 2011-05-21
i just viewed my reply and i think its the forum because there is no space when i view it on my computer

---

### Post by sanderd17 on 2011-05-21
Ok, I googled the error, and there is a solution for it (although I wouldn't have found it). You can see the solution here: [http://ubuntuforums.org/showthread.php?t=1750755](http://ubuntuforums.org/showthread.php?t=1750755)

please read the whole post before you start.

---

### Post by louissiuol on 2011-05-21
thank you so much, you've been very helpful i'll have a go at fixing it

---


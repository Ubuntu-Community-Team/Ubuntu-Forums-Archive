---
title: "Updater doesn't work?"
date: 2011-06-20
forum: General Help
---

### Post by lamefox on 2011-06-20
I just installed the latest 32 bit ubuntu on a new netbook and when trying to update I get this message:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'I don't have any idea what this means or how to fix it, but I assume if my updater doesn't work it probably can't fix itself. Is there something I can do about this...? I get online entirely through public wifi so I don't want updates to get behind.

Also, I can't get the software thing to work, where I select programs to install. It seems to look for them but never finish looking and display any...

---

### Post by plucky on 2011-06-21
> **lamefox said:**
> I just installed the latest 32 bit ubuntu on a new netbook and when trying to update I get this message:

I don't have any idea what this means or how to fix it, but I assume if my updater doesn't work it probably can't fix itself. Is there something I can do about this...? I get online entirely through public wifi so I don't want updates to get behind.

Also, I can't get the software thing to work, where I select programs to install. It seems to look for them but never finish looking and display any...

Welcome to the forum.

You can open a terminal **(Applications > Accessories > Terminal)** and use these commands ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command will ask for your password,but will not echo anything as you type it in.
It will delete the files in /var/lib/apt/lists and then reload them from your download server with the second command.

Good Luck

---

### Post by lamefox on 2011-06-21
It had some kind of error at first where it didn't complete but I tried it again a few hours later and it seems to have worked. Thanks!

---


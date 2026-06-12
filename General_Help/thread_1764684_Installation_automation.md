---
title: "Installation automation"
date: 2011-05-22
forum: General Help
---

### Post by Denis.Gorbachev on 2011-05-22
Hello everybody!


When I install Ubuntu on another computer:
[LIST]
[*]I need to install all the packages that I use.
[*]I need to make some config changes.
[*]I need to "svn checkout" some projects.
[*]I need to "git clone" some projects.
[*]I need to setup .ssh/config
[*]I need to download a custom Eclipse build.
[*]I need to download some additional Eclipse plugins.
[*]... many other tweaks ...
[/LIST]
So, I want to run a script, like "sudo install-everything-needed", that would execute these predefined actions.

Is there any package that provides the backbone for such system?

---

### Post by dragonfly41 on 2011-05-22
You don't just want to clone .. clonezilla?

If you require to go through a customised configuration I found these to be useful ..

APTonCD
AutoKey to build scripts
Nautilus Scripts Manager
GNOME Commander
bash script(s) to support the above ..


[COLOR=Blue][EDIT]

Here is an earlier thread I started on similar topic ..

[http://ubuntuforums.org/showthread.php?t=1745622](http://ubuntuforums.org/showthread.php?t=1745622)

If passwords are required  by different FTP servers for downloads I've found that it is easy to setup a string of FTP connections in GNOME Commander ..

look for list of created connections in     /home/user/.gnome-commander/connections

similarly if using Grsync

look in /home/user/.grsync/grsync.ini .. 

then use AutoKey .. or bash script .. to automate running through a batch of connections and tweaks.


So backup these configuration files to be used to reinstall packages, plugins etc.[/COLOR]

---

### Post by Denis.Gorbachev on 2011-05-23
I don't want to customize a CD. Rather, I want to apply modifications to an existing system. Say, when I create a new project and install all the new packages needed for it, I want this project and packages to appear on all my machines.

---

### Post by dragonfly41 on 2011-05-23
That wasn't too clear from your post ..
[I][COLOR=Blue]
"When I install Ubuntu on another computer:"[/COLOR][/I]


If you have already installed ubuntu on several systems .. *[COLOR=Blue]"on all my machines[/COLOR]*[COLOR=Blue]"[/COLOR] .. surely you just need to run through an upgrade script .. or scripts .. to sync these slaves with your master copy??


First look at the link above .. see tip from oldfred ..
```

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

```

Also it would be easier if you installed in separate "/" and "/home" partitions.

---


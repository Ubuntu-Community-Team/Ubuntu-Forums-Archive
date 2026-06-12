---
title: "Simple Backup Suite - Not installing properly"
date: 2010-12-14
forum: General Help
---

### Post by kevin_j_morse on 2010-12-14
Hi there,

I just went to install sbackup using

```
sudo apt-get install sbackup
```

everything appeared to work fine but the Simple Backup Suite menu item was not added to System / Administration and upon running sbackup using Alt - F2 I get the following error:

> An error occurred

Critical Error: No configuration file for the default profile was found!

Now continue processing remaining profiles.

I've tried reinstalling using Synaptic Package Manager but no luck. The program won't run and all I can see is the indicator icon which, when I click on it, says:

> Simple Backup
-------------------------
Profile: unknown
Size of backup: unknown
Progress: canceled
Remaining time: finished
-------------------------
Cancel Backup

Any help would be greatly appreciated.

---

### Post by lncoll on 2010-12-14
Just try:

```

$ sudo dpkg-reconfigure sbackup
$ sudo simple-backup-config
```

To start backups:
```
$ sudo sbackupd
```

---

### Post by kevin_j_morse on 2010-12-14
Thanks that did it! Still no menu item in Administration but maybe they removed that. Also this Simple Backup Suite is much different from the one in the tutorial on ubuntu.com...

---

### Post by disabled_20220313 on 2011-07-10
Hi,

I have just had the same problem. It seems to be a bug in the Sbackup configuration of the menu shortcuts.

To solve the problem you need to edit the respective .desktop files in /usr/share/applications/ .

```


gksudo gedit /usr/share/applications/sbackup-restore-su.desktop


```

This will open gedit with root privileges. 

Edit the following line from:
```

Categories=GTK;GNOME;System;

```

to

```

Categories=GTK;GNOME;System;Settings;

```

Once this is done the option to open the Sbackup Restore with root permissions should be visible in System --> Administrator.

Do the same for the configuration application component using the following command.

```

gksudo gedit /usr/share/applications/sbackup-config-su.desktop

```

The line to edit is exactly the same as above.

I have also reported this as a bug ([Bug 808260]("https://bugs.launchpad.net/sbackup/+bug/808260")) as it's a trivial problem that is really bloody annoying.

---


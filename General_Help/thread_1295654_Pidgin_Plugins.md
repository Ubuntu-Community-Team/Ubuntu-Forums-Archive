---
title: "Pidgin Plugins"
date: 2009-10-19
forum: General Help
---

### Post by yo2boy on 2009-10-19
Hi! I'm trying to install the new pidgin plugins for pidgin 2.6.* but it won't let me.

```
yo2boy@ubuntu:~$ sudo apt-get install pidgin-plugin-pack
[sudo] password for yo2boy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntustudio-default-settings
The following packages will be upgraded:
  pidgin-plugin-pack
1 upgraded, 0 newly installed, 1 to remove and 436 not upgraded.
1 not fully installed or removed.
Need to get 304kB of archives.
After this operation, 279kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/universe pidgin-plugin-pack 2.6.0-0ubuntu1 [304kB]
Fetched 304kB in 2s (151kB/s)              
(Reading database ... 137956 files and directories currently installed.)
Removing ubuntustudio-default-settings ...
dpkg: error processing ubuntustudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)
yo2boy@ubuntu:~$ ubuntustudio-default-settings - -remove
ubuntustudio-default-settings: command not found
yo2boy@ubuntu:~$ 
```

I have Ubuntu 9.10 karmic koala [beta] and I don't think the beta has to do anything with this since I had this problem with 9.04 jaunty before.
And, I did 'sudo apt-get install ubuntustudio-desktop' but now that I removed it, this is always showing up. HEEELPPPPP!!!!!!!

---

### Post by tom.swartz07 on 2009-10-19
alrighty- first lets do some housekeeping.

run the following commands
```
sudo apt-get update && sudo apt-get upgrade

THEN RUN

sudo apt-get autoremove
```

According to your list, you have over 436 packages to be upgraded. Since youre using the Beta, I would highly advise that you keep up on these so that your system doesnt become unstable while youre installing other packages. (theres nothing worse than having a kernel panic in the middle of installing a game!)

It might take a little while, so be patient. The 'update' command assures you have the most recent list of upgrades, and naturally the 'upgrade' command assures you apply the upgrades. 'Autoremove' on the other hand, might be just the ticket to get rid of the ubuntustudio package youre having trouble with.

After all of that is finished
After that, THEN you could run
```
sudo apt-get install pidgin-plugin-pack
```
And if you still have the error from ubuntustudio,
```
sudo apt-get remove --purge ubuntustudio-default-settings
```

Hope this Helps!!

---

### Post by yo2boy on 2009-10-19
Still didn't work. Took a while to download the upgrades, but the installation failed. Autoremove failed and 
sudo apt-get remove --purge ubuntustudio-default-settings failed

---

### Post by tom.swartz07 on 2009-10-19
Ok- what seems to be the problem now?

you had mentioned it didnt work. What part failed?

EDIT: didnt see your post.

try running the installation of the upgrades through the system upgrades manager
on the panel, system/admin/upgrades

click 'check' then 'install'

---

### Post by yo2boy on 2009-10-19
Well, before I do that, I would just like to post this, it was directly after I was done downloading the upgrades:
```

4~unofficial-0ubuntu4 [99.1kB]
Fetched 286MB in 14min 28s (329kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 137956 files and directories currently installed.)
Removing ubuntustudio-default-settings ...
dpkg: error processing ubuntustudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
yo2boy@ubuntu:~$ sudo apt-get autoremove
[sudo] password for yo2boy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntustudio-default-settings
0 upgraded, 0 newly installed, 1 to remove and 523 not upgraded.
1 not fully installed or removed.
After this operation, 73.7kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137956 files and directories currently installed.)
Removing ubuntustudio-default-settings ...
dpkg: error processing ubuntustudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)
yo2boy@ubuntu:~$ sudo apt-get remove --purge ubuntustudio-default-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntustudio-default-settings
0 upgraded, 0 newly installed, 1 to remove and 523 not upgraded.
1 not fully installed or removed.
After this operation, 73.7kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137956 files and directories currently installed.)
Removing ubuntustudio-default-settings ...
dpkg: error processing ubuntustudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

EDIT: -- [http://imgur.com/OfrGq.png](http://imgur.com/OfrGq.png)    -- [http://imgur.com/6HNDz.png](http://imgur.com/6HNDz.png)

That happened, and when I clicked, close, upd. manager closed.

---

### Post by tom.swartz07 on 2009-10-21
Hi, sorry for the long wait. I didnt see your new post.

> **yo2boy said:**
> ```

dpkg: error processing ubuntustudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-default-settings
**E: Sub-process /usr/bin/dpkg returned an error code (1)**

```



It seems that your problem arises from the dkpg program. Thats what causes all of your problems that you described. 

Like I said, When you open the manager, and you see the message like in [http://i.imgur.com/OfrGq.png](http://i.imgur.com/OfrGq.png) , Click Partial Upgrade.

The partial upgrade means that you will 'partially' upgrade the files, because there are updates available that could only be installed after previous versions are upgraded. (Upgrades to upgrades are available, if you will)

Run the updater, and once everything is upgraded, then you should be fine.



I dont mean to sound offensive, but it is not recommended for novices to install beta versions of the OS like this because of the stability problems, (like the ones you are experiencing with dpkg, for instance). Once the final version comes out next week, your problems should be minimal, but for future reference, the Beta releases are recommended for advanced users.


Run the partial upgrade, make sure that you install all of the upgrades. (verify it by running the sudo apt-get autoremove command to see what the count is.

AFTER all of the upgrades are installed, THEN you could use the upgraded (and fixed) dpkg program to remove the problem packages.


Let us know how it works!

---

### Post by superdav42 on 2009-10-21
did you try the command ```
sudo apt-get install -f
``` like it said to ?

---


---
title: "strange errors"
date: 2010-05-17
forum: General Help
---

### Post by Kubischbuntu on 2010-05-17
Hi,

I originally installed Ubuntu Jaunty - and then decided to try the KDE   desktop so installed that. I have not used gnome since and actually ran   the update to Lucid in KDE. 
I have now noticed that every time I do a sudo kate anything I get some strange error messages:

kubisch@squarebear:~$ sudo kate /etc/fstab
Error: "/var/tmp/kdecache-kubisch" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-kubisch" is owned by uid 1000 instead of uid 0.
kate(7084)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(7084)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/kubisch/.local/share/mime/magic"
Error: "/tmp/ksocket-kubisch" is owned by uid 1000 instead of uid 0.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/kubisch/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

Does anybody know what this means and what I should do about it?

Thanx

---

### Post by Zorael on 2010-05-17
You should never use sudo with kate or any other graphical applications! It *will* mess up file and directory permissions.

That's what **kdesudo** and **gksu** are for. See [this page](http://www.psychocats.net/ubuntu/graphicalsudo) for a brief explanation.

```
$ sudo chown -R root:root /var/tmp/kdecache-kubisch /tmp/kde-kudisch /tmp/ksocket-kudisch
```

Then run '**kdebugdialog**', check Disable all debug output, and hit OK.

---

### Post by Kubischbuntu on 2010-05-18
Hi,

thanx for that - I will keep the KDEsudo in mind for the future. I did the chown command you suggested (after correcting the spelling of the name ;)) but when I the did kdebugdialog I got:

kubisch@squarebear:~$ sudo chown -R root:root /var/tmp/kdecache-kubisch /tmp/kde-kubisch /tmp/ksocket-kubisch
[sudo] password for kubisch: 
kubisch@squarebear:~$ kdebugdialog
Error: "/var/tmp/kdecache-kubisch" is owned by uid 0 instead of uid 1000.
Error: "/var/tmp/kdecache-kubisch" is owned by uid 0 instead of uid 1000.
Error: "/tmp/kde-kubisch" is owned by uid 0 instead of uid 1000.
Error: "/tmp/kde-kubisch" is owned by uid 0 instead of uid 1000.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/kubisch/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

which to me seems to suggest the chown comman did not succeed??

Obviously once I disabled the debug output it did not get displayed anymore but the problem is still there - no?

---

### Post by Zorael on 2010-05-18
Very curious! Now that I look at my own machine those directories aren't owned by root, but rather my own user (as your initial error message claimed them to be). I'm not sure why it complained to begin with. So let's first undo the damage I wrought. >.<
```
$ sudo chown -R $(id -u):$(id -g) /var/tmp/kdecache-kubisch /tmp/kde-kubisch /tmp/ksocket-kubisch
```

The ibus bits are harmless.
```
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/kubisch/.config/ibus/bus
Bus:pen: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon 
```
As of lucid, Kubuntu compiles its KDE programs to use the ibus input method engine (IME) per default, and unless you're running its daemon it will complain like this. You don't need any special IMEs unless you plan to input in non-western languages, like Japanese. You can probably satisfy the first two error messages by creating the **~/.config/ibus/bus** directory that it seeks.
```
$ mkdir -p ~/.config/ibus/bus
```

---


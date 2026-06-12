---
title: "krunner and 'show system activity' won't start"
date: 2011-01-20
forum: General Help
---

### Post by craq on 2011-01-20
Neither of these programs will start by using their shortcuts (alt-F2 and ctrl-esc). Ctrl-alt-esc still works to knock out individual windows. Starting krunner from the terminal doesn't work either, and I have been getting a few different errors:

If it is not running, I get this one (although the last line changes)
```
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory                                                    
QFileSystemWatcher: failed to add paths: /home/rapsonc/.config/ibus/bus  
Bus::open: Can not get ibus-daemon's address.                            
IBusInputContext::createInputContext: no connection to ibus-daemon       
krunner(6023)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found 
```

If it is already running (but not visible or usable, I can only see it in htop) then there is no error message.

It sounds similar to this problem:
[http://ubuntuforums.org/showthread.php?t=1509675](http://ubuntuforums.org/showthread.php?t=1509675)
but I didn't want to hijack that thread and I don't think it has anything to do with plugins.

Ok... cancel all that. Just as I was about to hit send I tried one more time and it worked. I didn't actually change anything though, I guess this forum is just magic... I'd still be interested in an explanation, if anyone's got one?

---


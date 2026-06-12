---
title: "Cannot Uninstall An Application"
date: 2010-01-05
forum: General Help
---

### Post by Avidanis on 2010-01-05
I tried to uninstall bird and bird6 , keep getting errors , any suggestions ?

---

### Post by michy99 on 2010-01-05
If you post the errors, you are more likely to get help.

---

### Post by Avidanis on 2010-01-05
> **michy99 said:**
> If you post the errors, you are more likely to get help.

[code]
ronvista2@ubuntu:~$ sudo apt-get remove bird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bird
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 553kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137557 files and directories currently installed.)
Removing bird ...
Terminated
invoke-rc.d: initscript bird, action "stop" failed.
dpkg: error processing bird (--remove):
 subprocess installed pre-removal script returned error exit status 143
/etc/init.d/bird: 134: Syntax error: ";" unexpected
invoke-rc.d: initscript bird, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bird
E: Sub-process /usr/bin/dpkg returned an error code (1)
[\code]

---

### Post by Twitch6000 on 2010-01-05
Try uninstalling it through synaptic. 

Or if you do not mind terminal use use sudo apt-get remove bird -f

---

### Post by Avidanis on 2010-01-05
> **Twitch6000 said:**
> Try uninstalling it through synaptic. 

Or if you do not mind terminal use use sudo apt-get remove bird -f


I have tried it using both the console and synaptic.

---

### Post by Twitch6000 on 2010-01-05
> **Avidanis said:**
> I have tried it using both the console and synaptic.

try this - sudo dpkg --force-all -r bird

---

### Post by Avidanis on 2010-01-05
> **Twitch6000 said:**
> try this - sudo dpkg --force-all -r bird

still a no-go

---

### Post by Twitch6000 on 2010-01-05
Humm okay it seems it is still running. Try this killall bird and then try the above command.

---

### Post by michy99 on 2010-01-05
Try```
sudo apt-get install --reinstall bird
```and then try to remove it.

---

### Post by Avidanis on 2010-01-05
> **Twitch6000 said:**
> Humm okay it seems it is still running. Try this killall bird and then try the above command.

When I installed it , I got an error also. So I believe its partially installed somehow, if that is possible.  Here is the output I got from your suggestions above. 

and p.s. ,thanks for the help.



```
ronvista2@ubuntu:~$ sudo apt-get remove bird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bird
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 553kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137557 files and directories currently installed.)
Removing bird ...
Terminated
invoke-rc.d: initscript bird, action "stop" failed.
dpkg: error processing bird (--remove):
 subprocess installed pre-removal script returned error exit status 143
/etc/init.d/bird: 134: Syntax error: ";" unexpected
invoke-rc.d: initscript bird, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bird
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Avidanis on 2010-01-05
OK, this badboy is running . I went to the website and came across some information. 

I guess there are some configuration settings that need to be setup. Otherwise I see a command where I can shut down bird and then I will probably be able to  remove it.

```
ronvista2@ubuntu:~$ sudo birdc
BIRD 1.0.15 ready.
bird> ?
configure ["<file>"]                           Reload configuration
debug ...                                      Control protocol debugging
disable <protocol> | "<pattern>" | all         Disable protocol
down                                           Shut the daemon down
dump ...                                       Dump debugging information
echo [all | off | <mask>] [<buffer-size>]      Configure echoing of log messages
enable <protocol> | "<pattern>" | all          Enable protocol
exit                                           Exit the client
help                                           Description of the help system
quit                                           Quit the client
restart <protocol> | "<pattern>" | all         Restart protocol
show ...                                       Show status information
bird> show
No such command. Press `?' for help.
bird> show status
BIRD 1.0.15
Current server time is 05-01-2010 16:56:03
Last reboot on 05-01-2010 16:40:13
Last reconfiguration on 05-01-2010 16:40:13
Daemon is up and running
bird> 
ronvista2@ubuntu:~$
```

---

### Post by Shihan74 on 2010-01-23
I had the "joy" of falling into the same trap with bird...

what i did, and this is a complete hack.. edited /etc/init.d/bird and at the top of the file i put (well, just after the comments, about 6 lines):

return 0

same with /etc/init.d/bird6

thankfully, that allows it to uninstall. Make sure you do a "complete" removal otherwise those files stay around.

Its (sadly) not the first time i've been stuck in a lock like that either, and a simple "remove and ignore the pre-removal script" in dpkg would actually be handy.

---


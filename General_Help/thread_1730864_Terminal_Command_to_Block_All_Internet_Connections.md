---
title: "Terminal Command to Block All Internet Connections?"
date: 2011-04-16
forum: General Help
---

### Post by Dysruption on 2011-04-16
I'm not quite sure where to post it, so I put it here.

I am trying to write a shell script that will block any outgoing Internet connection, focusing mainly on the HTTP connections. 

It would be nice if this command could work on both Mac OSX and Linux. Any help is greatly appreciated! Thank you!

---

### Post by Foxheadz on 2011-04-16
Im fairly certain that running ```
sudo ifconfig "wireless interface" down
``` will stop all incoming and outgoing traffic for that specific card. And to find what wireless interface you need just run iwconfig

---

### Post by WorMzy on 2011-04-16
```
sudo /etc/init.d/network stop
```

May or may not work as a general command, depending on how your network is setup.

---

### Post by Dysruption on 2011-04-16
> **WorMzy said:**
> ```
sudo /etc/init.d/network stop
```May or may not work as a general command, depending on how your network is setup.

How would I reverse this? By replacing "stop" with "start"?

---

### Post by WorMzy on 2011-04-16
Yep. I take it this is your first experience with daemons? Most have a stop, a start, and a restart (stop+start combined, used to make configuration changes take effect) function.

---

### Post by Dysruption on 2011-04-16
> **WorMzy said:**
> Yep. I take it this is your first experience with daemons? Most have a stop, a start, and a restart (stop+start combined, used to make configuration changes take effect) function.

Yes, I am fairly new with Shell commands and am trying to write a script that can disable internet connections, and then another that can enable them again. 

I'm a bit unsure on what "daemons" is, however.

Nonetheless, thank you for the help.

---

### Post by WorMzy on 2011-04-16
A daemon is an application that runs in the background. If you're coming from a Windows environment, it may help to think of them as "services". They're things that take care of a lot of the background running of the system and don't require much input from you as a user.

---

### Post by Dysruption on 2011-04-16
> **WorMzy said:**
> A daemon is an application that runs in the background. If you're coming from a Windows environment, it may help to think of them as "services". They're things that take care of a lot of the background running of the system and don't require much input from you as a user.

Ah I see. I actually come from a mostly Mac environment.

Another question: I have appended lines to a file with a script and am wondering if there is a command that can reverse that process by removing those lines from that file?

Thank you again!

---

### Post by WorMzy on 2011-04-16
The easiest way to remove lines from a file is to manually edit it with a text editor. You can do it via command line if you really want to, but unless you need to automate the removal of these lines (like you're going to remove them on a regular basis), there's not not much point in doing it via command line.

Still, if you want to give it a try, look into the sed (stream editor) application.

```
sed -i '/this text to remove/d' /path/to/file.txt
```

Should remove _any_ line that has that "this text to remove" in it.

---


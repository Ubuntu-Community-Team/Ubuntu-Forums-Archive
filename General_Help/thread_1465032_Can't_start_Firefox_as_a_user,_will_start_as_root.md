---
title: "Can't start Firefox as a user, will start as root"
date: 2010-04-29
forum: General Help
---

### Post by krodrigue on 2010-04-29
I'm running Ubuntu Server 9.10, when I log in to a user account I can not run Firefox unless I start it as root through the terminal.

Any ideas on how to fix this.

---

### Post by Lekensteyn on 2010-04-29
How did you install Firefox from?
Did you get any errors?

It's most likely to be a permissions-related issue.

---

### Post by krodrigue on 2010-04-29
> **Lekensteyn said:**
> How did you install Firefox from?
Did you get any errors?
 
It's most likely to be a permissions-related issue.
 
I installed it through apt-get with out errors, this problem came about after I rebooted the box and kept getting all kind of permissions problems logged in as a user. I was able to fix them but now have this firefox problem.

---

### Post by dino99 on 2010-04-29
run gconf-editor and tweak firefox rights as you need

---

### Post by lovinglinux on 2010-04-29
If you started Firefox using *sudo* instead of *gksudo*, then you need to fix some permission issues. See [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2). After that, start it as normal user from a terminal and post the errors you get from the terminal output.

Also see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by krodrigue on 2010-04-29
> **dino99 said:**
> run gconf-editor and tweak firefox rights as you need

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
 
That is the g-conf error.

---

### Post by krodrigue on 2010-04-29
Ok, after folling thoes directions and also running sudo chown -R usr:usr /home/usr, and

 cmod -R 755 home/usr

Firefox is now working...now to figure out how to copy all of my links that I have saved.

Thanks for the help.

---

### Post by Lekensteyn on 2010-04-29
I don't think it was a wise idea to chmod the whole home and usr directory.
You should have chowned /home/yourusername/.mozilla:
```
sudo chown -R yourusername:yourusername /home/yourusername/.mozilla
```
And chmodded /usr/firefox:
```
sudo chmod -R 755 /usr/lib/firefox*
```

By chmodding the whole /home and /usr directory, you might create a security hole.

---


---
title: "Nautilus won't start without 'sudo'?"
date: 2011-05-21
forum: General Help
---

### Post by Atamisk on 2011-05-21
Hello all

Running natty (latest upgrade), and i'm having nautilus issues. 

If i type 
```
nautilus
```into the terminal, i get nothing. no errors, no text, and no window. 

If i type 
```
sudo nautilus
```it works great. here's a dump of the output from nautilus starting (under sudo)
```
** (nautilus:13087): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '13087'

(nautilus:13087): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

### Post by emoguitarist06 on 2011-05-21
I have the same problem EXCEPT nautilus does start for me without sudo but it's extremely slow and freezes a lot or sometimes doesn't start

---

### Post by sahabcse on 2011-05-21
nautilus is a root privilege command. So it will work only using sudo command.

Please follow below url for running a command without using sudo. 

[http://ubuntulinux.co.in/blog/ubuntu/how-to-run-a-command-without-using-sudo-password-in-ubuntu/](http://ubuntulinux.co.in/blog/ubuntu/how-to-run-a-command-without-using-sudo-password-in-ubuntu/)

Change the Cmnd_Alias accordingly.

---

### Post by emoguitarist06 on 2011-05-21
> **sahabcse said:**
> nautilus is a root privilege command. So it will work only using sudo command.

Please follow below url for running a command without using sudo. 

[http://ubuntulinux.co.in/blog/ubuntu/how-to-run-a-command-without-using-sudo-password-in-ubuntu/](http://ubuntulinux.co.in/blog/ubuntu/how-to-run-a-command-without-using-sudo-password-in-ubuntu/)

Change the Cmnd_Alias accordingly.

That makes absolutely no sense and sorry you're wrong. Nautilus is not just a root privilege application. It's Ubuntu's default file manager. When you use Nautilus WITHOUT root permission you can only modify files and fodlers under your HOME folder or ~/Home but if you run Nautilus WITH root permission you can then modify all files and folders including /tmp, /media, /etc... and so on

---

### Post by drs305 on 2011-05-21
Atamisk,

Something may be corrupted in your .nautilus folder. Try renaming ~/.nautilus (/home/<username>/.nautilus

A new .nautilus will be created the next time it's opened as a normal user. Note mine is currently empty, but it's still recreated.

If you can't rename it or perform any other options on .nautilus, that might be the problem. The folder or one of it's contents may be owned by root or some other user. As root, you will be able to remove ~/.nautilus if this is the case.

---

### Post by Atamisk on 2011-05-21
Renaming the .nautilus folder worked! Thanks!

-Aaron

---

### Post by mc4man on 2011-05-21
You may want to get in the habit when browsing nautilus as root, (if you do), of using
gksudo nautilus instead of sudo nautilus
(not saying it was a factor here, just good practice

---

### Post by WorMzy on 2011-05-21
Just expanding on what mc4man said here, but running graphical applications with "sudo" can lead to all sorts of problems.

[Read this]("http://www.psychocats.net/ubuntu/graphicalsudo") for more information.

---


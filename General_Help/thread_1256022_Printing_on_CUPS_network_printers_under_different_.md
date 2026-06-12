---
title: "Printing on CUPS network printers under different login?"
date: 2009-09-02
forum: General Help
---

### Post by sdaau on 2009-09-02
Hi all, 

I use Ubuntu 9.04, where I log in typically under my own username "homeuser"/"homepass" ... At work, we have a Linux backend, where printers are shared on the network via CUPS. At work, I have different credentials I would have to log in as, say "workuser"/"workpass". 

If I want to access the printers, I can for instance enter the CUPS server address in 'system-config-printer' (System/Administration/Printing) and I do get the list of printers. But if I try to open any of them, and hit OK without changing any settings, I get asked for a password - Ubuntu suggests first my "homeuser" login: 

[IMG]http://img338.imageshack.us/img338/3056/cups.png[/IMG] 

I delete that "homeuser", and enter my real credentials for the work network, "workuser"/"workpass" and I still can't get anywhere, because I get "Not Authorized": 

[IMG]http://img2.imageshack.us/img2/364/cupsna.png[/IMG] 

In this case, if I try to print a test page - or print say from Document Viewer, nothing gets added to the printer queue, and no error messages are generated. In other words, attempting to print like this fails silently. 

Since I do not have access to cups error and access logs, I can't really tell what is wrong, but I was suspecting the current logged in user. 

So I simply added a user on my Ubuntu on my PC, which has the exact same "workuser"/"workpass" as username/password combination. And lo and behold, no problems with printing whatsoever. 

So apparently, in the previous case, in spite of me deleting "homeuser" and entering the workuser/workpass combo - my Ubuntu apparently *still* authenticates me to the CUPS network as "homeuser" instead of "workuser" !! 

So, of course I find it extremely irritating that I should log out and log in to a different user just to have a page printed, and therefore I'd like to ask the community - is there any way to authenticate myself as "workuser" to the CUPS network printers, *while* I am logged in as "homeuser" in Ubuntu? 

I tried this while logged as "homeuser": 

```
 $ gksu -u workuser system-config-printer 

libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.

/usr/share/system-config-printer/system-config-printer.py:125: GtkWarning: gdk_cursor_new_for_display: assertion `GDK_IS_DISPLAY (display)' failed
  busy_cursor = gtk.gdk.Cursor(gtk.gdk.WATCH)
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 125, in <module>
    busy_cursor = gtk.gdk.Cursor(gtk.gdk.WATCH)
RuntimeError: could not create GdkCursor object

```So trying to run system-config-printer under a different user (than the currently logged in one) apparently tries to start X windows again - and as it is already started, it fails?? 

Any ideas would be greatly appreciated :) 

Cheers !

PS: Here is a couple of diagrams showing the problem:

Situation A: logged as homeuser, printing doesn't work:
[IMG]http://img140.imageshack.us/img140/9839/cupsnet.png[/IMG]

Situation B: logged in as work user, printing does work:
[IMG]http://img3.imageshack.us/img3/5434/cupsnet2.png[/IMG]

---

### Post by pkong on 2009-09-02
Hi,
I had a simillar  problem when changing to ubuntu 9.04
The solution was to rename the cups.conf.o in place of the new  ones created.
Hope it helps

---

### Post by sdaau on 2009-09-02
Hi pkong, 

Thanks for your reply !!!

I have on my system, under /etc/cups/, files cupsd.conf (and cupsd.conf.default and cupsd.conf.O). As far as I understand, cupsd.conf.O is just the "original" file used to restore a cupsd.conf ([http://www.nslu2-linux.org/wiki/HowTo/AddPrinter](http://www.nslu2-linux.org/wiki/HowTo/AddPrinter))...

However, I also think that cupsd.conf on my machine will influence the cups server on my machine - and what I probably need, would be to change the cupsd.conf on the work server - which I don't have access to. 

But in the end - the thing is that all works, if I am logged in as "workuser" on my machine as well - so I guess the question is, how do I force the system to authenticate me as "workuser" to the system, even if I am currently logged in as "homeuser".

This for instance works in command line:
```

homeuser@mypc$ su - workuser
Password: 
workuser@mypc:~$ lpstat -a                                  # list printers
workuser@mypc:~$ lpr -P myprinter1 toprint.ps    # print toprint.ps on printer myprinter1
workuser@mypc:~$ lpstat -u login all                     # check queued print jobs, see if all is OK
workuser@mypc:~$ exit                                         # go back to homeuser login

```

I just want something similar but working through the GUI - that is, calling system-config-printers as 'workuser' and having the printers show up in the system as 'workuser'

Thanks again, 
Cheers!

---

### Post by pkong on 2009-09-02
Hi ,
The only thing i can think of is to add a user to te cups server.
you should log in at localhost:630 on the server as workuser and add homeuser to the list of users.
best regards

---

### Post by sdaau on 2009-09-03
Hi pkong,

Thanks again for your response !! :) 

> **pkong said:**
> 
The only thing i can think of is to add a user to te cups server.
you should log in at localhost:630 on the server as workuser and add homeuser to the list of users.


Unfortunately, I do not have a permission to log manipulate users on the work servers... 

Since system-config-printer does actually ask for authentication, the best thing would be somehow to persuade it to actually use those credentials entered for all communication with cups server - and not send the "current logged user"'s credential.. 

In any case thanks for the response, 
Cheers !

---


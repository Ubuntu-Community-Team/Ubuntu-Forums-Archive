---
title: "Programs Crashing On Save"
date: 2009-11-09
forum: General Help
---

### Post by haruki on 2009-11-09
Hello. For some reason many programs (ex: Gimp, Gedit, OOffice) are crashing when I try to save the file I'm working on in them, programs which I have been using regularly with no problems for a long time. I have tried a number of searches looking for a clue but fear my grasp of the problem is to general at the moment to yield any helpful results. What can I do to narrow the problem? I am wondering if there are, most likely, some commands I can run, some logs I can view, that might help me get info to share that would explain the problem.

My only guess is that maybe it has something to do with a hard drive crash I had, though it seemed like everything was fine after running fsck (I was asked to by an Ubuntu script in recovery mode after booting). Other accounts on this computer, which use the same hard drive work fine (they aren't crashing on saving). This leads me to think maybe it has something to do with my home directory.

Thanks for reading and for any help, in advance.

---

### Post by Giblet5 on 2009-11-09
Open a terminal window and run (copy/paste) the following Really Long Command. It will set reasonable permissions on your home directory.

```
sudo find $HOME/ -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME/ -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; chmod 700 $HOME/.ssh ; chmod 600 $HOME/.ssh/* ; echo "It's all mine now! Bwah ha ha!"
```

Now try saving something.

Better? Then memorize that command so you can help others. ;)

---

### Post by haruki on 2009-11-10
Giblet5, thank you for your help. I ran the series of commands but I still cannot save anything, the programs still crash. Maybe there is something I am doing wrong?

---

### Post by haruki on 2009-11-12
I hope it is not bad to be replying to my own message. I am still experiencing crashes when trying to save files. What kinds of information do I need to give so that I can make it easier to solve this problem? Thank you in advance.

---

### Post by bashphoenux on 2009-11-12
run the program from terminal and post the error report that it shows in the terminal!

---

### Post by haruki on 2009-11-12
> **bashphoenux said:**
> run the program from terminal and post the error report that it shows in the terminal!

Thank you bashphoenux, that is a great idea! Okay, I just tried this with gedit and gimp, running them from command line then trying to save something from within the program... this is what happened:

~$ gedit
Segmentation fault

~$ gimp

(script-fu:18411): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault


Does this help?

---

### Post by JBAlaska on 2009-11-12
This seems to be a current known GTK+ bug. Try deleting:
```
 /home/username/.local/share/mime/mime.cache
```
And see if this fixes your segfault.

If that does not work, another reported workaround is to run the offending programs as root.

---

### Post by haruki on 2009-11-12
> **JBAlaska said:**
> This seems to be a current known GTK+ bug. Try deleting:
```
 /home/username/.local/share/mime/mime.cache
```
And see if this fixes your segfault.

If that does not work, another reported workaround is to run the offending programs as root.

JBAlaska, thank you for your help. I deleted the mime.cache file and that didn't fix it. However, running gimp as root worked. But, is there something else I can try? It seems unsafe or something to run OOffice and everything else as root.

---

### Post by septekin on 2009-11-12
Haruki, you said that other users, including root, work fine. Have you tried creating a new account for yourself, maybe with a just slightly different user name? If this works, you can copy your data from the faulty account and then delete the offender.

---

### Post by JBAlaska on 2009-11-12
As far as I can Google, This is "Possibly" a permissions bug with GTK+ that effects all flavors of *nix using both KDE and Gnome.

One user suggested trying another GTK theme, check this:

[quote="Gentoo bug report"]The bug is reproducible with very basic GTK application. Stacktrace is the same for all applications (see above). Actual problem is at ll 2420 icon = g_content_type_get_icon (content_type);icon is not valid pointer but not null

Also debug version of GTK  print a message before crash:Gtk-CRITICAL **: gtk_window_set_default_icon: assertion `GDK_IS_PIXBUF (icon)'failed[/quote]

Full bug report [here](https://bugs.gentoo.org/show_bug.cgi?id=287709) with no fix as of 11/11/09

Wish I could be of more help, but I can not replicate the segfault on my boxes.

---

### Post by Hugo_Rune on 2009-11-12
> **JBAlaska said:**
> This seems to be a current known GTK+ bug. Try deleting:
```
 /home/username/.local/share/mime/mime.cache
```And see if this fixes your segfault.

If that does not work, another reported workaround is to run the offending programs as root.

Thank you JBAlaska - I've been searching for a solution to this problem for about three weeks now (I got a crash every time a file dialog appeared using any GTK app - e.g. thunderbird, firefox, gimp etc).

So - thank you very much indeed! My system is all back up and working again. Great to find a solution on the Ubuntu forums when I'm using KDE 4.3 on OpenSuse 11.1 :)

---


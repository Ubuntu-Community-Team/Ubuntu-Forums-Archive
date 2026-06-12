---
title: "Can't run &quot;sudo nautilus&quot;"
date: 2010-01-05
forum: General Help
---

### Post by ana.g on 2010-01-05
Hi, I've got a problem with my laptop (with ubuntu 9.10) and maybe you can help me.  Everytime I try to run sudo nautilus /gksudo nautilus I've got the following error: 

(nautilus:2370): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed     

&quot;** (nautilus:2370): WARNING **: No marshaller for signature of signal 'UploadFinished'     

** (nautilus:2370): WARNING **: No marshaller for signature of signal 'DownloadFinished'     

** (nautilus:2370): WARNING **: No marshaller for signature of signal 'ShareCreateError'  Initializing nautilus-gdu extension    

**  Eel:ERROR:eel-preferences.c:117preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)&quot;;

 I have not been able to fix this problem. I tried running Nautilus using the root account but Nautilus didn't even start. I tried reinstalling Nautilus (Synaptic) but it didin't work. I don't know what else I can do.  I hope you can help me. Thank you

---

### Post by ana.g on 2010-01-12
Can anyone help me, please?.  Thanks.

---

### Post by pi/roman on 2010-01-12
I  think the better way to do it is supposed to be:
gksudo nautilus

That might not work either but if it does it should process your commands better.

---

### Post by audiomick on 2010-01-12
Hi.
Don't know what the errors mean, sorry.

You shouldn't try to run nautilus with sudo, only with gksu / gksudo.

See here for the reasons why.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by wojox on 2010-01-12
What does:

```
gconftool-2 --get /apps/nautilus/desktop/trash_icon_visible
```

report?

---

### Post by chrisinspace on 2010-01-12
> **pi/roman said:**
> I  think the better way to do it is supposed to be:
gksudo nautilus

That might not work either but if it does it should process your commands better.

Works for me.  I use this method all the time.  If you use Alt+F2, you don't have to worry about launching the terminal.

---

### Post by junapp on 2010-01-12
> **ana.g said:**
>  Everytime I try to run sudo nautilus /gksudo nautilus
> **pi/roman said:**
> I  think the better way to do it is supposed to be:
gksudo nautilus

op has tried with gksudo.

@ana.g have you recently installed anything that might cause this? Did you used to be able to run nautilus in this manner and it suddenly stopped working, or is this the first time you've tried it?

---

### Post by Cheesemill on 2010-01-12
Just an FYI, you should **never** run GUI apps with sudo. Always use gksudo instead.

---

### Post by pi/roman on 2010-01-12
Another thread, same error.  Post #4 gives some suggestions.

[http://ubuntuforums.org/showthread.php?p=8428769](http://ubuntuforums.org/showthread.php?p=8428769)

---

### Post by ana.g on 2010-01-13
Hi, thank you for your answers,  pi/roman I tried gksudo nautilus because as Cheesemill and audiomick say is much more advisable, but it did not work.  Chrisinspace: I also tried running ALT + F2 gksudo nautilus but it did not work either.  Wojox, this is the report:   ana@ana-laptop:~$ sudo gconftool-2 --get /apps/nautilus/desktop/trash_icon_visible  true  Thwe report is exactly the same even if I do not use "sudo" (gconftool-2 --get /apps/nautilus/desktop/trash_icon_visible).  Junapp: I reintalled karmic Koala one month ago, and I had some troubles restoring the trash icon (gconf-editor), but I finally managed  to do it. i have not been able to run sudo/gksudo nautilus since I reinstalled Karmic.   I tried deleting trash-icon-name key as suggested in another formum (gconf-editor apps/nautilus/desktop), and creating a new key; but it did not work).  Finally pi/roman, as suggested in the post you linked, I completely uninstalled Nautilus and reinstalled it but the problem is still there.  Thank you again for your asnwers, I hope you can help me.

---

### Post by 3rdalbum on 2010-01-13
Removing Nautilus and reinstalling it is not going to solve anything. The copy of Nautilus on disk is perfectly fine. The problem is elsewhere.

Try removing/renaming the ".gconf" directory inside /root:

```
sudo mv /root/.gconf /root/.gconf-jan10
```

That's what the error message seems to be complaing about anyway. The other messages that start with the word "warning" are most likely unrelated.

---

### Post by pi/roman on 2010-01-13
I would agree that it should probably be the last error to focus on because I have gotten the 3 WARNING errors and also the first Eel-CRITICAL error but have not had the problem of nautilus not starting.

---

### Post by seeker5528 on 2010-01-13
> **Cheesemill said:**
> Just an FYI, you should **never** run GUI apps with sudo. Always use gksudo instead.

What possible reasoning could there be for that bit of advice.

And no this link didn't really provide a reason.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Not remembering about firefox extensions? Seems like a no brainer that you shouldn't install Firefox extensions while running Firefox with elevated permissions.

Don't know what that weird crap about running sudo'ed KDE stuff over SSH was about, sounds like errant use of the stuff to me.

That claim that Kate won't work seems questionable as well, 'sudo kate' works and always worked for me. 

And there is a ton of docs/howtos the tell you to do 'sudo this', 'sudo that', etc.... so if it was really a problem, it seems like there would be more than a couple of references to obscure oddities to show as an example of why not to do it.

If you are typing the command in at the command line, you may as well type your user name and password in at the command line as well.

If you are creating a menu item for something, then there is a reason to use gksu or kdesu instead.

In the case of nautilus I would suggest to do:

```
sudo nautilus --browser --no-desktop
```

Later, Seeker

---

### Post by seeker5528 on 2010-01-13
If you have already tried:

> try deleting all your configuration files with
```
cd /home/yourusername
```
then
```

sudo rm -rf .gnome2 .gconf .gconfd .metacity 
```

or even if you have not, you might try:

```
sudo rm -rf /root/.gnome* /root/.gconf*
```

Since it sounds like Nautilus is fine when you are not running it under sudo?

Later, Seeker

---

### Post by ana.g on 2010-01-14
Hi, thank you very much for your answers.  As seeker said, I didn't have this problem when I ran nautilus without sudo.

 I finally managed to fix it (I followed 3rd Album command and it worked perfectly).

 Now, as Pi/Roman said I get this error:  

(nautilus:2987): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed  ** (nautilus:2987): 
WARNING **: No marshaller for signature of signal 'UploadFinished'   ** (nautilus:2987): 
WARNING **: No marshaller for signature of signal 'DownloadFinished'  ** (nautilus:2987): 
WARNING **: No marshaller for signature of signal 'ShareCreateError' 
Initializing nautilus-gdu extension

 Despite this error message nautilus starts properly. By the way, before I reinstalled Karmic (and I had this problem)  I used to get an error message -I can't remember whether it was exactly the same than I get now or not- everytime I ran sudo nautillus, nevertheless  nautillus used  to start without any problems.  

Thank you again for your answers, help and time. ;)

See/read you soon.

---

### Post by seeker5528 on 2010-01-16
> **seeker5528 said:**
> What possible reasoning could there be for that bit of advice.

And no this link didn't really provide a reason.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I see the issue with sudo versus gksudo/kdesudo now. Seems like it would have been much simpler just to say that sudo doesn't set reset $HOME to the home directory of the target user by default so it may write files back to your home directory that are owned by root. 

Later, Seeker

---


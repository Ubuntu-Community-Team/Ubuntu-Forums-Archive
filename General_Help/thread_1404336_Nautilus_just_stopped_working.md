---
title: "Nautilus just stopped working"
date: 2010-02-11
forum: General Help
---

### Post by vizitorq on 2010-02-11
I have no idea what happened. I'm running Ubuntu 9.10 on AMD Athlon 64bit system. It was in the middle of me using the computer. I wasn't doing anything out of the ordinary, and all of a sudden, I can't open nautilus.

When I try to run it in the shell it says this:
```
kumi@throne ~/Desktop nautilus

(nautilus:4201): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:4201): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:4201): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
(yes, it writes the second message twice)
I have NO idea what this means. Also, I cannot seem to open anything on my Desktop. mv, and cp commands still work in the shell, but the Desktop does not reflect these changes.

when i run this:
```

kumi@throne ~/Desktop gksudo nautilus
(nautilus:5439): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.1

** (nautilus:5439): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5439): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5439): WARNING **: No marshaller for signature of signal 'ShareCreateError'

```

Nautilus opens, but can barely navigate properly... I've restarted my computer and the same problem persists.

Please HELP!!

---

### Post by Dragonbite on 2010-02-11
The first thing that comes to mind reading your output (the second one specifically) is that you have Dropbox installed?

Perhaps try uninstalling Dropbox and see if things work after that.  

If so, then at least you've narrowed it down to Dropbox and mabye there is another version available, or it just doesn't like co-existing with UbuntuOne.

If not, then we need to dig deeper.

---

### Post by vizitorq on 2010-02-11
Thanks for the quick reply. I removed dropbox:
```
sudo apt-get remove nautilus-dropbox
```

but I still have the same problem. I rebooted and the same problem
```
kumi@throne ~ nautilus

(nautilus:3228): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:3228): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:3228): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

should I remove nautilus and install it again??

---

### Post by kanikilu on 2010-02-11
There are some similar-sounding bug reports, such as:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234)

Check the last few comments. They suggest removing some configuration files...

To see if that might help you, first try creating a new user on the machine (System > Administration > Users and Groups) and login with that account and try Nautilus again. If it works, it's probably something in the config files as mentioned in that bug report.

---

### Post by vizitorq on 2010-02-11
I created a new user and when I logged in with that user, Nautilus works just fine. However, I'm not so familiar with ubuntu and was not able to understand the last few comments in the bug report you linked me to (thanks by the way!)

I did, however, recognise that it must be the same problem. But in the comments in the bug report, there isn't enough detail for me to fix the problem myself. I could not find the nautilus configuration files that were mentioned as they are not in the same place in my computer.
Once I got into the .gconf directory I noticed a TON of config files, all with the same name, just in different sub-directories. I believe i've found the right one here:
```
/home/kumi/.gconf/apps/nautilus/preferences/%gconf.xml
```

I might just try renaming it to %gconf.xml.bak and logout and log back in to see if that fixes anything although at first glance, it doesn't look like there is anything in this file that has anything to do with the problem.

Am I in the right place??

---

### Post by vizitorq on 2010-02-11
After renaming the file I mentioned above, I logged out, then logged back in.

This time, after logging in, I'm able to click the items on my desktop, and the files will open (images). But as soon as I try to start nautilus again, let's say, by opening my Home folder using the "Places" tab in the top menu-bar, I'm no longer able to double-click any of the items on my desktop (as if they're a part of the wallpaper) and Nautilus STILL doesn't work.

Except this time, it doesn't wait to timeout. In under 2 seconds this is what I get:
```
kumi@throne ~ nautilus

(nautilus:14286): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
kumi@throne ~ 

```

However, the items on my desktop seem to remain frozen, regardless if Nautilus is still trying to run (which it isn't, unlike last time)

This is definitely beyond me. I really don't know what to do here, and as you might imagine... this is a serious issue. PLEASE help!

---

### Post by kanikilu on 2010-02-11
To be honest, I'm not entirely sure which files they mean either, so it's not just you ;)

I do see on my computer a **~/.nautilus** directory, perhaps try renaming that one?

---

### Post by lidex on 2010-02-11
> **vizitorq said:**
> I created a new user and when I logged in with that user, Nautilus works just fine. However, I'm not so familiar with ubuntu and was not able to understand the last few comments in the bug report you linked me to (thanks by the way!)

I did, however, recognise that it must be the same problem. But in the comments in the bug report, there isn't enough detail for me to fix the problem myself. I could not find the nautilus configuration files that were mentioned as they are not in the same place in my computer.
Once I got into the .gconf directory I noticed a TON of config files, all with the same name, just in different sub-directories. I believe i've found the right one here:
```
/home/kumi/.gconf/apps/nautilus/preferences/%gconf.xml
```

I might just try renaming it to %gconf.xml.bak and logout and log back in to see if that fixes anything although at first glance, it doesn't look like there is anything in this file that has anything to do with the problem.

Am I in the right place??

I think so.

---


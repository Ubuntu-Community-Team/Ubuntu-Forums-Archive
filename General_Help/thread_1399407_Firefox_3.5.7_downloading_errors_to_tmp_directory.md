---
title: "Firefox 3.5.7 downloading errors to /tmp directory??"
date: 2010-02-05
forum: General Help
---

### Post by tedrogers on 2010-02-05
Hi,

I'm downloading a file in Firefox 3.5.7 to be opened with a helper application, and I get this error:

```
/tmp/**INSERT FILE NAME HERE** could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location.
```

It seems to me that my permissions on /tmp are borked. Don't know why? This has just started happening since I installed the 2.6.31-19 kernel update (from 2.6.31-17).

I've tried all the usual stuff of restarting, changing default save in Firefox, resetting download sections in config:about for Firefox, uninstalling and reinstalling Firefox.

Any ideas anyone?

Thanks.

---

### Post by MattressVon on 2010-02-05
Try opening a run dialog with ALT + F2 and entering "gksudo nautilus" (without the quotes. You can then navigate to the /tmp directory and right click on it and click properties to adjust the permissions. It should be under file system in the left hand column. Mine are root for user with create and delete files as my options. See if that helps to start.

---

### Post by gmargo on 2010-02-05
Start a terminal and run "ls -ld /tmp".  You should see something like this:
```

drwxrwxrwt 13 root root 4096 Feb  5 17:00 /tmp
```If you don't see "drwxrwxrwxt" then do "chmod 1777 /tmp" (as root of course).

---

### Post by tedrogers on 2010-02-06
I get this:

```
drwxrwxrwt 17 root root 4096 2010-02-06 09:11 /tmp
```

...so I assume it's all okay.

Nautilus permissions seem okay too. Mine are also root for user with create and delete files as the options.

---

### Post by gmargo on 2010-02-06
Your permissions on /tmp look fine.  I'm at a loss.  The only other things I can think of are 

[LIST]
[*]there's already another file there of the same name but a different user.  Unlikely and I assume you tried more than one.
[*]try creating a file manually, ```
cd /tmp ; touch foo ; ls -l foo
``` to see if there are some weird permissions associated with your user id, like something from a security enhancement (selinix, apparmor?)
[/LIST]

---

### Post by tedrogers on 2010-02-06
My result from your code is:

```
-rw-r--r-- 1 ted ted 0 2010-02-06 19:19 foo
```

It looks like I have read / write permissions, and everyone else just has read.

You know I'm getting several other weird things on this laptop...random kernel crashes when using transmission and deluge, this /tmp issue with firefox, strange battery issues for hibernation etc (I have several unresolved threads at the moment!).

So in short, I'm backing up my /home directory now and I'm going to do a complete wipe and fresh install.

Using...

```
dpkg --get-selections > installed-software
```

...and...

```
dpkg --set-selections < installed-software
```

...I should be able to reinstall everything I need quickly once the fresh install is done.

Fingers crossed.

---

### Post by tedrogers on 2010-02-07
Reinstall worked. Weird.

Guess I'll never know what caused it now.

---


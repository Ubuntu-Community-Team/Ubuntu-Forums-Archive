---
title: "Nautilus ONLY works as root"
date: 2009-11-03
forum: General Help
---

### Post by legatek on 2009-11-03
Been running 9.10 for a couple of days now. Last night I reboot the computer for the 3rd time and came back without a desktop. Well, the desktop was there bot no icons. Typing nautilus in a terminal gives this:

```
monkey@monkey-laptop:~$ nautilus

(nautilus:4673): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:4673): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4673): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4673): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault (core dumped)
```

Opening Nautilus as root gives this:

```
monkey@monkey-laptop:~$ gksudo nautilus
[sudo] password for monkey: 

(nautilus:4690): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```

And I get Nautilus, albeit in root, which is not what I'm after.

---

### Post by dialynas on 2009-11-03
i have the same problem

---

### Post by Peter09 on 2009-11-03
There is a bug report here

> [http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=HOt&q=%28nautilus%3A4673%29%3A+Eel-CRITICAL+**%3A&btnG=Search&meta=&aq=f&oq=](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=HOt&q=%28nautilus%3A4673%29%3A+Eel-CRITICAL+**%3A&btnG=Search&meta=&aq=f&oq=)
which could be related.

I suggest as a start to get to recovery mode and use the menu to reset your video setup.

---

### Post by legatek on 2009-11-04
Still no solution.

I tried dpkg --configure nautilus, which told me nautilus is installed and configured.

I tried sudo apt-get purge nautilus, and reinstalled nautilus, and the problem persists.

The output of dmesg:

```
monkey@monkey-laptop:~$ dmesg |grep nautilus
[   71.896072] nautilus[1826]: segfault at b6dadfec ip 0101e760 sp b6dadff0 error 6 in libgvfsdbus.so[1002000+24000]
```

which suggests a problem with the gvfs libraries, so I reinstalled them from the package manager. No joy.

Again, I can gksudo nautilus without a problem, but then I can only access my desktop from the file browser, and I have a root application open all the time which I don't like. Anything else to try? I'm about ready to downgrade to Intrepid, which was the last distribution that played nice for me.

---

### Post by Peter09 on 2009-11-04
I wonder if you have a user configuration problem? Two thoughts - check the groups that your user belongs to and if that does not help try creating a new user and see if that user has the same problem.

---

### Post by P4man on 2009-11-04
Your error message mentions a > nautilus-gdu extension.
I dont have that it seems. Is that something you added? I dont see it in the repo's either. Perhaps try removing it?

---

### Post by Peter09 on 2009-11-04
A third option:-

first save your configuration file

```
mv .gnome2 gnome2_saved
```
then logout and log in again.

This will cause gnome to create a new gnome configuration - you will lose any set-up that you have, but not any data or anything like that.

See if you still have the problem.

---

### Post by legatek on 2009-11-04
OK, some progress. Removing .gnome2 had no effect, but creating a new user worked for that user. Nautilus works fine there, but not in my current user. Now I only have to figure out why THIS user cannot use Nautilus. Since I earlier purged Nautilus, none of the configuration files in /home should be the cause, nor should anything in .gnome2 since moving it and starting my current user with a new .gnome2 didn't fix the problem. Any ideas where I can start looking? Alternatively I can start migrating config files over to the new user until Nautilus breaks.

As for nautilus-gdu, I have no idea why that's there. A google search links it to Fedora.

---

### Post by Peter09 on 2009-11-04
Have you checked that your working user has the same group membership as your non-working user?

Also check permissions on the home directories.

Mmmmm ...... trying to think what else may be involved.

---

### Post by legatek on 2009-11-05
All permissions are the same. I'll try mucking about until it's fixed or I give up and install Intrepid.

---

### Post by Peter09 on 2009-11-05
might be worth removing the .nautilus file just to make sure.

---

### Post by Karmatica on 2009-11-11
I also am having the same problems. I was running 9.04 and after upgrading nautilus stopped working. I tried new users, uninstalling and reinstalling nautilus. So I just did a complete reinstall and nautilus worked, well sort of I can get to places no problem and it will work through terminal as well but still get the error message:

Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

Then I allowed update manager to update and then after nautilus no longer worked. So I am back to step one and reinstalled Ubuntu 9.10 and am going to update each of the 86 items, and see which update messes things up I believe it might be one of the following, Adobe Flash, Brasero, rythmbox or possibly one of the codecs. I will keep you posted and see what happens.

---

### Post by Peter09 on 2009-11-11
Have you tried deleting the .nautilus directory in your home folder.

---

### Post by Karmatica on 2009-11-11
to be honest no I haven't and don't really have the skills or knowledge on how to do that through terminal...if you could be so kind as to give that to me I could try that

---

### Post by Peter09 on 2009-11-11
The terminal command is

```
rm -r .nautilus
```

---

### Post by tecnoprint on 2009-11-11
Hola yo tambien tengo el mismo problema y Trate de usar los concejos que dejaron en este foro pero aun asi no me ayudó.

---

### Post by Karmatica on 2009-11-12
Same result for me. On the upside I found out what seems to be causing the issue for me, mind you fixing it on the other hand?
After getting the nautilus has no conflicts message and then purging nautilus and using dolphin instead...nothing worked so I had to do a new fresh reinstall .
The culprit it seems is the burned CD I have with MP3's on it because nautilus works when the CD is not in the drive but it won't work when it is in the drive any idea on how to fix that? is it possible to install 2 file managers at the same time and also was wondering if deleting the .nautilus file will actually make a difference?

---

### Post by legatek on 2009-11-12
None of the suggestions worked for me. I ended up reinstalling an earlier version of Ubuntu.

---

### Post by Karmatica on 2009-11-12
well so i have found that the only worka round was to use dolphin(another file manager) which worked on copying over 2 cd's and after a restart now dolphin won't even see the files on the drive??? the drive did sound kinda funny mind you how does one confirm if the drive is dead?

---

### Post by Hawy.php on 2009-12-23
i was facing same problem and i tried all solutions here and didn't solved till i tried this 
```
mv  ~/.local/share/gvfs-metadata ~/.local/share/gvfs-metadata.old
```
and logout then login and hello New Nautilus :)

i get the solution from here
[http://ubuntuforums.org/showpost.php?p=8546582&postcount=20](http://ubuntuforums.org/showpost.php?p=8546582&postcount=20)

---


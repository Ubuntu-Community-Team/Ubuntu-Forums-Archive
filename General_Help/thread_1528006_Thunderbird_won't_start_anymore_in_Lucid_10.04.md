---
title: "Thunderbird won't start anymore in Lucid 10.04"
date: 2010-07-10
forum: General Help
---

### Post by Aquila99 on 2010-07-10
Thunderbird won't start in Lucid 10.04
It used to work, but stopped working (an update perhaps)
Running from the menu just gives a tiny window, which when expanded is blank
Running thunderbird from the from the command line crashes as follows:

```

peter@trinity:~$ /usr/lib/thunderbird-3.0.5/thunderbird-bin
/usr/lib/thunderbird-3.0.5/thunderbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

```

Looking for the missing library:
```

peter@trinity:~$ ls /lib/libmozjs.so
ls: cannot access /lib/libmozjs.so: No such file or directory

```

Not sure what to do next ... help

---

### Post by DeMus on 2010-07-10
> **Aquila99 said:**
> Thunderbird won't start in Lucid 10.04
It used to work, but stopped working (an update perhaps)
Running from the menu just gives a tiny window, which when expanded is blank
Running thunderbird from the from the command line crashes as follows:

```

peter@trinity:~$ /usr/lib/thunderbird-3.0.5/thunderbird-bin
/usr/lib/thunderbird-3.0.5/thunderbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

```

Looking for the missing library:
```

peter@trinity:~$ ls /lib/libmozjs.so
ls: cannot access /lib/libmozjs.so: No such file or directory

```

Not sure what to do next ... help

Not sure what happened but you could try to re-install Thunderbird so it will put the library back in its place. I use the 3.0.6 and also had an update this week. But here it is still working.
Try re-installing. Your settings and accounts will stay, don't worry.

---

### Post by Aquila99 on 2010-07-10
Hi DeMus
Thanks for the advice.  I tried this (using Synaptic Manage Gui)
Still get the same error.
Cheers

---

### Post by ExpU on 2010-07-10
Take a look at this:

[http://guide.ubuntuforums.org/showpost.php?p=9563448&postcount=14](http://guide.ubuntuforums.org/showpost.php?p=9563448&postcount=14)

Worked fine for me

---

### Post by DeMus on 2010-07-10
> **Aquila99 said:**
> Thunderbird won't start in Lucid 10.04
It used to work, but stopped working (an update perhaps)
Running from the menu just gives a tiny window, which when expanded is blank
Running thunderbird from the from the command line crashes as follows:

```

peter@trinity:~$ /usr/lib/thunderbird-3.0.5/thunderbird-bin
/usr/lib/thunderbird-3.0.5/thunderbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

```

Looking for the missing library:
```

peter@trinity:~$ ls /lib/libmozjs.so
ls: cannot access /lib/libmozjs.so: No such file or directory

```

Not sure what to do next ... help

You wrote you looked for the lib in /lib. I looked in my system and the "missing" lib libmozjs.so is in /usr/lib/thunderbird-3.0.6.
Have a look in your Thunderbird folder to see if it is there or not. Even when it is there it obviously is not loaded since the program doesn't work.
As mentioned in one of the other posts you could also try to install another version, like the 3.0.6 which is available in Synaptic.

---

### Post by Aquila99 on 2010-07-10
I decided to uninstall, and go back to the previous version of Thunderbird (which I am sure was working)- 3.05.
Same error!
So rebooted (again), just to be sure, and it worked
So then updated to the latest version of Thunderbird, and all seems good. :D

Honestly, not sure what was going on, and will probably never know.
But all seems good now
Thanks for the advice.

---

### Post by DeMus on 2010-07-10
> **Aquila99 said:**
> I decided to uninstall, and go back to the previous version of Thunderbird (which I am sure was working)- 3.05.
Same error!
So rebooted (again), just to be sure, and it worked
So then updated to the latest version of Thunderbird, and all seems good. :D

Honestly, not sure what was going on, and will probably never know.
But all seems good now
Thanks for the advice.

Don't know if I helped, but you're welcome.

---

### Post by hroitblat on 2010-08-29
I had the same problem after upgrading to 3.06 on Ubuntu 10.04.  Rebooting fixed it (without having to go back a version).
I reinstalled Thunderbird with no effect, but then rebooted, and everything was then OK.

---


---
title: "g_set_prgname() called multiple times"
date: 2009-12-23
forum: General Help
---

### Post by vttay03 on 2009-12-23
...anyone  else seen this terminal output when starting Thunderbird and Firefox?  Seems to have happened after some updates yesterday (I think it's related to some of the glib updates).  Anyone have a fix?

---

### Post by chiahung on 2009-12-24
Yes. It's due to the unstable version (2.22.3-0ubuntu1) of libglib2.0-0.
You can use Synaptic Package Manager to downgrade libglib2.0-0 and libglib2.0-data to the previous version (2.22.2-0ubuntu1).
Mark the package you want to downgrade, and choose "Force version ..." from "Package" on the main menu. Select the previous version and it is done.

---

### Post by igorek93 on 2009-12-25
how can i do this in commad line? (i'm running ubuntu server 9.10 )

---

### Post by tafsen on 2009-12-26
> **chiahung said:**
> Yes. It's due to the unstable version (2.22.3-0ubuntu1) of libglib2.0-0.
You can use Synaptic Package Manager to downgrade libglib2.0-0 and libglib2.0-data to the previous version (2.22.2-0ubuntu1).
Mark the package you want to downgrade, and choose "Force version ..." from "Package" on the main menu. Select the previous version and it is done.
Cheers! This fixed my problem :popcorn:

---

### Post by vttay03 on 2009-12-26
sweet, thanks for the info...i'm on travel for christmas but i'll definitely give this a shot when i return home.  it was really starting to bug me since i start firefox and thunderbird from a shell.

---

### Post by Umeaboy on 2009-12-28
How soon will this be fixed?
Until the release of Ubuntu 10.4?
Just wondering.

---

### Post by Cue2 on 2009-12-28
I actually get three warnings. I dont know if they're related.

```
process:2996): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(firefox:2996): GLib-WARNING **: g_set_prgname() called multiple times

Gdk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

```

edit:

OK, I tried to downgrade libglib2.0.0 and it downgraded successfully. however now I couldn't start firefox at all. not even from the gnome desktop. it would say "starting firefox" at the bottom,disappear, then nothing would happen. typing firefox in a terminal did nothing, not even any error messages.

at this point I upgraded libglib again and reinstalled all my firefox packages from synaptic package manager. now everything works fine with the latest libglib2.0.0. 
I can launch firefox from a terminal without any GTK, GDK warnings. still get the glib warning but firefox works fine anyway both from the shell and gnome menu.

---

### Post by vttay03 on 2009-12-29
> 
Yes. It's due to the unstable version (2.22.3-0ubuntu1) of libglib2.0-0.
You can use Synaptic Package Manager to downgrade libglib2.0-0 and libglib2.0-data to the previous version (2.22.2-0ubuntu1).
Mark the package you want to downgrade, and choose "Force version ..." from "Package" on the main menu. Select the previous version and it is done.


Thanks, just got around to trying this and it seems to have fixed my problem.  No more ugly messages on terminal output...

---

### Post by geoffm on 2010-02-28
I tried downgrading libglib2.0-0, at first I thought it solved the problem, but firefox just loads once after I ram in safe-mode.

I tried editing compatibility.ini.

I removed:
```
LastPlatformDir=/usr/lib/firefox**-3.6**
LastAppDir=/usr/lib/firefox**-3.6**
```

to leave:

```
LastPlatformDir=/usr/lib/firefox
LastAppDir=/usr/lib/firefox
```

Now I get 3 lines of the same error message in the console, but FF loads.
And make compatibility.ini read-only so it doesn't switch back.

---

### Post by alphaamanitin on 2010-04-22
I have the same problem.  Are they just waiting until 10 comes out to fix it?  Annoying, but Firefox does run for me.

AlphaA

---

### Post by nkbatsi on 2010-06-19
THANK YOU GUYS!!!
I think this topic has solved a problem torturing me for a looong time!

Thank you, thank you, thank you...

---


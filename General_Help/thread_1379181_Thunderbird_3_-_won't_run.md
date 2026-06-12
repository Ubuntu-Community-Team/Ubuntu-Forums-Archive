---
title: "Thunderbird 3 - won't run"
date: 2010-01-12
forum: General Help
---

### Post by kneewax on 2010-01-12
Hey folks,

Having issues with TB3 at the moment:

When i run the application I get a window that says:

"Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system."

However - TB is not running and several reboots later i still get the message.

When I run from the CLI I get these errors:


/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

anyone know what is going on here or how to fix it?

Cheers

Ali

---

### Post by warfacegod on 2010-01-12
Try using System Monitor to End or Kill the Thunderbird process.

---

### Post by kneewax on 2010-01-12
ah yes, unfortunatly it's not there! TB ain't running.....

---

### Post by warfacegod on 2010-01-12
Try: System> Admin.> Synaptic> Edit> Fix Broken Packages

---

### Post by wojox on 2010-01-12
It looks like your 32-bit program is trying to load 64-bit libraries, which doesn't work. You'll need the 32-bit versions of those libraries.

Have a look at [getlibs]("http://ubuntuforums.org/showthread.php?t=474790"), that should be able to automatically find and install the 32-bit libraries that your specific program needs.

---

### Post by kneewax on 2010-01-13
Hi Folks,

I am running the x64 version of Ubuntu so the libs shouldn't be a surprise. Having said that TB doesn't use x64 libs at all as far as I'm aware so that is perplexing.

I have today tried a complete removal and re-install of both TB2 (I tried this first) then then TB3 using Ubuntuzilla.

However I still get the same error message and TB still isn't running as a process!

I am going to attempt to remove/reinstall once more but I shall backup and remove the TB file structure from $home before the install and see if there is some odd setting there that is causing TB to fail.

Ali

---

### Post by kneewax on 2010-01-13
And that failed to work!

On the plus side I no longer get the error shown in the first messsage in this thread.  Now if I run TB I get the spinning cursor for about 30 seconds as if it is trying to load, then....nothing happens!

running from CLI makes no difference, I get no outputted error message to the CLI, it just seeems to think it is working!  canoot start in safe mode, or any other error reporting mode. Also cannot load the profile manager either!

Any ideas folks?

---

### Post by ELMIT on 2010-08-16
I just came to this point. What can we do?
Upgraded, ... and now no email!!!

(wrong ELF class: ELFCLASS64)

bye

Ronald

---


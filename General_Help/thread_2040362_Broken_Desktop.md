---
title: "Broken Desktop"
date: 2012-08-10
forum: General Help
---

### Post by PaulInBHC on 2012-08-10
I have 12.04 and unity 3D. I was running a game that froze and I tried alt + F4 to kill it. That didn't work so I started pressing crtl + alt + something and ended up in tty terminal. I got out of that and no longer have anything but my background and a couple of shortcuts. No top panel and no launcher. Super key does nothing.
I tried unity -- reset and get errors and it just sits there. I tried sudo unity --reset and get further but it stops at terminal_command_key and doesn't seem to finish.

What next?

---

### Post by ubudog on 2012-08-10
Hi, try this command:
```
unity --reset-icons
```

---

### Post by PaulInBHC on 2012-08-11
Thanks, did not work

Tried it, log out, log in, still the same.

Tried as sudo, ends at cannot load plugin ezoom, log out, restart, still the same.

---

### Post by PaulInBHC on 2012-08-11
Bump

Am I just not being patient enough for the terminal to finish doing something?

Or do I need to reinstall the OS?

---

### Post by Frogs Hair on 2012-08-11
Try to reset from TTY.

Unity 3D gone Missing:

Login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next enter user name, password, and run the following command.

Code:
unity --reset

Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu.

---

### Post by PaulInBHC on 2012-08-11
Thanks

It runs until

Set update "run_key"

Then it just sits there. I walked away for 10 minutes, still sitting with a flashing cursor. HDD activity light flashes every 3 seconds.

---

### Post by Frogs Hair on 2012-08-11
Restart again if you haven't already and try one more time. There are some other command line options at the link. [http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

---

### Post by PaulInBHC on 2012-08-11
Thanks again

I tried again from tty with reset, then again with reset-icons and still no luck.

---

### Post by PaulInBHC on 2012-08-11
I tried removing compiz, no luck.

Ran unity --reset again, it doesn't seem to ever finish. I waited over 20 minutes.

---

### Post by PaulInBHC on 2012-08-11
No more answers?

I had 11.10 on one partition and 12.04 on another. After 12.04 had been out for a while, I decided to do the upgrade on the 11.10. That is what I am having a problem with. Using XP at the moment.

I downloaded 12.04 and burned a CD. I guess I'll work on partitions and reinstall tomorrow.

---

### Post by cg40k on 2012-08-12
Had this same problem Paul and just had to re-install. One thing of note, is that you can run in the GNOME desktop just fine for attempted fixing and/or backing-up your files for re-install,

---

### Post by PaulInBHC on 2012-08-12
Thanks

Fortunately I don't have anything so important that I can't afford to lose it. I think at some point a hotkey combo opened nautilus so maybe I can move some stuff to the other partition.

I've been touting the glory of ubuntu at quite a few forums lately but I sure hope I don't have to explain this to someone that took my advice.

---


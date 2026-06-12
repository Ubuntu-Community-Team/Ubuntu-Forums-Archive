---
title: "Karmic ...Failed   then ICE?"
date: 2010-03-06
forum: General Help
---

### Post by Tourdog on 2010-03-06
I had been working on a Samba Share/ after creating a Shared Folder in my "home" directory. 

 Karmic has been running flawlessly then upon my shutting down.................   "there is a problem with the configuration server",and /usr/libgconf2-4/gconf-sanity -check-2 exited with status 256................ showed up on screen.

Also, "Failed to execute child process:

"/home/firefox/firefox

/home/tourdog/Desktop,/home/tourdog/.nautilus .......................  all these showed up within a couple minutes of my trying to gain control of what had happened.

Upon reboot ie past "grub" .............  "could not update ice authority file"  /home/tourdog/.iceAuthority.   

The most I can get out of Gnome is the "sand wave" desktop with nothing else showing.

I've tried my -17 version from grub but same result.........  no gui shows except the "sand wave".... ie same end as my once "flawless"  -18 Karmic.  ie neither works now!

What do you suggest?

tia!

---

### Post by Tourdog on 2010-03-06
To continue:

Nautilus could not create the following required folders:  /home/tourdog/Desktop,/home/tourdog/.nautilus....................... Before running nautilus please create these folders, or set permissions  such that nautilus can create them.......................


that showed up upon reboot...................  desktop is simply the "sand wave" with nothing else showing.

Is the fix:   mkdir /home/tourdog/Desktop?  
                 How do you deal with the .nautilus hidden?

Any help would be appreciated!

---

### Post by Tourdog on 2010-03-06
It looks like the "required subdirectories (folders)  (see above) are actually there.

Ran "startx" and Karmic began to load.............  all but Firefox.   I'll see to that.

---


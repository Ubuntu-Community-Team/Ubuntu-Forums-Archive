---
title: "Turn off beeping"
date: 2010-12-24
forum: General Help
---

### Post by COKEDUDE on 2010-12-24
Could someone please tell me how to turn off beeping. Every time my system restarts or I close firefox with multiple tabs it makes this REALLY annoying beeping sound.

---

### Post by noah++ on 2010-12-24
[This article]("http://www.tech-recipes.com/rx/2762/ubuntu_disable_system_beep/") describes how to disable the PC speaker at the kernel level for the current session. Kleber Souza's comment on the article shows how to make the change permanent. This solution depends on *pcspkr* having been compiled as a module instead of into the kernel. If it is not a module, then you need to recompile your own kernel that excludes it, or find some other setting that will shut it up.

Of course, if your system beeps at boot time, when Linux isn't in control yet, then you would need to disable the speaker beep either with a BIOS setting or a screwdriver.

---

### Post by uRock on 2010-12-24
Post number three in this thread gives the commands needed to turn off the internal speaker permanently. [http://ubuntuforums.org/showthread.php?t=1224408](http://ubuntuforums.org/showthread.php?t=1224408)

> **t4thfavor said:**
> Explanation:
Removes the pcspkr module from the kernel (requires sudo for elevated privs.)
```

sudo rmmod pcspkr

```Prevents the module pcspkr from getting loaded on boot by adding an entry to the file /etc/modprobe.d/blacklist.conf
```

sudo su -c "echo 'blacklist pcspkr' >> /etc/modprobe.d/blacklist.conf"

```

---

### Post by COKEDUDE on 2010-12-24
What does this mean? 

```
~ $ sudo rmmod pcspkr
ERROR: Module pcspkr does not exist in /proc/modules

```

---

### Post by noah++ on 2010-12-24
I believe that means it's compiled into the kernel, not as a module.

---

### Post by COKEDUDE on 2010-12-24
> **noah++ said:**
> I believe that means it's compiled into the kernel, not as a module.

So how would I turn off the beeping sound?

---

### Post by noah++ on 2010-12-24
Well, like I said, to do it at the kernel level you'd have to compile a custom kernel with PC speaker support excluded. Otherwise, it may be a BIOS option on your computer; or there may be some other OS-level option to disable the speaker or the system bell/beep you could Google for (if nobody else chimes in with it here).

---

### Post by wojox on 2010-12-24
What version are you using that your getting these beeper errors on?

---

### Post by COKEDUDE on 2010-12-24
> **wojox said:**
> What version are you using that your getting these beeper errors on?

Linux Mint

This turns off the login sound beep. Use the Startup Applications menu. This is located at System > Preferences > Startup Applications. I don't think this will work for the shutdown beeping. 

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/Screenshot-StartupApplicationsPreferences.png[/IMG]

Another way is to rename your startup and shutdown sounds. These are located at **/usr/share/sounds**. 

```
cd /usr/share/sounds
ls -al

```

Then use the mv command to rename them. 

The only way I have found to turn off the firefox beeping is with **sound preferences**. Select your sound theme as none. 

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/Screenshot-SoundPreferences.png[/IMG]

[http://www.tech-recipes.com/rx/2736/ubuntu_disable_startup_sound/](http://www.tech-recipes.com/rx/2736/ubuntu_disable_startup_sound/)
[http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/)
[http://ubuntuguide.net/how-to-turn-offdownup-login-sound-when-ubuntu-gnome-startup](http://ubuntuguide.net/how-to-turn-offdownup-login-sound-when-ubuntu-gnome-startup)

---


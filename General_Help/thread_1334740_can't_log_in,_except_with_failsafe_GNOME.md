---
title: "can't log in, except with failsafe GNOME"
date: 2009-11-22
forum: General Help
---

### Post by ikacer on 2009-11-22
My computer boots to the log in screen, but when I try to log in it goes to a loading screen, then a black screen for a few seconds, then back to the log in screen. If I select "failsafe GNOME" from the options at the bottom, it works though.

Any ideas on what I might try to fix this will be appreciated.

Also is there a log of what is happening when I try to log in?

---

### Post by lidex on 2009-11-22
/var/log/messages
/var/log/dmesg

Could be gdm failing to load. Go into synaptic, search "gdm", mark for re-install and apply. Open "system>administration>boot-up manager" and make sure gnome display manager is ticked. Reboot.

More:
[http://ubuntuforums.org/showpost.php?p=8159301&postcount=6]("http://ubuntuforums.org/showpost.php?p=8159301&postcount=6")

---

### Post by ikacer on 2009-11-23
I tried the re-install tip with a few different packages and unfortunately, no luck.

From my syslog I am getting this output, having entered my username and password around 01:14:22, and the 01:14:40 is around when the login screen comes up again
```
Nov 23 01:14:23 fredreT61 pulseaudio[3674]: x11wrap.c: XOpenDisplay() failed
Nov 23 01:14:23 fredreT61 pulseaudio[3674]: module.c: Failed to load  module "module-x11-publish" (argument: "display=localhost:0.0"): initialization failed.
Nov 23 01:14:26 fredreT61 gdm-simple-slave[3697]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 23 01:14:26 fredreT61 acpid: client 3524[0:0] has disconnected
Nov 23 01:14:26 fredreT61 acpid: client 3524[0:0] has disconnected
Nov 23 01:14:26 fredreT61 acpid: client connected from 3698[0:0]
Nov 23 01:14:40 fredreT61 acpid: client connected from 3698[0:0]
```

I don't get any of these messages when I log in with failsafe GNOME, but I'm not sure if any of these are actually related to the problem.

---

### Post by lidex on 2009-11-23
> WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
That could be your problem. Looking in my /etc/gdm folder I have "gdm.conf" and "gdm.conf-custom" but no "custom.conf"
Your system is looking for a file that does not exist. A lot of gdm info in those files BTW - you might have a look. Also might try running gdm setup:
```
sudo gdmsetup
```

---

### Post by ikacer on 2009-11-23
When I run gdmsetup I get this error:
```
(gdmsetup:6641): Gtk-WARNING **: cannot open display: localhost:0.0

```

I'm beginning to suspect that this is an xorg issue. I found this page which may be relevant ([http://www.softpanorama.org/Xwindows/Troubleshooting/can%27t_open_display.shtml]("http://www.softpanorama.org/Xwindows/Troubleshooting/can%27t_open_display.shtml") but right now I need to get some sleep. I'll see if I cant fix this tomorrow.

---

### Post by saberworks on 2009-11-23
I just updated a bunch of packages in xubuntu this morning and ran into the same thing -- when logging in, it would flash my screen a bunch of times and then drop me back to the login screen.  I just started an xterm session, apt-get remove gdm, and the graphical login manager is gone.  Now when my computer boots, I get a text login and I can type "startx" to get to xfce.  This may help you if you need to login in the meantime but is probably not a permanent fix (you can just apt-get install gdbm again if you want it back).

---

### Post by saberworks on 2009-11-23
After reinstalling gdm, the problem came back.  So I ran "gdmsetup" as root (as recommended earlier in this thread).  I clicked the "unlock" button, then changed the radio to auto login and then back to the default, then pressed closed, exited, rebooted, and everything works now.

---

### Post by ikacer on 2009-11-23
I finally got it working, though I never pinpointed exactly what the problem was. Here's how I fixed it.

First off I found that the "cannot open display" error was unrelated, and is because I was running in failsafe mode.

I wanted to see if this error was due to my user settings, so I created a new user account which worked fine. This indicated that the problem was with my preferences in my /home/USERNAME folder, so I went through and deleted every preference file and folder that might possibly be related to the problem, which fixed it.

This is a sort of brute force method, and I suggest that before anyone try this they backup anything important.

Also, thanks to everyone who responded in this thread :)

---

### Post by ikacer on 2009-11-23
I discovered the precise cause of my troubles now. I had installed MCNP yesterday, which made some changes to my ~/.bashrc file. Part of this was:
```

          # -------------------------------------------------
          # set shell environment variables for MCNP5

            export PATH
            PATH="$TARGET_BIN:\$PATH"

            export DISPLAY
            DISPLAY="localhost:0.0"
          # -------------------------------------------------
```

the DISPLAY="localhost:0.0" was causing the error. I edited my bashrc, bash_profile, and profile files to remove this and now everything works perfectly.

---


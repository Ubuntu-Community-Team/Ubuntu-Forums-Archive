---
title: "Computer unstable using karmic"
date: 2010-02-22
forum: General Help
---

### Post by Cue2 on 2010-02-22
I seem to be having problems with karmic and perhaps GRUB2

sometimes when the computer boots after the GRUB2 screen I get a flashing cursor (underscore) and nothing happens. I end up having to hard reset. other times I'm using karmic and everything seems ok and then it suddenly freezes. I haven't been able to find a reason. Memtest seems ok too.

which log file is likely to show me where things went wrong?

thanks in advance.

---

### Post by Cue2 on 2010-02-23
Anybody have even a stab in the dark suggestion?

---

### Post by ubunterooster on 2010-02-23
sudo apt-get update grub?

---

### Post by Cue2 on 2010-02-23
> **ubunterooster said:**
> sudo apt-get update grub?

thanks for the reply ubunturooster, I've reinstalled grub2 but unfortunately it didn't help. 

I'd like to look at some log files to see where things failed but I don't know where to look.

---

### Post by ubunterooster on 2010-02-23
'dmseg | less' reads kernel output after boot.
"cat var/log/messges | less"  examines system logging.

---

### Post by ubunterooster on 2010-02-23
when this happens type "telinit 1" and hit enter [return]. You should get a grey (some say gray) screen w/ a large X in the center. Hit cntrl+alt+backspace.
  under var/log/messages pay attention to lines starting w/ EE (error) also see the Xorg log file under var/log

see also the .Xsessions-error in home direcory if such a file exists

---

### Post by Cue2 on 2010-03-19
Sorry for the late reply I have been waiting until a crash to try and see the last entry just before the crash since I couldn't spot any obvious fatal errors in my logs.

My computer crashed at 4:58 and this is the last entry before the crash.
```

Mar 19 04:58:12 COSMOS NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```
Could it be this which is causing it, is this bug known to cause instability.

---

### Post by ubunterooster on 2010-03-19
Not likely, this only refers to networks. More likely this is another symptom. Are there any other errors within two minues?

  Btw, did you fill out a bug report?

---

### Post by Cue2 on 2010-03-19
> **ubunterooster said:**
> Not likely, this only refers to networks. More likely this is another symptom. Are there any other errors within two minues?

  Btw, did you fill out a bug report?

I haven't filed a bug report yet, was hoping to find a specific cause before doing so. Can I file a bug if I don't know the cause or how to recreate it?

My log a few minutes before the crash looks like this

```
Mar 19 04:53:41 COSMOS gnome-session[4098]: WARNING: Failed to acquire org.gnome.SessionManager
Mar 19 04:53:50 COSMOS gnome-session[4098]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
Mar 19 04:53:50 COSMOS gnome-session[4098]: WARNING: GSIdleMonitor: IDLETIME counter not found
Mar 19 04:53:50 COSMOS wpa_supplicant[1300]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 04:54:50 COSMOS wpa_supplicant[1300]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 04:55:50 COSMOS wpa_supplicant[1300]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 04:56:13 COSMOS gnome-session[4281]: WARNING: GSIdleMonitor: IDLETIME counter not found
Mar 19 04:56:50 COSMOS wpa_supplicant[1300]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 04:57:50 COSMOS wpa_supplicant[1300]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 04:58:12 COSMOS NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```

Then before this its just spammed with
```
wpa_supplicant[1300]: CTRL-EVENT-SCAN-RESULTS
```
every 2 minutes

the only other thing that looks to be of any significance is a segmentation fault almost an hour before the crash.
> 
Mar 19 04:02:53 COSMOS kernel: [10602.873115] npviewer.bin[2602]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ffb5daec error 14

---

### Post by ubunterooster on 2010-03-19
04:53:41's error seems to say the error is with gnome. :( Not sure what to do here but reccomend you try installing the xubuntu-desktop or kubuntu-desktop the next time you can do something with it. An alternative, not a solution, but it should be stable using one of the other desktop enviroments. Once you have one (or both) of the above installed, log out. Near the bottom will be a drop-down menu. It should say something like "Sessions" choose xcfe or kde.

---


---
title: "Where to look for answers?"
date: 2009-10-16
forum: General Help
---

### Post by Imoen on 2009-10-16
My computer randomly will dump me back to the login screen, close firefox without warning or errors, completely freeze up etc. This happens at random times while doing different things, on different sites and under different modes including fail safe. I am desperately trying to find the cause. Can anyone tell me where I can find maybe an error log that may give me some idea to what is occurring to cause this or any ideas on what the cause is please? I am getting really tired of loosing any work I have done because my computer just crashed for no reason every hour or so.

---

### Post by Rocket2DMn on 2009-10-16
Most logs are in the /var/log directory, and some require sudo/root privileges to view, though most are public.  You can also check the .xsession-errors file in your home directory.  Have you run memtest86 from the Grub menu to test your RAM?  Random freezes and crashes sound like bad RAM.  It may also be worth checking your drives for errors with fsck - you can force a one-time disk scan at bootup by running
```
sudo touch /forcefsck
```
then rebooting your machine.
You can try debugging program and system crash based on links here - [uwiki]DebuggingProcedures[/uwiki].

---

### Post by mike555 on 2009-10-16
You might also check your computers temperature , if it doesn't have problems till it has been running for a while is a sign.........

---

### Post by Imoen on 2009-10-17
.xsession-errors log:

(gnome-settings-daemon:1639): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1639): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/kristie/.config/metacity/sessions/1037d2c82cbc40ca7b125575768035209000000016260001.ms: Failed to open file '/home/kristie/.config/metacity/sessions/1037d2c82cbc40ca7b125575768035209000000016260001.ms': No such file or directory
Unable to find a synaptics device.

(nautilus:1672): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1666): DEBUG: Adding applet 0.
** (gnome-panel:1666): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1666): DEBUG: Adding applet 1.
** (gnome-panel:1666): DEBUG: Adding applet 2.
** (gnome-panel:1666): DEBUG: Adding applet 3.
** (gnome-panel:1666): DEBUG: Adding applet 4.
** (gnome-panel:1666): DEBUG: Adding applet 5.
** (gnome-panel:1666): DEBUG: Adding applet 6.

(gnome-panel:1666): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
Initializing nautilus-gdu extension

** (nautilus:1672): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1672): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1672): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (gnome-panel:1666): DEBUG: Adding applet 7.
** (gnome-panel:1666): DEBUG: Adding applet 8.
** (gnome-panel:1666): DEBUG: Adding applet 9.
** (gnome-panel:1666): DEBUG: Adding applet 10.

(nautilus:1738): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(firefox:1765): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1765): Gdk-WARNING **: XID collision, trouble ahead

Not sure what that means :(

As for it being a hard drive problem, I don't think it is since I have one one ide hard drive 8.10 and on a sata drive 9.10 and they both do the same thing. I checked the ram and temp and they are both fine too.

---

### Post by Rocket2DMn on 2009-10-17
Hm, random crashes and freezes are notoriously difficult to track down.  I have also seen in the past that a bad power supply can be the source of these problems, causing system lockup, unexpected reboots, etc.

It sounds like your software crashes are in graphical applications - are you using restricted drivers?  What is the make and model of your graphics card?  Are you running compiz (your .xsession-errors leads me to believe you're not, but it's best to ask)?  Are you ever able to reproduce the problems or somehow force them to occur?  If so, or if they happen very regularly, we can try debugging the program crash using gdb - this works for crashes, but not usually for freezes.

---

### Post by Imoen on 2009-10-18
I'm not sure how to go about testing the power supply to eliminate that as the source of the problems. 

I don't have any idea if I'm using restricted drivers, where do I look to find out? My graphics are the ones that are on the Foxconn G31MV motherboard.

Compiz is installed but I have it set to none. If this is still causing errors I can just remove it, I think it just came installed when I installed Ubuntu. The problems seem to happen more frequently when I'm doing things like using flashchat or playing flash games but they have also occured when I have nothing open except Gimp. They happen at least 2-3 times an hour, sometimes more.


EDIT:
I just realized that this processor is an Intel® EM64T. Would these problems occur if I installed the x86 version of Ubuntu?

---

### Post by Rocket2DMn on 2009-10-18
Your processor model shouldn't be a problem, you're just not taking full advantage of it's capabilities if you use a 32 bit OS (that's OK though, you may not notice much of a difference).  Are you using the 64 bit version?  Flash and java have historically had problems in the 64 bit version of Ubuntu, though recently I understand it has been getting better.

You can check to see if you're using restricted drivers from System->Administration->Hardware Drivers.  You can also see what you make/model video card is by running:
```
lspci | grep VGA
```

Flash is known to cause problems for some people, so I wouldn't be surprised if playing flash games in FF causes it to crash sometimes.  However, is it freezing up the whole computer, or just FF?  When you say it happens when GIMP is running, is it just GIMP that freezes or is it the whole computer?

---

### Post by Imoen on 2009-10-18
I was running the 32 bit version, now I installed the 64 bit to see if it will make a difference. 

VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

System->Administration->Hardware Drivers says I am not using any drivers on my system.

When I say freezes I mean that I have to hold in my power button until the computer shuts off and then start it again.

---

### Post by Rocket2DMn on 2009-10-18
Ok, that video card doesn't use any restricted drivers.  The system freezing really sounds like a hardware problem to me - have you added or removed any pieces of hardware from your system recently (or around the time the problem started appearing)?  Have you made any changes to BIOS settings?

If you have added any hardware, please try removing it and seeing if the problem persists.  Unfortunately I don't have an adequate way to test the power supply without swapping it out for a new one (same goes for the motherboard).

As for random program crashes (not the whole system), you can try debugging based on the link I gave in post #2.  These problems may be unrelated to the system freezing.  If you are able to capture a crash while debugging, you can file a bug report.

---

### Post by Imoen on 2009-10-18
This computer (an HP Media Center M7060N) was my mom's, the motherboard died in it so she bought a new one and gave her old one to me for parts. I opted to replace the motherboard in it with the Foxconn and stick a 2.20 Ghz CPU in it in hopes to then be able to run edubuntu on it for my kids so they can be exposed to Linux at a young age instead of letting the school corrupt their minds into thinking Windows is the only real choice.

The issues that I'm having with it has been occurring since first run. I didn't spend much time until now to see what the issue is because I wasn't using it so I didn't know how bad the problem was, I just thought that my daughter was impatient and restarted it a lot. Last week my motherboard died though, so now I need to use this computer as my main one until January when I get financial aid money to fix my computer.

I guess I will try the debugging next and hope I have luck with that. Thanks for the effort, it is appreciated.

---

### Post by Imoen on 2009-10-27
This issue has been resolved. I assumed that when I ordered ram I was sent the ram speed I ordered, but the person I bought it from sent me the wrong speed which was the cause of the problem. Thanks for the help anyway.

---


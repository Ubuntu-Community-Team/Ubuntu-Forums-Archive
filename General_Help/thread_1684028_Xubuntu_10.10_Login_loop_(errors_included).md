---
title: "Xubuntu 10.10 Login loop (errors included)"
date: 2011-02-08
forum: General Help
---

### Post by hungrybelly on 2011-02-08
Recently Xubuntu froze on me during or just after startup (it was in the middle of connecting to the wireless network). I powered the computer off, and since then have been unable to login. When I enter my password, it sits a bit, flicks to a black screen with a few messages (too fast for me to read), then comes back to the login screen.

I see in the forums that other people have had similar issues with Ubuntu. Using advice from other posts, I tried reinstalling xubuntu-desktop, and I tried dpkg, and neither solved the problem. Using help from someone else's post on the topic I managed to look at my .xsession-errors file:

>  /etc/gdm/Xsession: Beginning session setup...
 Setting IM through im-switch for locale=en_US
 Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etcX11/xinit/xinput.d/default.
 /usr/bin/startxfce4: X server already running on display :0
<stdin>:1: error: invalid preprocessing directive #Those
<stdin>:2: error: invalid preprocessing directive #or
<stdin>:3: error: invalid preprocessing directive #Xft
<stdin>:4: error: invalid preprocessing directive #Xft
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
xfce4-session: Unable to access file /home/<user>/. ICEauthority: Input/output error
X10:  fatal IO error 0 (Success) on X server ":0.0"
          after 33 requests (32 known processed) with 0 events remaining.I'm new to Linux and fairly command-line ignorant/phobic; I don't know what to do with this information, but hoped someone here might be able to advise me. I set up my /home folder as a separate partition, so as I understand it my files should be safe even if I have to reinstall (& maybe I can back them up first using a liveCD? & anyway it's not many files), but I'd prefer not to reinstall the system (and programs, and settings) if I don't have to.

I'm running Xubuntu 10.10 on an Asus EEEPC 1000HE with 2GB RAM, dual-boot with Windows XP. The installation is from a CD burned sometime in the last month or so. The last thing I installed before the current problem was "Simon Tatham's Portable Puzzle Suite". From the beginning, this installation has listed 2 error messages between selecting OS and the login screen - something about a couple of files it's unable to locate (I can copy it down if need be but haven't because the screen goes by quickly enough that I'd have to restart a few times to do it). This hasn't had any obvious effect. I used the same CD to install Xubuntu on an older computer before messing with my current one, and it doesn't have these error messages.

Thanks for your time!

---

### Post by Brandon Williams on 2011-02-09
Use Ctrl+Alt+F1 to switch to a console login prompt and then login to the system. Run 'ls -l ~/.ICEauthority'. On my system, the file has "-rw-------" permissions and it is owned by me. This should be the case on your system too. If it is not, then post the output from the ls command so that we can give you specific help. In the mean time, try "chmod 644 ~/.ICEauthority && chown $USER ~/.ICEauthority".

After all of this, press Ctrl+Alt+F7 to get back to the graphical login screen and try to login again.

---

### Post by hungrybelly on 2011-02-09
The file permissions seem to be correct. I forgot to write everything down before switching back to Windows, but it went like
> -rw------- 1 $USER $USER <a date> <the filename>

When I entered the commands to change to permissions & owner I got back something like
> Changing owner <filename>: Input/Output Error

Ctrl+Alt+F7 didn't get me back to the graphical login (it went as far as the "Checking battery state...OK" message), so I went back to the console login, shutdown & restarted. When I got back to the graphical login, it gave me the same loop behavior.

---

### Post by Brandon Williams on 2011-02-10
Are you able to simply delete the file? And if you do, does it make any difference for your ability to log in? Are you able to read and write other files in your home directory?

If Ctrl+Alt+F7 doesn't get you back to the gdm login screen, the try other F keys (F2 through F9; F8 is most likely). Alternatively, restart gdm with 'sudo service gdm restart', which should automatically take you to the correct tty for gdm.

---

### Post by hungrybelly on 2011-02-11
That seems to have done it - thank you so much!

*For posterity:*
I was able to delete the file (or at least received no feedback to the contrary). Ctrl+Alt+F8 got me back to the graphical login, which showed me as logged in. I clicked my username, entered my password, and saw my desktop for the first time in over a week! After I backed up my files, I restarted the computer and was able to login properly again - I'm typing this from Xubuntu instead of Windows. Huzzah!

---


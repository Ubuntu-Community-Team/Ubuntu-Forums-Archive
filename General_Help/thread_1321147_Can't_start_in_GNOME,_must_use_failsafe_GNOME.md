---
title: "Can't start in GNOME, must use failsafe GNOME"
date: 2009-11-09
forum: General Help
---

### Post by shadowayex on 2009-11-09
I'm having a problem on my desktop where I can't boot into a GNOME session, just failsafe GNOME session.

At first, I had thought it was because I did an upgrade from Jaunty to Karmic. So I backed up my data and did a clean install. Turns out, the clean install did improve some things on the machine (drivers and such), but it did not solve the problem.

What happens when I try to boot into GNOME is the Ubuntu loading screen goes for a few seconds, then the screen flashes. The Ubuntu loading screen goes again for a few seconds, the screen flashes again. This time when the loading comes back, there's a U-shaped discoloration along the sides and bottom of the screen. The screen is frozen for a little while. Then, it flashes one more time and the loading screen is back, then loads the login stuff and I'm back at the beginning. This is a seemingly endless cycle. I've tried to boot 6 or 7 times in a row before just booting failsafe GNOME, which goes right in.

My laptop does not have this problem. I used the same install disc I burnt for my laptop on my desktop. Here are some system specs of my desktop:

Intel Pentium D 2.8 Ghz Processor
ATI Radeon X300 graphics card
160 GB HDD
1 GB RAM

It's got a 5.1 sound card, but it's onboard and works just fine.

Does anyone know what the problem is and how to fix it? If there's any more information you need, just ask.

---

### Post by Giblet5 on 2009-11-09
Permissions would do this...

Open a terminal window and run (copy/paste) the following Really Long Command, plus the subsequent commands. It will set reasonable permissions on your home directory, change ownership to your account, move your non-working configuration to a backup subdirectory and restart the session. When you log back in, everything should be reset to defaults and working well.

```
sudo find $HOME/ -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME/ -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; chmod 700 $HOME/.ssh ; chmod 600 $HOME/.ssh/* ; echo "It's all mine now! Bwah ha ha!"
mkdir dotbackup
mv .gconf* .config dotbackup
sudo /etc/init.d/gdm restart
```

If it works, memorize that first command line and help others with it. ;)

---

### Post by shadowayex on 2009-11-09
Nope. The terminal gives me this error on the first command:

bash: !": event not found

---

### Post by Giblet5 on 2009-11-09
> **shadowayex said:**
> Nope. The terminal gives me this error on the first command:

bash: !": event not found

It's really several commands chained with semicolons. That error was because of the echo statement at the end. The rest of it worked fine, but it won't hurt to do it again without the echo statement:

```
sudo find $HOME/ -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME/ -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; chmod 700 $HOME/.ssh ; chmod 600 $HOME/.ssh/*
mkdir dotbackup
mv .gconf* .config dotbackup
sudo /etc/init.d/gdm restart
```

Run the rest of the commands. It will take you back to the login screen. When you log back in, you'll be using the default config, but all of your files and data will be intact.


If you get an error message: "find: `/home/you/.gvfs': Permission denied", that can be ignored. You can't change that folder.

---

### Post by shadowayex on 2009-11-09
New results:

find: `/home/cyle/.gvfs': Permission denied
find: `/home/cyle/.gvfs': Permission denied
chmod: cannot access `/home/cyle/.ssh/*': No such file or directory

Do I just omit that part too then?

Some of the code went, some didn't. I don't know what did and didn't, but it did restart after a couple tries and no change. Still got the problem.

Edit: The code that didn't go was the backup of the settings, since the directory existed and wasn't empty.

---

### Post by Giblet5 on 2009-11-09
> **shadowayex said:**
> New results:

find: `/home/cyle/.gvfs': Permission denied
find: `/home/cyle/.gvfs': Permission denied
chmod: cannot access `/home/cyle/.ssh/*': No such file or directory

Do I just omit that part too then?

Some of the code went, some didn't. I don't know what did and didn't, but it did restart after a couple tries and no change. Still got the problem.

Edit: The code that didn't go was the backup of the settings, since the directory existed and wasn't empty.

The errors are normal and expected if you don't use ssh or rsync. It appears that you don't.


So you've tried this before...

For this problem? Did I help you with it? (Sorry if I don't remember... I do this a lot; it's a common problem.)

Try moving dotbackup to dotbackup.bak first.

```
mv dotbackup dotbackup.bak
mkdir dotbackup
mv .gconf* .config dotbackup
sudo /etc/init.d/gdm restart
```

---

### Post by shadowayex on 2009-11-09
I haven't. It may have been created when I copied and pasted your code?

Should I try that code again without the ssh stuff?

---

### Post by Giblet5 on 2009-11-09
> **shadowayex said:**
> I haven't. It may have been created when I copied and pasted your code?

Should I try that code again without the ssh stuff?

No, the 'permission denied' errors tell me that those complicated find commands both worked, and you now own every file in your home directory.

Just the backup and gdm restart should do it.

What we're doing is moving any and all interface customization out of the way (I suspect something in there is bad). It should provide the same interface as when you first logged in after the install. And it should work.


Gotta run an errand. Back in 90 minutes.

---

### Post by shadowayex on 2009-11-09
Well, I ran your code and it went without error in the terminal, but I still can't get in under regular GNOME.

---

### Post by Giblet5 on 2009-11-10
I'll pick this up at 8am EST. Long day.

Back.

It might be worthwhile to try to log in with regular Gnome, let it fail, then flip to the console via Ctrl-Alt-F1, log in, and grab a snapshot of the .xsession-errors file that was created by that failed attempt: ```
cp .xsession-errors Failed-Login.txt
```

Then log in in failsafe and post that Failed-Login.txt file's contents.

---

### Post by shadowayex on 2009-11-10
When I press CTRL+ALT+F1 I get that colorful version I mentioned earlier, and the screen locks. I have to press CTRL+ALT+DEL to get out of the locked screen.

---

### Post by Giblet5 on 2009-11-10
Bummer.

For reference though, There are usually 7 virtual terminals defined on an Ubuntu system (and most others).

Ctrl+Alt+F1 - F6 are text mode consoles.

Ctrl+Alt+F7 = Xorg graphic interface.

That is, of course, when things are working correctly...


Have you tried moving any existing xorg.conf out of the way, just to see if it affects this problem?

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.091110
sudo /etc/init.d/gdm restart
```

---

### Post by shadowayex on 2009-11-10
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory

Well, that's the result =/

---

### Post by Richiegs on 2009-11-10
I have the same problem. I am only able to log in thru Failsafe Gnome, but not Gnome.
I upgraded from Ubuntu 9.04 to 9.10 using Wubi. My PC is a desktop with Windows XP. Please help.

---

### Post by Giblet5 on 2009-11-10
> **shadowayex said:**
> mv: cannot stat `/etc/X11/xorg.conf': No such file or directory

Well, that's the result =/

To be expected when the file isn't there, which it won't be by default. If the file were there before the command, then the problem might have been fixed by moving it aside.


> **Richiegs said:**
> I have the same problem. I am only able to log in thru Failsafe Gnome, but not Gnome.
I upgraded from Ubuntu 9.04 to 9.10 using Wubi. My PC is a desktop with Windows XP. Please help.


Can YOU follow the directions from [post #10]("http://ubuntuforums.org/showpost.php?p=8283722&postcount=10")?

We need to capture the logged entries for the attempted Gnome session and **shadowayex** can't do it.

---

### Post by Richiegs on 2009-11-11
Giblet5, I am not really sure how to proceed in #10. Would you please explain to me step by step. I really appreciate your help.

---

### Post by Giblet5 on 2009-11-11
Try to log in using regular Gnome.

When it fails, and returns to the login screen, hit the Ctrl+Alt+F1 keys.

You'll flip to the text console.

Log in.

Enter ```
mv .xsession-errors Failed.txt
exit
```

Hit the Ctrl+Alt+F7 keys.

Log in in failsafe mode.

Open the "Failed.txt" file in your home folder.

Hit the New Reply button in this thread.

Click the '#' icon in the comment editor.

Paste the contents of Failed.txt inside the CODE block.

Click Submit Reply.

---

### Post by Richiegs on 2009-11-11
Giblet5, I just ran Update Manager and restarted the PC. I now have no problem logging in thru Gnome mode. I now have to test to see how stable Ubuntu 9.10 is. Thank you very much for your help

---

### Post by Giblet5 on 2009-11-11
> **Richiegs said:**
> Giblet5, I just ran Update Manager and restarted the PC. I now have no problem logging in thru Gnome mode. I now have to test to see how stable Ubuntu 9.10 is. Thank you very much for your help

Great! Maybe shadowayex will have the same luck, cuz I'm out of ideas since he can't use the text console for some reason.

---

### Post by shadowayex on 2009-11-11
No such luck.

Updates went fine. When I restarted, I get the same error when trying to log into GNOME.

However this time when I try to run the CTRL+ALT+F1 terminal, the graphical interface glitches on a whole new level xD. Stuff flashes and shakes and it's really quite intriguing to watch. Of course, I still have to use CTRL+ALT+DEL to restart the computer.

Do you think it may have something to do with my graphics card considering it's an ATI and I've heard many people have problems with Ubuntu-ATI combos?


EDIT: Interesting discovery. I can use the text terminals before I try logging into regular GNOME. They don't stop until after the first failed attempt.

---

### Post by Giblet5 on 2009-11-11
Excellent! Yes, this is probably due to the ATI card.

Let's focus and capture the log file:

Reproduce the problem.

Reboot.

Flip to the console with Ctrl+Alt+F1.

The .xsession-errors file - SAVE it.

Flip back to graphics via Ctrl+Alt+F7.

Log in in failsafe mode.

Post it.

---

### Post by shadowayex on 2009-11-11
```

(gnome-settings-daemon:1528): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/cyle/.config/metacity/sessions/10fa16ab18925cda77125795232969739300000015160001.ms: Failed to open file '/home/cyle/.config/metacity/sessions/10fa16ab18925cda77125795232969739300000015160001.ms': No such file or directory

(nautilus:1557): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Unable to find a synaptics device.
** (gnome-panel:1556): DEBUG: Adding applet 0.
** (gnome-panel:1556): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1556): DEBUG: Adding applet 1.
** (gnome-panel:1556): DEBUG: Adding applet 2.
** (gnome-panel:1556): DEBUG: Adding applet 3.

** (nautilus:1557): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1557): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1557): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
** (gnome-panel:1556): DEBUG: Adding applet 4.
** (gnome-panel:1556): DEBUG: Adding applet 5.
** (gnome-panel:1556): DEBUG: Adding applet 6.
** (gnome-panel:1556): DEBUG: Adding applet 7.
** (gnome-panel:1556): DEBUG: Adding applet 8.
** (gnome-panel:1556): DEBUG: Adding applet 9.
** (gnome-panel:1556): DEBUG: Adding applet 10.

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead

(firefox:1620): Gdk-WARNING **: XID collision, trouble ahead
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(gnome-panel:1556): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' failed
gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```

That's the entire content of the file.

---

### Post by Giblet5 on 2009-11-11
It appears that there is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/460478") on Xorg crashing during login.

That's for Xubuntu, but the errors seem to be the same.

---

### Post by shadowayex on 2009-11-11
Alright so I read through that.

Now, I may just be missing something, but I'm not sure there's a solution in there. If there is I didn't catch it at all.

---

### Post by Giblet5 on 2009-11-11
No... There's no solution in a bug report until the bug has been resolved.

But it's in front of the Ubuntu dev team now.

I think your options are limited: endure failsafe mode until a fix is released, do a backup and install Jaunty (or SUSE, or CentOS, etc), or replace the graphics card.

**If it were me**, I would buy an nvidia card and sell the ATI card on eBay. I've only owned one ATI card and it was not a good experience. I hear things have improved since then, and you can even get an ati driver for linux now, but I've already been prejudiced against them.

---

### Post by shadowayex on 2009-11-12
Yeah. The computer was bought used and the ATI card was in it. I've always preferred nVidia. The problem is I do not have the monetary resources to replace the card. Although I do have a card on hand, my computer does not have the proper slot, inconveniently enough.

I've got Karmic on my laptop and I'll probably use that for my primary system until the bug is resolved.

Thank you for all of your support. You're a smart person and very patient. I wish all of my tech support experiences went like this xD

Although my issue is not resolved, I feel much better about this experience than some I've had that even ended up resolved (i.e. getting my Xbox 360 replaced, >_< Microsoft).

Once again. thank you for your time and effort and I hope if I ever have any more problems I can work with you again. Or maybe even help you out if I somehow manage to discover something you don't know. Doubtful, but hey, it could happen xD

---

### Post by UCSDPulsePower on 2009-11-12
I am a native mac user, stuck on PCs at work, and so I just flipped all the PCs to Ubuntu...and one, a Dell Dimension 9100 didn't allow me to login to Gnome.  I could however log into failsafe gnome.  I ran a system profile to find what graphics card I had, and found that it was a Radeon X300...
I found the drivers for ubuntu here:
[http://packages.ubuntu.com/hardy/xorg-driver-fglrx](http://packages.ubuntu.com/hardy/xorg-driver-fglrx)
and downloaded/installed it through terminal...
reboot...
And I can now login to Gnome...

That driver package supports a variety of radeon drivers so it is at least worth a look if you are having the same problem as me...which it seems a number of people are...

Thanks to all the people who have posted help to get me this far...

---

### Post by shadowayex on 2009-11-12
Well what do ya know? I have a Dell Dimension 9100. And installing the drivers you mentioned worked! First non-failsafe boot on my desktop.

The boot was a little slow, but it's in regular GNOME so I can finally do stuff =D.

Thanks for that link.

---

### Post by bige610 on 2009-11-19
i have the same problem, however when i go to install this package i get this error

Error: Dependency is not satisfiable: linux-restricted-modules-common

---

### Post by efflandt on 2009-11-20
If you can get into **Failsafe GNOME** and have networking, try using Synaptic to install **xorg-driver-fglrx** package.  After grabbing the list of latest packages, just let it finish updating its quick search index, then type in ati to narrow down the list.

Just to see how it would work, I initially installed Jaunty on an old PIII 550, 320 MB RAM, Linksys WUSB56GSC wireless, and that worked fine.  Flash in Firefox did not have a real high framerate, but worked smoothly with no sound gaps.

So I tried Xubuntu 9.10.  That worked fine (including wireless) until after the first set of updates.  Then I could no longer log into Xfce.  It would do some gyrations and dump me back to login screen.  I could get into xterm or the console, but not into a desktop.  But I thought that was on a bad partition because I was getting disk read errors, so I installed it in place of the well working Jaunty, made no configuration changes, and same problem looping back to login after updates.

So I installed Ubuntu 9.10 thinking it may be more refined.  But even when I rebooted from initial install, I could not get into GNOME.  Instead of looping back to login, it simply started to form the desktop, then locked up solid with no cursor movement, and no console with Ctrl-Alt-Fn keys.  Then I noticed "Failsafe GNOME" and that worked fine, except no sound or networking icons, so I could configure, but not activate wireless.  Connecting my old WET11 wireless bridge to ethernet got me on-line.

Although, my AMD64 3200+ desktop works fine with default modules for its ATI card, I had seen lots of discussion about ATI.  So from Failsafe GNOME I used Synaptic to install xorg-driver-fglrx on the old PC, and after reboot I was able to log into GNOME. Firefox flash was sluggish in gnome, but audio was smooth with no interruptions.

So I reinstalled Xubuntu 9.10 to see if xorg-driver-fglrx before doing updates fixes that, and if it runs more efficiently than gnome.  I am now able to boot and log into Xfce after updates, but flash seems even more sluggish than Karmic, with pauses in sound and video.  So it looks like that old computer will be running 9.04 Jaunty for now.

---

### Post by giest on 2009-12-31
Hey Giblet5, thanks!!!  You solved my problem, I was not a permission issue; it was a startup script that I must have edited and forgot the 'fi'.  

xsession-errors caught the problem, and once I deleted the script, everything worked.

---


---
title: "Log in failing on most users"
date: 2010-08-15
forum: General Help
---

### Post by oli-UK on 2010-08-15
I have ubuntu 10.4 set up with multiple logins - 1 for me, one for each child etc

recently logging in become a bit unreliable - i thought i was mis-typing the passwords but on closer looking the passwords were ok (faulty passwords produces "authentication failure)

Using the correct passwords the screen blanks for a second and then returns to the list of possible logins 

I cannot log in except as one of the children - could this be because their logins have been used less often and less recently

Everything was working well and I have not knowingly changed anything except the passwords after the problems started in order to solve what i thought was a simple mis-typing problem

I can log in as the children but their logins obviously do not have permission to do much
I also have a bootable puppy CD
Unfortunately I am also a total noob but determined not to backslide into XP because up to now Ubuntu has been fantastic

Any help greatly appreciated

---

### Post by chopinhauer on 2010-08-15
> **oli-UK said:**
> 
Using the correct passwords the screen blanks for a second and then returns to the list of possible logins 


What probably happens is that the session exits after just a second. Try with another session: “GNOME failsafe” to begin with and if that doesn't work choose “xterm” and then launch Metacity, Nautilus and Firefox to be able to read files and post to this forum:
```

metacity --replace &
nautilus &
firefox &

```

The errors from your previously failed session should be in the file .xsession-errors.old in your home directory, please retrieve it and post it.

My guess is you uninstalled **gnome-session** or another important part of the system, so when GDM (the login screen) tries to launch a GNOME session it fails.

---

### Post by oli-UK on 2010-08-15
Thanks for reading my post

Your thought that the session starts and then exits quickly is exactly what appears to happen 

This is the contents of the .xsession-errors.old for one of the affected users

 
(gnome-settings-daemon:4801): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Unable to find a synaptics device.
Window manager warning: Failed to read saved session file /home/oncs99/.config/metacity/sessions/105060c7e2315af896128190129336568400000047370023.ms: Failed to open file '/home/oncs99/.config/metacity/sessions/105060c7e2315af896128190129336568400000047370023.ms': No such file or directory
Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':5.0'.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :5.0.

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/workspace_switcher_screen0' was not being monitored by GConfClient 0x8e245a8

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/window_list_screen0' was not being monitored by GConfClient 0x8e245a8

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/show_desktop_button_screen0' was not being monitored by GConfClient 0x8e245a8

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/indicator_applet_screen0' was not being monitored by GConfClient 0x8e245a8

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/notification_area_screen0' was not being monitored by GConfClient 0x8e245a8

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/clock_screen0' was not being monitored by GConfClient 0x8e245a8

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/applet_0' was not being monitored by GConfClient 0x8e245a8

(gnome-panel:4838): GConf-WARNING **: Directory `/apps/panel/applets/applet_1' was not being monitored by GConfClient 0x8e245a8
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :5.0.

---

### Post by chopinhauer on 2010-08-15
> **oli-UK said:**
> 
This is the contents of the .xsession-errors for one of the affected users


Unfortunately it doesn't tell much (maybe .xsession-errors.old has more informations). Did you manage to log in into an alternative session with one of the affected users? If you open an 'xterm' session and run 'gnome-session' from a terminal, does it crash?

---

### Post by oli-UK on 2010-08-15
Hi 

sorry i edited my post just after i put it up with what i hope is more useful but you probably have not  needed to  refresh your screen - my fault

logging in to an xterm session works ok and then 'gnome-session' starts gnome which is also ok.

I will have a look at another user and confirm what is happening

Thanks

---

### Post by oli-UK on 2010-08-15
I checked another user and this is the same 
Gnome and failsafeGnome both blank the screen for a second and return to the list of logins (?GDM screen?)
'gnome-session' run from xterm is ok

I have the .xsession-errors.old for this user also

(gnome-settings-daemon:8812): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/adminbod/.config/metacity/sessions/106301860bdac3be33128190387091604500000088000001.ms: Failed to open file '/home/adminbod/.config/metacity/sessions/106301860bdac3be33128190387091604500000088000001.ms': No such file or directory
Unable to find a synaptics device.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :16.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :16.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :16.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':16.0'.

---

### Post by chopinhauer on 2010-08-15
> **oli-UK said:**
> 
(gnome-settings-daemon:8812): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed


This must be the main error. Reinstall **gnome-settings-daemon**:
```
sudo apt-get --reinstall install gnome-settings-daemon
```
to be sure that its global configuration is correct and if that doesn't work, rename the directories .gconf/apps/gnome-settings and .gconf/apps/gnome_settings_daemon in your users home directories (for example append '.bak' to the names).

---

### Post by oli-UK on 2010-08-15
I ran sudo apt-get

$ sudo apt-get --reinstall install gnome-settings-daemon
[sudo] password for oncs99: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 libjline-java rhino linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 258kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main gnome-settings-daemon 2.28.1-0ubuntu2 [258kB]
Fetched 258kB in 1s (218kB/s)                 
(Reading database ... 204036 files and directories currently installed.)
Preparing to replace gnome-settings-daemon 2.28.1-0ubuntu2 (using .../gnome-settings-daemon_2.28.1-0ubuntu2_i386.deb) ...
Unpacking replacement gnome-settings-daemon ...
Processing triggers for hicolor-icon-theme ...
Setting up gnome-settings-daemon (2.28.1-0ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
$

 After this, attempting to start gnome from the login screen caused the screen to blank and stay blank except for a small white flashing cursor

I have renamed .gconf/apps/gnome-settings appending .bak

I cannot find .gconf/apps/gnome_settings_daemon

The closest i can get is /usr/lib/gnome-settings-daemon
Should I rename this?

I will be away for the next 24hours I hope we can resume after that
Thank you so much for your help so far

---

### Post by chopinhauer on 2010-08-15
> **oli-UK said:**
> 
 After this, attempting to start gnome from the login screen caused the screen to blank and stay blank except for a small white flashing cursor


The screen reverted to text mode (like the one you obtain with CTRL+ALT+F1 and CTRL+ALT+F7 to return to 'gdm'), meaning you will find pretty interesting debugging informations in .xsession-errors .

If you don't find the login screen anymore, log into a text mode console and type:
```

sudo service gdm restart

```> **oli-UK said:**
> 
The closest i can get is /usr/lib/gnome-settings-daemon
Should I rename this?


Yes, this way a default configuration can be reestablished.

**Edit**: Ooops, I read .gconf/apps/gnome-settings-daemon. For /usr/lib/gnome-settings-daemon I would say to leave it alone.

---

### Post by Madwand on 2010-08-15
I'm having a similar problem, although I thought it was caused by my efforts to add a second monitor. I've started a post here:

[http://ubuntuforums.org/showthread.php?p=9724983#post9724983](http://ubuntuforums.org/showthread.php?p=9724983#post9724983)

I'll be very curious to see what fixes the problem! I don't have any secondary accounts so it may be tricky for me to try certain things.

---

### Post by oli-UK on 2010-08-17
Hi and thankyou

Renamed  /usr/lib/gnome-settings-daemon 

Everything now ok

BTW had a lot of trouble using rename even after chmod the directory and file and ended up booting a puupy live CD because it seems to access and write anything - bit scary but cool

Thankyou  so much for the help

---

### Post by chopinhauer on 2010-08-17
> **oli-UK said:**
> 
Renamed  /usr/lib/gnome-settings-daemon 

Everything now ok


I am happy that everything is ok, however when I told you to move this directory I was thinking about another one. :-)

Now that everything is working try reinstalling gnome-settings-daemon again, hoping it will install correctly:
```

sudo apt-get --reinstall install gnome-settings-daemon

```

---

### Post by oli-UK on 2010-08-17
Done  that
If Gnome is selected - After entering password, screen blank for 5 seconds then back to GDM screen

'gnome-session' from x-term works ok

---

### Post by oli-UK on 2010-08-17
Just tried another user after reinstall of gnome-settings-daemon.

Login worked correctly the first time straight into gnome from GDM screen 

Tried to log in a second time and now this user also has the same problems
Does gnome-settings-daemon do something different or extra the 2nd time the login is used?

---

### Post by chopinhauer on 2010-08-17
> **oli-UK said:**
> 
If Gnome is selected - After entering password, screen blank for 5 seconds then back to GDM screen


So the **wrong** solution of moving the gnome-settings-daemon binary directory is actually the **right** one? I can not say what the problem can be, but as a workaround you can always move the /usr/lib/gnome-settings-daemon/ directory again.

You might experience some problems in the future (with themes, keyboard config), but for the moment leave it there.

You might also post another thread with a title like &#8220;gnome-settings-daemon refuses to start&#8221; where you explain your situation and your workaround. An input from other users might be beneficial.

---

### Post by oli-UK on 2010-08-17
Thanks for the help.
I will start a new thread as you suggest
For now I have a working system and have learnt may things. Fantastic

---


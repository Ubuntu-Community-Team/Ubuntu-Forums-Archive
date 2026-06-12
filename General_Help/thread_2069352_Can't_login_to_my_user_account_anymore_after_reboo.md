---
title: "Can't login to my user account anymore after reboot"
date: 2012-10-10
forum: General Help
---

### Post by Jimboland on 2012-10-10
I didn't install or change anything, and suddenly I can't login to my account anymore. I tried to login with guest, and thats working fine.
I created a new account, and thats not working either.

I tried to purge some applications that start automatic like Clementine and Rainlendar but it didn't help.

I wanted to update my video driver but I don't have any rights onder the guest account. So what can I do? I can't access my system anymore!

I'm using 12.04 with all the latest updates. The updates are installed automatic as I added the command:

***apt-get update && apt-get upgrade -y***

to my rc.local.

---

### Post by Jimboland on 2012-10-10
Somebody, please!!!

---

### Post by steeldriver on 2012-10-10
Do you really mean that you can't log in - or just that you can't log in via the graphical interface? have you tried Ctrl-Alt-F1 and logging in at a virtual terminal? This will narrow it down to an X session problem versus an actual auth problem

If all else fails you can boot into recovery mode and fix things from there - but it's hard to be specific without more info from you

---

### Post by Jimboland on 2012-10-10
I mean I can't log in from the GUI. I was able to log in from the virtual terminal, thats how I purged the applications.

I would like to give you more info, but I really don't know what else I can share. My knowledge stops here..

---

### Post by steeldriver on 2012-10-10
Well common causes for those symptoms are

[LIST=1]
[*]no space left on the drive / home partition - since guest login works I think that's unlikely but you can check with 'df -h'
[*]user's home dir unwritable due to screwed up ownership or permissions
[*]user's Xauthority or ICEauthority file unwriteable due to screwed up ownership or permissions
[/LIST]
The last 2 can be checked with


```
ls -ld /home/*username*
```
```
ls -l /home/*username*/.{X,ICE}authority
```

---

### Post by Jimboland on 2012-10-10
Thanks for your help!

My home partition is large enough, 500GB+, and i'm sure more then 400 is free. And I have 120+ for my / root partition.

[U]guest-Wbvmmk@24DAC:~$ ls -ld /home/jimmy
drwxr-xr-x 71 jimmy jimmy 4096 Oct 10 19:36 /home/jimmy
guest-Wbvmmk@24DAC:~$ 
[/U]
Looks normal.

[U]guest-Wbvmmk@24DAC:~$ ls -l /home/jimmy/.{X,ICE}authority
-rw------- 1 jimmy jimmy 72582 Oct 10 19:36 /home/jimmy/.ICEauthority
-rw------- 1 jimmy jimmy     0 Oct 10 19:36 /home/jimmy/.Xauthority[/U]

I don't know, I don't even know how this could happen, I didn't change nothing.

---

### Post by Jimboland on 2012-10-11
After 10 minutes I have exactly the same problem on my notebook!

Can somebody explain me what to do, I'm not a Linux expert, I don't want to mess up my installation Again.

How can I make it work without screwing up everything? Please!

edit:

I think its an app thats automatically updated during startup (via the repo's)
But how can I check which one or what caused it?

Ubuntu is supposed to be easy to use, how the hell my mom would find out what to do is she had this problem with only Ubuntu to use?

---

### Post by cashmank on 2012-10-16
I have the same problem. There's enough space on my installation, but I cannot access my home folder or the authority files.

---

### Post by Zieb on 2012-10-16
I just put this elsewhere (the wrong forum probably seeing I got there through Google; stupid me), but I am having the exact same problem with Lubuntu.  Worked fine before on install.  Then I tried to get back in and couldn't.  

Pswd to change password to "1" to make sure it was idiot proof, and still no luck.  Checked and my username is correct.  No clue what's going on.

---

### Post by Zieb on 2012-10-16
Jimbo, I know you said you're not the most advanced on this, but I'm much worse.  I think it has something to do in my case with the way I installed (I had no cd, no jumpdrive, only an old wubi download of 11.10 on windows XP).  I then typed some stuff in the xterm I found online without looking into it.  

Result, I have no idea what I have here.  :)  However, on the up side, and to show how dumb I am, I am using ubuntu again right now after a very, very simple bit of thinking.  If you're in the same boat as me, just do what I did.  Choose something on the login besides lubuntu.  Ubuntu and LXDE as options work just fine with my username and password.  I'm sure someone here can explain to me exactly how I herped the derp here.  :)

---

### Post by Jimboland on 2012-10-16
"Jimbo, I know you said you're not the most advanced on this, but I'm much worse"

Well, you gave me hope again!:P:P I started to dig in to my problem !

I changed all the permissions from .Xauthority as well as .ICEauthority.

[B]-rwxrwxrwx 1 jimmy jimmy 74788 Oct 16 23:59 /home/jimmy/.ICEauthority
-rwxrwxrwx 1 jimmy jimmy    50 Oct 16 23:59 /home/jimmy/.Xauthority
guest-VFtBZz@24DAC:~$ [/B]


The file permissions of my home directory are unchanged.

**drwxr-xr-x 71 jimmy jimmy 4096 Oct 17 00:00 /home/jimmy**

But I still can't login to my system. One correction I would like to make is, I'm using standard Ubuntu, not lubuntu.

I tried to login in an Ubuntu 2D session, but it didn't work for me.

---

### Post by Zieb on 2012-10-17
> **Jimboland said:**
> 
But I still can't login to my system. One correction I would like to make is, I'm using standard Ubuntu, not lubuntu.

I tried to login in an Ubuntu 2D session, but it didn't work for me.
I didn't try that one.  Some of the others worked for me.  

I broke down and reinstalled though in the end.  I didn't add lubuntu this time.  I'm using whatever the default experience is called again (Unity is it?) and am just concentrating on getting as many lightweight applications as possible installed to speed things up.  If this breaks down again, I think I'll admit an aging netbook is too little computer for Ubuntu.

---

### Post by Jimboland on 2012-10-17
Yes, its Unity :)

I think, Lubuntu is the best option if you have limited recources. Or you could try Xubuntu.  I used it myself for a long time.

I think its my faith, reinstalling and reconfiguring everything again... If I didn't hate it so much, I would have done it long time ago.

---

### Post by steeldriver on 2012-10-17
so (@Jimboland) it's still not fixed? have you had a look in the lightdm logs, something like

```
sudo grep *-r username */var/log/lightdm/
```there may be some clues there... also possibly in your ~/.xsession-errors file

---

### Post by Jimboland on 2012-10-17
Nope, problem still not fixed.

When I enter:
sudo grep *-r username */var/log/lightdm/
[I]/var/log/lightdm/x-1-greeter.log.old:[+1.14s] DEBUG: Loaded session /org/freedesktop/DisplayManager/Session0 (jimmy)
/var/log/lightdm/x-1-greeter.log.old:[+1.14s] DEBUG: unity-greeter.vala:327: Adding/updating user jimmy (jimmy)
/var/log/lightdm/x-0-greeter.log:[+0.38s] DEBUG: unity-greeter.vala:327: Adding/updating user jimmy (jimmy)
/var/log/lightdm/lightdm.log:[+0.00s] DEBUG: Starting new display for automatic login as user jimmy
/var/log/lightdm/lightdm.log:[+1.94s] DEBUG: Automatically logging in user jimmy
/var/log/lightdm/lightdm.log:[+1.94s] DEBUG: Started session 1726 with service 'lightdm-autologin', username 'jimmy'
/var/log/lightdm/lightdm.log:[+2.01s] DEBUG: Autologin user jimmy authorized
/var/log/lightdm/lightdm.log:[+2.07s] DEBUG: Writing /home/jimmy/.dmrc
/var/log/lightdm/lightdm.log:[+2.22s] DEBUG: Starting session ubuntu-2d as user jimmy
/var/log/lightdm/x-1-greeter.log:[+0.71s] DEBUG: Loaded session /org/freedesktop/DisplayManager/Session0 (jimmy)
/var/log/lightdm/x-1-greeter.log:[+0.71s] DEBUG: unity-greeter.vala:327: Adding/updating user jimmy (jimmy)
/var/log/lightdm/x-1-greeter.log:[+31.27s] DEBUG: Starting authentication for user jimmy...
/var/log/lightdm/x-1-greeter.log:[+35.20s] DEBUG: Authentication complete for user jimmy with return code 0

[/I]And this looks  completely normal to me.[I]

In my  [/I]~/.xsession-errors file     there are some clues that could be a problem. A quick search on google gave some answers, but not a specific one to my problem. So I think I need some help on this.

This is where I think the problem is:

[I]
(exe:2522): Gtk-WARNING **: cannot open display: :0

(exe:2526): Gtk-WARNING **: cannot open display: :0
gnome-session[1827]: WARNING: Detected that screensaver has left the bus
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0'.
unity-2d-panel: [WARNING] unity-2d-panel: Fatal IO error: client killed
unity-2d-shell: [WARNING] unity-2d-shell: Fatal IO error: client killed

(gnome-settings-daemon:1891): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:2068): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:2080): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:2083): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(polkit-gnome-authentication-agent-1:2069): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(indicator-keylock:2076): Gdk-WARNING **: indicator-keylock: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

indicator-sysmonitor: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
guake.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
hamster-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
classicmenu-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
[2521:2521:44334081:ERROR:x11_util.cc(102)] X IO Error detected
coverbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
[2090:2090:44355979:ERROR:chrome_browser_main_x11.cc(62)] X IO Error detected

(nautilus:2061): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


** (exe:2531): WARNING **: Could not connect: Connection refused
No protocol specified
No protocol specified

(exe:2531): Gtk-WARNING **: cannot open display: :0
No protocol specified
No protocol specified

(exe:2561): Gtk-WARNING **: cannot open display: :0

[/I]Without the emotions :)
It looks like this is some kind of bug in x.org. Because I saw more people that have this problem .
 Can this be solved if I intall xorg edgers or a different kind of xserver?

---

### Post by steeldriver on 2012-10-17
Hi I don't know what those errors indicate but can I suggest you return your ~/.Xauthority and ~/.ICEauthority files to permissions 600 if you have not done so already

```
$ ls -l ~/.{ICE,X}authority 
-rw------- 1 *user* *user* 2262 Oct  7 15:39 /home/*user*/.ICEauthority
-rw------- 1 *user* *user*   52 Oct  7 15:39 /home/*user*/.Xauthority
``` *Sometimes* authorization processes are picky about things like that - if you could then try logging in again and we can see what remaining errors show up

---

### Post by Jimboland on 2012-10-17
I changed the permissions to 600, now the output is different;


[I]** Message: moving back from GtkStatusIcon to indicator
[2493:2493:48154041:ERROR:x11_util.cc(90)] X Error detected: serial 33, error_code 3, request_code 137, minor_code 4

(gnome-settings-daemon:1867): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gnome-session[1803]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

ICE default IO error handler doing an exit(), pid = 2031, errno = 11

(bluetooth-applet:2062): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

hamster-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
indicator-sysmonitor: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
[2493:2493:48706418:ERROR:x11_util.cc(102)] X IO Error detected

(polkit-gnome-authentication-agent-1:2052): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:2057): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

guake.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(indicator-keylock:2054): Gdk-WARNING **: indicator-keylock: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0'.
[2069:2069:48706796:ERROR:chrome_browser_main_x11.cc(62)] X IO Error detected
coverbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
classicmenu-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(gnome-fallback-mount-helper:2051): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.AfcVolumeMonitor: org.freedesktop.DBus.Error.Disconnected: Connection was disconnected before a reply was received

(gnome-fallback-mount-helper:2051): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GPhoto2VolumeMonitor: org.freedesktop.DBus.Error.Disconnected: Connection is closed

(gnome-fallback-mount-helper:2051): Gdk-WARNING **: The application 'gnome-fallback-mount-helper' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.


(nautilus:2037): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.AfcVolumeMonitor: org.freedesktop.DBus.Error.Disconnected: Connection was disconnected before a reply was received

(nautilus:2037): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GPhoto2VolumeMonitor: org.freedesktop.DBus.Error.Disconnected: Connection is closed
unity-2d-shell: [WARNING] GVFS-RemoteVolumeMonitor: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.AfcVolumeMonitor: org.freedesktop.DBus.Error.Disconnected: Connection was disconnected before a reply was received[/I]

---


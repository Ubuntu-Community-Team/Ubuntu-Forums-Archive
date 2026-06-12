---
title: "Infinite login at start"
date: 2009-11-03
forum: General Help
---

### Post by Tea Bag on 2009-11-03
Hi everyone, I hope you can help me with this, i don't know what to do:

When I turn the computer on, after a "video mode error", I introduce my user and password, it gets back to this login screen to infinity.

Before having this problem I was changing some settings in Wine (to run Heroes3 correctly) and I installed a startup manager application.

Now I cannot run through the Live CD 'cause it's not recognizing it.


Please some help with this!!

Xubuntu 9.10
Acer Extensa 4420
ATI x1250


Thread in Spanish: [http://www.ubuntu-es.org/?q=node/120692](http://www.ubuntu-es.org/?q=node/120692)

Thanks a lot

---

### Post by Praxicoide on 2009-11-03
Have you tried safe mode? (ESC when grub loads) or logging in through a terminal? (alt+ctrl+F1)

If you manage to get to a terminal, you can try resetting Xorg:

sudo dpkg-reconfigure xserver-xorg

---

### Post by Tea Bag on 2009-11-03
Hi, I tried safe mode and the thing you say about xorg, but nothing. 

But I just have it even worse:

Well, I introduced <i>sudo startx</i> and I changed some options at Startup-Manager (I changed the resolution and turn off the limit of kernels shown at startup).

Now I can't choose any kernel 'cause there's no one... I can't run recovery mode nor enter with startx...

Please, I'm really lost.

---

### Post by Tea Bag on 2009-11-03
I finally can choose from some kernels and run startx. I've tried to reconfigure xorg again but nothing happened. I tried to reset Startup-Manager but I'm still stuck in login screen.

---

### Post by Praxicoide on 2009-11-04
We need to find out what the error is. From a tty, (Ctrl+Alt+F1) type

sudo /etc/init.d/gdm stop

followed by

startx

and see if it gives you any errors. If it doesn't, then maybe it is a problem with your /home directory, not a graphics problem.

---

### Post by Tea Bag on 2009-11-04
Thanks Praxicoide, now I don´t have here my laptop, but yesterday when I ran *startx* I couldn´t see any error. 
 
I tried giving permissions to my folder /home/... but nothing. Today I´ll try the command you say and we´ll see.
 
I thought maybe is an insufficient  memory issue and removed wine, I´ll try to remove even more things as well.
 
Thanks!

---

### Post by s.jegen on 2009-11-04
I think I have a similar problem with Xubuntu 9.10 (just upgraded from 9.04). If I try to log in to my usual (standard) XFCE-session I just get directed back to the gdm screen. The problem occurred after maybe the 10th boot without any config or other changes I know of.I will post my .xsession-errors log here for debugging purposes:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/silvan/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/scim-bridge.
Smart Common Input Method 1.4.9

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
/usr/bin/startxfce4: X server already running on display :0
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.9

xfdesktop[2139]: starting up
Starting SCIM as daemon ...
SCIM has been successfully launched.

(xfce4-panel:2141): xfce4-panel-WARNING **: xfce4-panel is not running
Failed to init the UI: Unknown option --sm-config-prefix

** (evince:2153): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

(xfce4-mixer-plugin:2171): Gtk-WARNING **: cannot open display: :0.0
xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfwm4: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfsettingsd: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Thunar: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfdesktop: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-power-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-menu-plugin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-places-plugin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
evince: ../../src/xcb_io.c:378: _XAllocID: Assertion `ret != inval_id' failed.
libnotify-Message: GetServerInformation call failed: Connection was disconnected before a reply was received
libnotify-Message: Error getting spec version
The application 'pidgin' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

Since I can log in per LXDE-session without any problems (except a inconsistent warning about GNOME Icon configs) the problem seems to be the XFCE-session configuration.

I have to admit that I'm a little bit relieved because I'm not the only one having the same problem... ;)

---

### Post by Tea Bag on 2009-11-04
Just a question, since I´m using Xubuntu, is this running gdm? Wasn´t it only for Gnome?
 
Tanks

---

### Post by s.jegen on 2009-11-04
[GDM is the GNOME Display Manager, a graphical login program; Ubuntu and Xubuntu use GDM by default. ]("http://tuxicity.wordpress.com/2007/03/02/some-gdm-basics-for-ubuntu-and-xubuntu-theming-and-auto-login/")

It seems...

---

### Post by Tea Bag on 2009-11-04
I hope somebody could help us, s.jegen.
 
I have a problem too with a NTFS partition (/media/DATA). I´ve been using this partition without problems. Here in /DATA I have some folders and one of them (/DESCARGAS), where jDownloader is downloading, seems to be empty (I do know it´s plenty full). 
 
When I look at GParted this partition is almost full, except 2 or 3 GB, so the information isn´t lost, but for Xubuntu is empty (no matter if I use Thunar or type ls in a terminal...). Any ideas on this??
 
As soon as I get a big HD I´m going to make a clean instal of Ubuntu 9.10 of course.
 
Thanks

---

### Post by Tea Bag on 2009-11-04
Thanks s.jegen, I´ll try [COLOR=black]*sudo gdmsetup* as well.[/COLOR]

---

### Post by zika on 2009-11-04
> **Praxicoide said:**
> Have you tried safe mode? (ESC when grub loads) or logging in through a terminal? (alt+ctrl+F1)

If you manage to get to a terminal, you can try resetting Xorg:

sudo dpkg-reconfigure xserver-xorg```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by zika on 2009-11-04
> **Praxicoide said:**
> We need to find out what the error is. From a tty, (Ctrl+Alt+F1) type

sudo /etc/init.d/gdm stop

followed by

startx

and see if it gives you any errors. If it doesn't, then maybe it is a problem with your /home directory, not a graphics problem.```
sudo service gdm stop
```or```
sudo initctl stop gdm
```because we are now using Upstart.

---

### Post by s.jegen on 2009-11-04
When I change to tty1 directly from the gdm log in menu, I can stop gdm with the initctl method suggested above. If I then start the xfc4 session with the shell command 'startxfce4' I seem to be able to start the XFCE-session without any problems (but some of the icons changed).

But then another problem occurs when I change to a virtual console and then back to the X-server running on tty7. The X-server does not seem to be able to restore the session and just shows me the panel and the desktop with almost no icons. I wonder what's wrong with it. If I only had more time to play around, but I should be doing some work for the university right now... :-)...

---

### Post by Praxicoide on 2009-11-04
Thank you Zika for the corrections.

---

### Post by Praxicoide on 2009-11-04
Perhaps you could try to move the .config and .cache directories and see if that helps...

mv $HOME/.config $HOME/.config.bak

mv $HOME/.cache $HOME/.cache.back

---

### Post by Tea Bag on 2009-11-04
I've tried what Praxicoide and zica suggested (*sudo dpkg-reconfigure xserver-xorg -phigh*) and restarted but nothing.

I tried as well this (and I get these answers):

[INDENT]*sudo servce gdm stop* --> *sudo: servce: command not found*[/INDENT]

then:

[INDENT]*sudo initctl stop gdm* --> *initctl: Unknown instance:*[/INDENT]

and:

[INDENT]*sudo service gdm stop* --> *stop: Unknown instance:*[/INDENT]

so I tried with this:

[INDENT]*sudo gdmsetup* --> *(gdmsetup:1398): Gtk-WARNING **: cannot open display:*[/INDENT]

and this:

[INDENT]*sudo /etc/init.d/gdm stop* --> [I]Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm[/I]
[/INDENT]


So, certainly zika was right, but I cannot understand then the *stop: Unknown instance:*.

On the other hand I tried to move the .config and .cache directories and after all I ran startx. No errors. 

I restarted and nothing.

---

### Post by Tea Bag on 2009-11-04
I've taken a look to these posts:
[URL="http://ubuntuforums.org/archive/index.php/t-298582.htm"]
http://ubuntuforums.org/archive/index.php/t-298582.htm[/URL] 
[URL="http://ubuntuforums.org/showthread.php?t=247429"]
http://ubuntuforums.org/showthread.php?t=247429[/URL] 

I tried giving permissions to my user and thie Xauthority but nothing happened. Any idea about this? Maybe I wrote somethin incorrectly? What is the best way to change these permissions?

Thanks again

---

### Post by zika on 2009-11-05
> **Tea Bag said:**
> I've tried what Praxicoide and zica suggested (*sudo dpkg-reconfigure xserver-xorg -phigh*) and restarted but nothing.

I tried as well this (and I get these answers):
[INDENT]*sudo servce gdm stop* --> *sudo: servce: command not found*[/INDENT]then:
[INDENT]*sudo initctl stop gdm* --> *initctl: Unknown instance:*[/INDENT]and:
[INDENT]*sudo service gdm stop* --> *stop: Unknown instance:*[/INDENT]so I tried with this:
[INDENT]*sudo gdmsetup* --> *(gdmsetup:1398): Gtk-WARNING **: cannot open display:*[/INDENT]and this:
[INDENT]*sudo /etc/init.d/gdm stop* --> [I]Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm[/I]
[/INDENT]
So, certainly zika was right, but I cannot understand then the *stop: Unknown instance:*.

On the other hand I tried to move the .config and .cache directories and after all I ran startx. No errors. 

I restarted and nothing.I'm sorry for my typo: service not servce ... I've corrected it in my post.

---

### Post by Tea Bag on 2009-11-06
No problem, if all my problems were like that... ;)

---

### Post by Tea Bag on 2009-11-08
Please, has anyone any idea?

---

### Post by stephane_messerli on 2009-11-19
Hi,

I had the exact same issue after upgrading from mythbuntu 9.04 to mythbuntu 9.10.

gdm wouldn't start my xfce4 session, and I was crashing back over and over again to the gdm login screen.

I noticed that by editing this file:
  ```
vi ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
```And changing this line:
  ```
<property name="SaveOnExit" type="bool" value="true"/>
```To:
  ```
<property name="SaveOnExit" type="empty"/>
```gmd was again able to start my xfce4 session.
Of course, you will have to modify the same file for all users, who use xfce4.

Cheers,
- Stéphane

---

### Post by Fabrys on 2009-12-21
Hello !

I've been looking for a troubleshoot for several weeks.
I've just created an account to share it here (many thanks to mr_pouit from ubuntu-fr.org) :

```
sudo mv /usr/bin/xsplash /usr/bin/xsplash.disabled
```

This command disables the Xubuntu9.10 screen with the flying pixels and lets you to log directly to your desktop.

Hope it'll help you as it has helped me :)

---


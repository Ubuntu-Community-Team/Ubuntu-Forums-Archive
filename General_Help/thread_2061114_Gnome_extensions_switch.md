---
title: "Gnome extensions switch"
date: 2012-09-21
forum: General Help
---

### Post by Mvrius on 2012-09-21
I've been trying to install and customize Gnome itself and its themes and extensions all day, and I really can't figure out why it won't work. 
Everywhere it says that [https://extensions.gnome.org/](https://extensions.gnome.org/) is supposed to have an on/off switch for the extensions, but for me it doesn't.
I'm registered, logged in, tried chrome and firefox and the plugin is enabled.

Thanks in advance.

EDIT:
Screenshot:
[IMG]http://i.imgur.com/DgJYY.png[/IMG]

---

### Post by Cheesemill on 2012-09-21
Are you actually running a Gnome Shell session?

Can you post a screenshot of your desktop please.

---

### Post by Mvrius on 2012-09-21
> **Cheesemill said:**
> Are you actually running a Gnome Shell session?

Can you post a screenshot of your desktop please.

I do believe I am. Added a screenshot to my first post.

---

### Post by Cheesemill on 2012-09-21
You're not using Gnome Shell, you're using Gnome Classic.

Surprisingly enough Gnome Shell extensions only work if you are actually using Gnome Shell.
You can use Gnome Shell by logging out and then clicking on the gear icon to select Gnome (which means Gnome Shell) before logging in again, it should look something like this...

---

### Post by Mvrius on 2012-09-21
> **Cheesemill said:**
> You're not using Gnome Shell, you're using Gnome Classic.

Surprisingly enough Gnome Shell extensions only work if you are actually using Gnome Shell.
You can use Gnome Shell by logging out and then clicking on the gear icon to select Gnome (which means Gnome Shell) before logging in again, it should look something like this...

When I log out there's 5 options (3 for gnome and 2 for unity); Gnome, Gnome Classic and another version of Gnome Classic, I am using the top (Gnome) one right now, which has a Unity symbol next to it. No idea how to get the one in your screenshots working.

---

### Post by Cheesemill on 2012-09-21
You should have an option for GNOME on your logon screen (see attached picture).

What is the output of:
```
dpkg --get-selections | grep gnome
```

---

### Post by Mvrius on 2012-09-21
compiz-gnome					install
gir1.2-gnomebluetooth-1.0			install
gir1.2-gnomedesktop-3.0				install
gir1.2-gnomekeyring-1.0				install
gnome-accessibility-themes			install
gnome-applets					install
gnome-applets-data				install
gnome-bluetooth					install
gnome-contacts					install
gnome-control-center				install
gnome-control-center-data			install
gnome-desktop-data				install
gnome-desktop3-data				install
gnome-disk-utility				install
gnome-exe-thumbnailer				install
gnome-font-viewer				install
gnome-games-common				deinstall
gnome-games-data				install
gnome-icon-theme				install
gnome-icon-theme-full				install
gnome-icon-theme-symbolic			install
gnome-keyring					install
gnome-media					install
gnome-menus					install
gnome-nettool					install
gnome-online-accounts				install
gnome-orca					install
gnome-panel					install
gnome-panel-data				install
gnome-power-manager				install
gnome-screensaver				install
gnome-screenshot				install
gnome-search-tool				install
gnome-session					install
gnome-session-bin				install
gnome-session-canberra				install
gnome-session-common				install
gnome-session-fallback				install
gnome-settings-daemon				install
gnome-shell					install
gnome-shell-common				install
gnome-shell-extensions				install
gnome-shell-extensions-common			install
gnome-shell-system-monitor			install
gnome-specimen					install
gnome-sudoku					install
gnome-system-log				install
gnome-system-monitor				install
gnome-terminal					install
gnome-terminal-data				install
gnome-themes-standard				install
gnome-tweak-tool				install
gnome-user-guide				install
gnome-user-share				install
language-pack-gnome-en				install
language-pack-gnome-en-base			install
language-selector-gnome				install
libgnome-bluetooth8				install
libgnome-control-center1			install
libgnome-desktop-3-2				install
libgnome-keyring-common				install
libgnome-keyring0				install
libgnome-media-profiles-3.0-0			install
libgnome-menu-3-0				install
libgnome-menu2					install
libgnome2-0					install
libgnome2-common				install
libgnomecanvas2-0				install
libgnomecanvas2-common				install
libgnomekbd-common				install
libgnomekbd7					install
libgnomeui-0					install
libgnomeui-common				install
libgnomevfs2-0					install
libgnomevfs2-common				install
libpam-gnome-keyring				install
libreoffice-gnome				install
libsoup-gnome2.4-1				install
network-manager-gnome				install
network-manager-pptp-gnome			install
policykit-1-gnome				install
python-gnome2					install
python-gnomekeyring				install
ssh-askpass-gnome				install
system-config-printer-gnome			install
ubuntuone-client-gnome				install

---

### Post by Cheesemill on 2012-09-21
OK, so gnome-shell is installed properly.

What are your system specs (specifically graphics card) and have you installed any drivers from the 'Restricted Drivers' application?

The reason I'm asking is that your system needs to support 3D graphics acceleration for Gnome Shell to work otherwise it automatically falls back to Gnome Classic.

---

### Post by Mvrius on 2012-09-21
> **Cheesemill said:**
> OK, so gnome-shell is installed properly.

What are your system specs (specifically graphics card) and have you installed any drivers from the 'Restricted Drivers' application?

The reason I'm asking is that your system needs to support 3D graphics acceleration for Gnome Shell to work otherwise it automatically falls back to Gnome Classic.

For some reason I can't find my graphics card in system info, but my laptop model is supposed to have a SIS Mirage 3+ 672MX.
And no, seeing as I'm not fully aware what that is, I don't think I have.

---

### Post by Cheesemill on 2012-09-21
To find out what graphics card  you have you can do:
```
lspci | grep VGA
```As far as I know the SIS cards don't support accelerated 3D so Gnome Shell is never going to work on your machine. Sorry.

I *may* be wrong so I'd wait for someone else to confirm this.

Edit - Bad news I'm afraid, I've done some googling and your SIS graphics card doesn't support 3D acceleration.

---

### Post by Mvrius on 2012-09-21
> **Cheesemill said:**
> To find out what graphics card  you have you can do:
```
lspci | grep VGA
```As far as I know the SIS cards don't support accelerated 3D so Gnome Shell is never going to work on your machine. Sorry.

I *may* be wrong so I'd wait for someone else to confirm this.

You're most likely right, my laptop isn't really capable of anything at all.

Thanks a lot for your time and effort, I really appreciate it.

---


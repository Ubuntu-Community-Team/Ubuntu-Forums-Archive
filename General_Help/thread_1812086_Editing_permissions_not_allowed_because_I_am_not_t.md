---
title: "Editing permissions not allowed because I am not the owner?"
date: 2011-07-25
forum: General Help
---

### Post by Trilogin on 2011-07-25
I am just wondering why this is happening. I just tried to use a tutorial to customize my GUI and give myself a custom launcher for Libre Office, and when I tried to copy the edited .desktop file back into my "/adam/usr/shared/applications" folder, it told me I didn't have permission to do this. I tried to edit the folder permissions and it told me that I was not able to because I am not the owner. Is there any way to fix this or do I have to re-install Ubuntu?

I am using 11.04, in case this matters.

Thanks! :)

---

### Post by jamesisin on 2011-07-25
Can you confirm that full path you are discussing?

You should be the owner of everything under ~/ (which is also called /home/username/ ).

If you do need to alter ownership, you'll use the chown command, but let's make sure you are on the right path first.

(This should be very fixable without a re-installation.)

---

### Post by Kira_Belka on 2011-07-25
sudo chown -R "your_user" "your_folder" :)))

---

### Post by AlphaLexman on 2011-07-25
Linux and Ubuntu do **NOT** have directories in /home/username/usr/share[COLOR="Red"]d[/COLOR]/applications

They **DO** have /usr/share/applications/*.desktop files...

Notice the difference between usr/share[COLOR="red"]d[/COLOR]/applications and /usr/share/applications

I think the OP has confused their username in the prompt as part of the path... 

@ADAM: post the output of...
```
ls -l /usr/share/applications
```

---

### Post by Trilogin on 2011-07-25
/usr/share/applications/ is the folder that I have to copy the .desktop file too. It is also the folder that I cannot access. 

adam@ubuntu:~$ ls -l /usr/share/applications
total 664
-rw-r--r-- 1 root root   396 2010-11-25 04:32 alacarte.desktop
-rw-r--r-- 1 root root   283 2011-04-20 19:44 apport-gtk-mime.desktop
-rw-r--r-- 1 root root   125 2011-03-30 08:39 apturl.desktop
-rw-r--r-- 1 root root   522 2011-04-19 05:30 at-properties.desktop
-rw-r--r-- 1 root root  6708 2011-07-13 00:39 bamf.index
-rw-r--r-- 1 root root   583 2011-06-28 00:40 banshee-audiocd.desktop
-rw-r--r-- 1 root root  2353 2011-06-28 00:40 banshee.desktop
-rw-r--r-- 1 root root   580 2011-06-28 00:40 banshee-media-player.desktop
-rw-r--r-- 1 root root   403 2011-04-19 15:42 baobab.desktop
-rw-r--r-- 1 root root   173 2010-05-18 21:54 billard-gl.desktop
-rw-r--r-- 1 root root   489 2011-03-23 19:28 bluetooth-properties.desktop
-rw-r--r-- 1 root root   713 2011-02-14 15:19 brasero.desktop
-rw-r--r-- 1 root root   530 2011-02-14 15:19 brasero-nautilus.desktop
-rw-r--r-- 1 root root  3213 2011-03-17 06:18 ccsm.desktop
-rw-r--r-- 1 root root   269 2011-04-07 05:17 checkbox-gtk.desktop
-rw-r--r-- 1 root root   396 2011-06-24 11:04 compiz.desktop
-rw-r--r-- 1 root root   333 2011-03-03 10:45 computer-janitor-gtk.desktop
-rw-r--r-- 1 root root   503 2011-04-19 05:30 default-applications.desktop
lrwxrwxrwx 1 root root    24 2011-07-12 02:37 defaults.list -> /etc/gnome/defaults.list
-rw-r--r-- 1 root root 36793 2011-07-13 00:39 desktop.en_US.UTF8.cache
-rw-r--r-- 1 root root   465 2011-04-19 05:30 display-properties.desktop
-rw-r--r-- 1 root root   311 2010-12-22 06:30 dopewars.desktop
-rw-r--r-- 1 root root   450 2011-06-06 03:57 empathy-accounts.desktop
-rw-r--r-- 1 root root   468 2011-06-06 03:57 empathy.desktop
-rw-r--r-- 1 root root   747 2010-12-10 06:53 eog.desktop
-rw-r--r-- 1 root root   843 2011-06-17 01:07 evince.desktop
-rw-r--r-- 1 root root   465 2011-04-14 15:02 evolution-2.2.desktop
-rw-r--r-- 1 root root  1038 2011-04-14 13:34 evolution.desktop
-rw-r--r-- 1 root root   451 2011-04-14 15:02 evolution-mail.desktop
-rw-r--r-- 1 root root   272 2011-04-14 13:34 evolution-settings.desktop
-rw-r--r-- 1 root root  1567 2011-04-27 14:30 file-roller.desktop
-rw-r--r-- 1 root root  5550 2011-06-22 18:23 firefox.desktop
-rw-r--r-- 1 root root   236 2011-05-29 14:03 flaw.desktop
-rw-r--r-- 1 root root   427 2011-04-10 20:01 gbrainy.desktop
-rw-r--r-- 1 root root   455 2011-04-21 06:37 gcalctool.desktop
-rw-r--r-- 1 root root   404 2010-12-13 04:55 gconf-editor.desktop
-rw-r--r-- 1 root root   171 2011-04-18 04:56 gdm-guest-session.desktop
-rw-r--r-- 1 root root   316 2011-05-24 14:26 gdmsetup.desktop
-rw-r--r-- 1 root root   520 2011-02-04 09:06 gedit.desktop
-rw-r--r-- 1 root root   872 2011-06-08 13:21 gimp.desktop
-rw-r--r-- 1 root root   348 2011-02-23 09:27 gksu.desktop
-rw-r--r-- 1 root root   270 2011-03-07 10:25 gmenu-simple-editor.desktop
-rw-r--r-- 1 root root   417 2011-04-14 12:47 gnome-about.desktop
-rw-r--r-- 1 root root   423 2011-04-19 05:30 gnome-about-me.desktop
-rw-r--r-- 1 root root   454 2011-04-19 05:30 gnome-appearance-properties.desktop
-rw-r--r-- 1 root root   422 2011-04-19 05:30 gnomecc.desktop
-rw-r--r-- 1 root root   483 2011-04-19 05:30 gnome-font-viewer.desktop
-rw-r--r-- 1 root root   382 2011-05-21 06:40 gnome-nettool.desktop
-rw-r--r-- 1 root root   468 2011-04-19 05:30 gnome-network-properties.desktop
-rw-r--r-- 1 root root   568 2011-05-03 01:37 gnome-panel.desktop
-rw-r--r-- 1 root root   529 2011-03-14 20:32 gnome-power-preferences.desktop
-rw-r--r-- 1 root root   414 2011-02-16 08:56 gnome-screensaver-preferences.desktop
-rw-r--r-- 1 root root   730 2011-04-19 15:42 gnome-screenshot.desktop
-rw-r--r-- 1 root root   461 2011-04-19 15:42 gnome-search-tool.desktop
-rw-r--r-- 1 root root   416 2011-04-19 05:30 gnome-settings-mouse.desktop
-rw-r--r-- 1 root root   439 2011-04-06 13:47 gnome-sound-recorder.desktop
-rw-r--r-- 1 root root   410 2011-04-08 01:32 gnome-sudoku.desktop
-rw-r--r-- 1 root root   457 2011-04-19 15:43 gnome-system-log.desktop
-rw-r--r-- 1 root root   458 2010-11-16 23:35 gnome-system-monitor.desktop
-rw-r--r-- 1 root root   452 2011-03-07 10:03 gnome-terminal.desktop
-rw-r--r-- 1 root root   520 2011-04-19 05:30 gnome-theme-installer.desktop
-rw-r--r-- 1 root root   407 2011-04-13 10:13 gnome-user-share-properties.desktop
-rw-r--r-- 1 root root   435 2011-04-06 13:47 gnome-volume-control.desktop
-rw-r--r-- 1 root root   361 2011-04-26 15:55 gnome-wm.desktop
-rw-r--r-- 1 root root   377 2011-04-08 01:32 gnomine.desktop
-rw-r--r-- 1 root root   230 2010-12-06 21:45 goldendict.desktop
-rw-r--r-- 1 root root   458 2011-04-06 13:47 gstreamer-properties.desktop
-rw-r--r-- 1 root root   379 2010-12-09 12:25 gucharmap.desktop
-rw-r--r-- 1 root root   335 2011-04-27 20:09 gwibber-accounts.desktop
-rw-r--r-- 1 root root   821 2011-04-27 20:09 gwibber.desktop
-rw-r--r-- 1 root root   335 2011-04-27 20:09 gwibber-preferences.desktop
-rw-r--r-- 1 root root   428 2011-06-08 10:07 hplj1020.desktop
-rw-r--r-- 1 root root   235 2011-03-03 22:47 ibus-setup.desktop
-rw-r--r-- 1 root root   334 2011-06-06 03:56 icedtea-netx-javaws.desktop
-rw-r--r-- 1 root root   585 2011-03-12 04:58 im-switch.desktop
-rw-r--r-- 1 root root   318 2011-04-18 11:11 indicator-datetime-preferences.desktop
-rw-r--r-- 1 root root   258 2011-04-19 05:50 jockey-gtk.desktop
-rw-r--r-- 1 root root   480 2011-04-19 05:30 keybinding.desktop
-rw-r--r-- 1 root root   445 2011-04-19 05:30 keyboard.desktop
-rw-r--r-- 1 root root   284 2011-05-19 07:55 language-selector.desktop
-rw-r--r-- 1 root root  5384 2011-05-05 01:24 libreoffice-calc.desktop
-rw-r--r-- 1 root root  4148 2011-05-05 01:24 libreoffice-draw.desktop
-rw-r--r-- 1 root root  4829 2011-05-05 01:24 libreoffice-impress.desktop
-rw-r--r-- 1 root root  3910 2011-05-05 01:24 libreoffice-math.desktop
-rw-r--r-- 1 root root  4912 2011-05-05 04:41 libreoffice-startcenter.desktop
-rw-r--r-- 1 root root  5554 2011-05-05 01:24 libreoffice-writer.desktop
-rw-r--r-- 1 root root   403 2011-04-08 01:32 mahjongg.desktop
-rw-r--r-- 1 root root   504 2011-04-14 13:41 metacity.desktop
-rw-r--r-- 1 root root 18352 2011-07-13 00:39 mimeinfo.cache
-rw-r--r-- 1 root root   343 2011-04-08 15:40 mount-archive.desktop
-rw-r--r-- 1 root root   397 2011-04-08 15:40 nautilus-autorun-software.desktop
-rw-r--r-- 1 root root   463 2011-04-08 15:40 nautilus-browser.desktop
-rw-r--r-- 1 root root   446 2011-04-08 15:40 nautilus-computer.desktop
-rw-r--r-- 1 root root   441 2011-04-08 15:40 nautilus.desktop
-rw-r--r-- 1 root root   483 2011-04-08 15:40 nautilus-file-management-properties.desktop
-rw-r--r-- 1 root root   461 2011-04-08 15:40 nautilus-folder-handler.desktop
-rw-r--r-- 1 root root   356 2011-04-08 15:40 nautilus-home.desktop
-rw-r--r-- 1 root root   278 2011-04-08 15:40 network-scheme.desktop
-rw-r--r-- 1 root root   428 2011-03-23 15:57 nm-connection-editor.desktop
-rw-r--r-- 1 root root   361 2010-12-31 06:02 onboard.desktop
-rw-r--r-- 1 root root   383 2010-12-31 06:02 onboard-settings.desktop
-rw-r--r-- 1 root root   233 2011-05-10 14:32 openbravo-erp.desktop
-rw-r--r-- 1 root root   390 2011-06-11 03:55 openjdk-6-java.desktop
-rw-r--r-- 1 root root   294 2011-06-11 03:55 openjdk-6-policytool.desktop
-rw-r--r-- 1 root root   465 2011-04-11 12:00 orca.desktop
-rw-r--r-- 1 root root   290 2011-02-14 06:47 palimpsest.desktop
-rw-r--r-- 1 root root   406 2010-12-13 04:34 pitivi.desktop
-rw-r--r-- 1 root root   150 2009-02-23 17:04 PlayOnLinux.desktop
-rw-r--r-- 1 root root   220 2011-04-11 14:08 python2.7.desktop
-rw-r--r-- 1 root root   577 2010-10-17 11:50 scorched3d.desktop
drwxr-xr-x 2 root root  4096 2011-04-25 18:01 screensavers
-rw-r--r-- 1 root root   424 2011-03-31 12:05 seahorse.desktop
-rw-r--r-- 1 root root   476 2011-04-26 15:55 session-properties.desktop
-rw-r--r-- 1 root root   481 2011-03-31 14:35 shares.desktop
-rw-r--r-- 1 root root   358 2011-04-28 18:23 shotwell.desktop
-rw-r--r-- 1 root root  1041 2011-04-28 18:23 shotwell-viewer.desktop
-rw-r--r-- 1 root root   212 2010-11-15 09:46 simple-scan.desktop
-rw-r--r-- 1 root root   467 2011-04-24 14:09 software-properties-gtk.desktop
-rw-r--r-- 1 root root   500 2011-04-08 01:31 sol.desktop
-rw-r--r-- 1 root root   353 2011-04-06 07:53 synaptic.desktop
-rw-r--r-- 1 root root  7538 2011-04-06 07:53 synaptic-kde.desktop
-rw-r--r-- 1 root root   304 2011-05-09 09:42 system-config-printer.desktop
-rw-r--r-- 1 root root   353 2011-04-20 05:51 tomboy.desktop
-rw-r--r-- 1 root root  2311 2011-03-15 14:50 totem.desktop
-rw-r--r-- 1 root root  3379 2011-03-31 15:35 transmission-gtk.desktop
-rw-r--r-- 1 root root   272 2010-12-13 05:26 tsclient.desktop
-rw-r--r-- 1 root root   249 2010-06-26 14:56 tuxtype.desktop
-rw-r--r-- 1 root root   258 2011-05-03 01:37 ubuntu-about.desktop
lrwxrwxrwx 1 root root    34 2011-07-12 02:52 ubuntu-amdcccle.desktop -> /etc/alternatives/amdcccle_desktop
lrwxrwxrwx 1 root root    36 2011-07-12 02:52 ubuntu-amdccclesu.desktop -> /etc/alternatives/amdccclesu_desktop
-rw-r--r-- 1 root root   250 2011-05-30 00:53 ubuntuone-control-panel-gtk.desktop
-rw-r--r-- 1 root root   417 2011-06-17 01:00 ubuntu-software-center.desktop
-rw-r--r-- 1 root root   247 2011-06-17 07:18 unity-preferences.desktop
-rw-r--r-- 1 root root   256 2011-05-03 01:37 update-manager.desktop
-rw-r--r-- 1 root root   288 2011-04-30 07:42 usb-creator-gtk.desktop
-rw-r--r-- 1 root root   403 2011-03-31 14:35 users.desktop
-rw-r--r-- 1 root root   403 2010-12-02 08:57 vinagre.desktop
-rw-r--r-- 1 root root   382 2010-12-02 08:57 vinagre-file.desktop
-rw-r--r-- 1 root root   453 2011-04-28 09:03 vino-preferences.desktop
-rw-r--r-- 1 root root   391 2010-02-16 17:44 warsow.desktop
-rw-r--r-- 1 root root   308 2010-09-05 14:56 warzone2100.desktop
-rw-r--r-- 1 root root   446 2011-04-19 05:30 window-properties.desktop
-rw-r--r-- 1 root root  1373 2011-04-04 16:03 wine-browsedrive.desktop
-rw-r--r-- 1 root root  1207 2011-04-04 16:03 wine.desktop
-rw-r--r-- 1 root root  1075 2011-04-04 16:03 wine-notepad.desktop
-rw-r--r-- 1 root root  1795 2011-04-04 16:03 wine-uninstaller.desktop
-rw-r--r-- 1 root root  1832 2011-04-04 16:03 wine-winecfg.desktop
-rw-r--r-- 1 root root   155 2011-04-19 06:05 wine-winetricks.desktop
-rw-r--r-- 1 root root   459 2011-04-12 03:17 yelp.desktop

---

### Post by Trilogin on 2011-07-25
> **Kira_Belka said:**
> sudo chown -R "your_user" "your_folder" :)))

so it would look like this:

adam@ubuntu:~$ sudo chown -r "adam" "/usr/share/applications/"

??

**EDIT: I just went ahead and did it without waiting for a response and it was successful. Thanks! :) Now I have a nice little custom launcher when I right click on my LibreOffice launcher!

---

### Post by hyfanious on 2011-07-25
> **Trilogin said:**
> so it would look like this:

adam@ubuntu:~$ sudo chown -r "adam" "/usr/share/applications/"

??

**EDIT: I just went ahead and did it without waiting for a response and it was successful. Thanks! :) Now I have a nice little custom launcher when I right click on my LibreOffice launcher!
 

like this: adam@ubuntu:~$ sudo chown -r adam /usr/share/applications/

no need to quotations( " )

---

### Post by enimeizoo on 2011-07-25
I'm not sure you want to change the permission  of that folder.

What you should do imho is to copy the file as root.
Make sure you are in the right directory, or use the absolute path of your file.

```
sudo cp yourfile.desktop /usr/share/applications/
```

(edit) didn't see the edit, glad it worked, but permission are like they are for a reason, you shouldn't change them whenever you need access to something. Not that big of a deal there, though, especially if you are the only actual user.

---

### Post by Trilogin on 2011-07-25
Ok. Is there a way to undo the permission change now that I have done what I wanted to do?

---

### Post by hyfanious on 2011-07-25
like this: adam@ubuntu:~$ sudo chown -r root /usr/share/applications/

---

### Post by enimeizoo on 2011-07-25
Almost the same way.

```
sudo chown -r root /usr/share/applications/
```

And don't forget to mark this as solved! :P

---

### Post by Wim Sturkenboom on 2011-07-25
Just a note:

You should not have done whatever you did. You might turn your system unusable if you change the ownership of certain directories.

Next time use '*sudo cp ...*' (in terminal) or '*gksudo yourfilemanager*' (in the graphical environment; replace yourfilemanager by the one that you're using, possibly nautilus).

---

### Post by hyfanious on 2011-07-25
> **wim sturkenboom said:**
> just a note:

You should not have done whatever you did. You might turn your system unusable if you change the ownership of certain directories.

Next time use '*sudo cp ...*' (in terminal) or '*gksudo yourfilemanager*' (in the graphical environment; replace yourfilemanager by the one that you're using, possibly nautilus).

+1

---

### Post by Trilogin on 2011-07-26
Alright, I will change the ownership back right away to root. That way I can avoid any problems lol. 

So using the "sudo" tells the computer that if I input my password, I am allowed to perform this action even though I am not the root user.. That is what I am getting out of this. 

Using "sudo" i can do just about anything, so I should be wary of what comes after that in the command I am using.

**EDIT: 

I changed the permissions back. Thanks!

---

### Post by Wim Sturkenboom on 2011-07-26
If your problem is solved, please mark it as such using the thread tools just above the first post on a / this page. Thanks

> **Trilogin said:**
> So using the "sudo" tells the computer that if I input my password, I am allowed to perform this action even though I am not the root user.. That is what I am getting out of this.Yep; similar to entering your password when you e.g. run the update manager or synaptic.

> **Trilogin said:**
> 
Using "sudo" i can do just about anything, so I should be wary of what comes after that in the command I am using.
Again yep. On the other hand, the way you changed the ownership you could accidently have wiped the full content of the directory that you took ownership of ;)

---


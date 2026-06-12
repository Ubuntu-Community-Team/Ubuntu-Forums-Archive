---
title: "Can't edit or delete my session settings"
date: 2006-05-17
forum: General Help
---

### Post by chadk on 2006-05-17
Ok, I've been having trouble with firestarter not running right and I've tried to delete it several different times, I've even tried deleting my ~./gnome2/session file and nothing gets rid of the "gksudo firestarter" line in my startup.  Likewise, I can't seem to add "thunderbird" to the startup.
Here's the session file from ls:
4 -rw-r--r--   1 chad chad  2532 2006-05-17 21:07 session
The actual file:
```

[Default]
0,id=101b0ef9d6000114771851800000294270000
0,RestartStyleHint=2
0,Priority=20
0,Program=metacity
0,CurrentDirectory=/home/chad
0,DiscardCommand=rm -f /home/chad/.metacity/sessions/1147916836-12823-2676679897.ms 
0,CloneCommand=metacity 
0,RestartCommand=metacity --sm-save-file 1147916836-12823-2676679897.ms 
1,id=101b0ef9d6000114771851800000294270002
1,RestartStyleHint=1
1,Priority=40
1,Program=gnome-volume-manager
1,CurrentDirectory=/home/chad
1,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-H1Hvd9/ 
1,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-H1Hvd9/ --sm-client-id 101b0ef9d6000114771851800000294270002 --screen 0 
2,id=101b0ef9d6000114771851900000294270003
2,RestartStyleHint=2
2,Priority=40
2,Program=nautilus
2,CurrentDirectory=/home/chad
2,CloneCommand=nautilus --sm-config-prefix /nautilus-NUkfB7/ 
2,RestartCommand=nautilus --sm-config-prefix /nautilus-NUkfB7/ --sm-client-id 101b0ef9d6000114771851900000294270003 --screen 0 
3,id=101b0ef9d6000114771851800000294270001
3,RestartStyleHint=2
3,Priority=40
3,Program=gnome-panel
3,CurrentDirectory=/home/chad
3,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-y1PmXa/ 
3,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-y1PmXa/ --sm-client-id 101b0ef9d6000114771851800000294270001 --screen 0 
4,id=101b0ef9d6000114771852000000294270005
4,RestartStyleHint=2
4,Priority=50
4,Program=gnome-cups-icon
4,CurrentDirectory=/home/chad
4,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-blnAk7/ 
4,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-blnAk7/ --sm-client-id 101b0ef9d6000114771852000000294270005 --screen 0 
5,id=101915188a000114790673700000079460001
5,RestartStyleHint=0
5,Program=evolution-alarm-notify
5,CurrentDirectory=/
5,CloneCommand=evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-6oSst7/ 
5,RestartCommand=evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-6oSst7/ --sm-client-id 101915188a000114790673700000079460001 --screen 0 
6,id=105e5adbe5000114791684800000130010000
6,Program=evolution-exchange
6,CurrentDirectory=/
6,CloneCommand=evolution-exchange 
6,RestartCommand=evolution-exchange --sm-client-id 105e5adbe5000114791684800000130010000 --screen 0 
7,id=105e5adbe5000114791700800000130010005
7,Program=gnome-terminal
7,CurrentDirectory=/home/chad
7,CloneCommand=gnome-terminal 
7,RestartCommand=gnome-terminal --sm-client-id 105e5adbe5000114791700800000130010005 --screen 0 
8,id=105e5adbe5000114791830700000130010008
8,Program=gedit
8,CurrentDirectory=/home/chad
8,CloneCommand=gedit 
8,RestartCommand=gedit --sm-client-id 105e5adbe5000114791830700000130010008 --screen 0 
num_clients=9

```

---

### Post by bswilson on 2006-05-18
The firestarter application isn't called as part of the Gnome GUI.  That's why you're not being successful.  If you really want to delete firestarter (and I don't recommend that you do), why not just uninstall it?

```
sudo dkpg -r firestarter
```

If you don't want to do that, and you really just want to disable it, then you can delete this file (but I recommend you make a backup just in case).

```
sudo cp /etc/init.d/firestarter > /home/whatever/firestarter.BAK
sudo rm -f /etc/init.d/firestarter
```

That'll do it.

---

### Post by chadk on 2006-05-18
```
chad@figment:~$ sudo dpkg -r firestarter
(Reading database ...
dpkg: serious warning: files list file for package `linux-386' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-restricted-modules-386' missing, assuming package has no files currently installed.
74104 files and directories currently installed.)
Removing firestarter ...

``` -- didn't do anything (correctly)


I removed the /etc/init.d/firestarter file and it didn't do anything.  Still prompted for a password when I started gnome.
-- which brings me back to the problem I'm having.  I can't edit my session to add/remove programs from it.

---

### Post by Ramses de Norre on 2006-05-18
What's the output of ```
dpkg -l | grep -i firestarter
ps -aef | grep -i firestarter
```
Can you open system > preferences > session and look for firestarter at the start up tab?

---

### Post by chadk on 2006-05-18
```
chad@figment:~$ dpkg -l | grep -i firestarter
pc  firestarter                            1.0.3-1.1ubuntu1 gtk program for managing and observing your

```

```
chad@figment:~$ ps -aef | grep -i firestarter
chad      8902  8882  0 16:19 pts/0    00:00:00 grep -i firestarter

```

---


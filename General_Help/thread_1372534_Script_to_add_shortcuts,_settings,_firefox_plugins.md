---
title: "Script to add shortcuts, settings, firefox plugins etc"
date: 2010-01-04
forum: General Help
---

### Post by J V on 2010-01-04
I'm writing a script to help me install my apps nice and quick when lucid arrives :)

All I need now is:
Command line to load a .profile file into compiz
Command line to make and assign shortcuts
Command line to set ctrl-alt-bckspace to restart X (in keyboard settings now)
Command line to install firefox plugins

Anyone happens to know these please help, thanks :)

---

### Post by J V on 2010-01-06
bump...

---

### Post by J V on 2010-01-07
Ok, got a lot done, following is going nowhere:
Still need a way to load the compiz.profile file
Still need a way to install firefox plugins from the CLI (Edit: Just opened firefox with the plugin urls, it did the rest)

Other than that my problems are commented out below:
```
wget http://live.gnome.org/Gedit/Plugins?action=AttachFile&do=get&target=python_indentation.tar.gz | sudo tar -xz # What goes here?
# Above needs to download, unpack, and install plugin to system wide gedit plugin directory, need help with tar command
gconftool-2 --get /apps/gedit-2/plugins/active-plugins
# Need to filter above value and add what is missing then fill in below
gconftool-2 --type list --list-type string --set /apps/gedit-2/plugins/active-plugins # What goes here?
```Any help would be appreciated!

---

### Post by J V on 2010-01-08
Ok, all I need now is a way to load the compiz.profile file, and someone to confirm the syntax of the following is correct:

```
archive=`wget -O - "http://live.gnome.org/Gedit/Plugins?action=AttachFile&do=get&target=python_indentation.tar.gz"`
$archive | sudo tar -xzf - --directory "/usr/lib/gedit-2/plugins"
archive=
```That gives me this:```
--2010-01-08 14:07:27--  http://live.gnome.org/Gedit/Plugins?action=AttachFile&do=get&target=python_indentation.tar.gz
Resolving live.gnome.org... 209.132.180.163
Connecting to live.gnome.org|209.132.180.163|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2120 (2.1K) [application/x-tar]
Saving to: `STDOUT'

100%[======================================>] 2,120       --.-K/s   in 0.005s  

2010-01-08 14:07:28 (422 KB/s) - `-' saved [2120/2120]

./test.sh: line 3: &#65533;&#65533;&#65533;Hpython_indentation.tar&#65533;Y&#65533;n&#65533;F&#65533;o>&#65533;4&#65533;AT+&#65533;&#65533;l&#65533;=&#65533;t&#65533;&#65533;&&#65533;&#65533;1lE&#65533;&#266;\J
   Q\bI&#1703;+&#65533;@}&#65533;>&#65533;&#65533;&#65533;&#65533;DR&#65533;&#65533;^&#953;&#65533;&#65533;&#65533;&#1817;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;*]&#65533;s&#65533;&#65533;": command not found

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

```

---


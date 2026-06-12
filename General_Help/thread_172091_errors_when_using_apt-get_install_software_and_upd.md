---
title: "errors: when using apt-get install software and update system"
date: 2006-05-08
forum: General Help
---

### Post by newpants2003 on 2006-05-08
Errors were encountered while processing:
 initramfs-tools
 udev
 ubuntu-minimal
 mdadm
 ubuntu-standard
 hal
 gnome-volume-manager
 hal-device-manager
 update-notifier
 usplash

when setting "initramfs-tools" it just stop there forever, dont know how to fix them.
looking for help.

---

### Post by bluevoodoo1 on 2006-05-08
from a terminal you could try...

sudo apt-get install -f

that will try to fix your problem.

---

### Post by newpants2003 on 2006-05-08
thanx , going to try...

and another thing bother me, when i quit gnome, ctrl+alt+backspace  there are some error will pup up 
some thing like [xxxxx xxxxx](some numbers) assume device write though     I/O error .....   
they keep comeing up forever, wont stop, happens when booting system too.

dont know how to config printer, device manage does show my printer, when i try to add a new printer, it shows it too, but there is not driver match my printer, choose one which the system recmmand, wont work, and try to add printer again, the printer can not be found anymore. dont want to load windows to print every time.

---

### Post by newpants2003 on 2006-05-08
running ap-get install -f 
got :evms_open_engine() failed with error code 13: Permission denied
and stop at :Setting up usplash (0.1-35) ...
what shuold i do?

---

### Post by bluevoodoo1 on 2006-05-08
[QUOTE=newpants2003]running ap-get install -f 
got :evms_open_engine() failed with error code 13: Permission denied
and stop at :Setting up usplash (0.1-35) ...
what shuold i do?[/QUOTE]

should be this... 

```
sudo apt-get install -f
```

---

### Post by newpants2003 on 2006-05-08
[QUOTE=bluevoodoo1]should be this... 

```
sudo apt-get install -f
```[/QUOTE]

that's what i did in terminal.

---

### Post by pwnb0t on 2007-03-31
I am having a similar problem, I tried running apt-get install -f and I get the same errors that I get whenever I install/remove anything:

```
sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 atanks-data libglitz1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up update-manager (0.45.2) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 481 strings at 20 - 27f8
Wrote aliases at 27f8 - 29ac
Wrote parents at 29ac - 337c
Wrote literal globs at 337c - 33e0
Wrote suffix globs at 33e0 - 67c8
Wrote full globs at 67c8 - 67ec
Wrote magic at 67ec - bdfc
Wrote namespace list at bdfc - be0c
***
Compiling /usr/lib/python2.4/site-packages/BitTorrent/PiecePicker.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/PiecePicker.py", line 1
    case "$model" in
                ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/RateMeasure.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/RateMeasure.py", line 2
    DeviceConfig() {
                   ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/RawServer.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/RawServer.py", line 1
    CheckPolicy() {
                  ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/Rerequester.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/Rerequester.py", line 1
    if [ `pidof xscreensaver` ]; then
                           ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/__init__.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/__init__.py", line 7
    @hooks [
           ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/bitfield.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/bitfield.py", line 5
    <confdir:pcm/modem.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/btcompletedir.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/btcompletedir.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/btformats.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/btformats.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/btmakemetafile.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/btmakemetafile.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/download.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/download.py", line 6
    Aureon51.pcm.default {
                         ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/fakeopen.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/fakeopen.py", line 6
    CA0106.pcm.default {
                       ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/fmt.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/fmt.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/parseargs.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/parseargs.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/selectpoll.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/selectpoll.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/spewout.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/spewout.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/testtest.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/testtest.py", line 3
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/track.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/track.py", line 5
    <confdir:pcm/front.conf>
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/BitTorrent/zurllib.py ...
  File "/usr/lib/python2.4/site-packages/BitTorrent/zurllib.py", line 6
    ICE1712.pcm.default {
                        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GDebi/DebPackage.py ...
  File "/usr/lib/python2.4/site-packages/GDebi/DebPackage.py", line 1
    ;
    ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GDebi/GDebi.py ...
  File "/usr/lib/python2.4/site-packages/GDebi/GDebi.py", line 5
    pcm.!center_lfe {
        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GDebi/GDebiCli.py ...
  File "/usr/lib/python2.4/site-packages/GDebi/GDebiCli.py", line 5
    pcm.!dmix {
        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GDebi/SimpleGladeApp.py ...
  File "/usr/lib/python2.4/site-packages/GDebi/SimpleGladeApp.py", line 5
    pcm.!dsnoop {
        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GDebi/Version.py ...
  File "/usr/lib/python2.4/site-packages/GDebi/Version.py", line 5
    pcm.!iec958 {
        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GDebi/__init__.py ...
  File "/usr/lib/python2.4/site-packages/GDebi/__init__.py", line 5
    pcm.!rear {
        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GMenuSimpleEditor/__init__.py ...
  File "/usr/lib/python2.4/site-packages/GMenuSimpleEditor/__init__.py", line 10
    pcm.!surround40 {
        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/GMenuSimpleEditor/config.py ...
  File "/usr/lib/python2.4/site-packages/GMenuSimpleEditor/config.py", line 11
    pcm.!surround50 {
        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/LanguageSelector/FontConfig.py ...
  File "/usr/lib/python2.4/site-packages/LanguageSelector/FontConfig.py", line 1
    [Desktop Entry]
                 ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/LanguageSelector/LangCache.py ...
  File "/usr/lib/python2.4/site-packages/LanguageSelector/LangCache.py", line 1
    [Desktop Entry]
                 ^
SyntaxError: invalid syntax

dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-manager
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried reinstalling update-manager and update-notifier but that didn't change anything.  I think my problems are deeper than that.

Any help is appreciated

---

### Post by pwnb0t on 2007-03-31
A little bit more info for you, after remove update-manager and update-notifier (which also removed gnome-app-install) the errors are not there anymore

Whenever I use apt-get, at the end it tried to 
Conf update-manager
Conf update-notifier
(I found this out by sudo apt-get install -fs)

Anyway, I removed them completely (incl. conf. files) and then reinstalled but I start getting the errors again
How do I make it so that apt doesn't try to Conf update-manager and update-notifier?

Would you like to see some of the lines of code that are referenced in these update errors?

Perhaps I'll just try to remove (not delete) that whole BitTorrent directory and see if that changes anything...

---

### Post by pwnb0t on 2007-03-31
Ok, so I ran
sudo mv BitTorrent GDebi GMenu* Language* /home/user

And now:
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up update-manager (0.45.2) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 481 strings at 20 - 27f8
Wrote aliases at 27f8 - 29ac
Wrote parents at 29ac - 337c
Wrote literal globs at 337c - 33e0
Wrote suffix globs at 33e0 - 67c8
Wrote full globs at 67c8 - 67ec
Wrote magic at 67ec - bdfc
Wrote namespace list at bdfc - be0c
***

Setting up gnome-app-install (0.2.21) ...
Caching application data...
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry brasero.desktop
Got non-package menu entry kmyfirewall.desktop
Generating mime map...

Setting up update-notifier (0.43.4) ...
```

And then:

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm not getting errors, but I don't know if I've now messed up some configuration or something.  Of course, whatever was giving those errors wasn't getting configured anyway.

I bet that wasn't the best way to handle the error, but at least the error is gone.

---


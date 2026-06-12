---
title: "How to recover all websites on Firefox"
date: 2011-04-29
forum: General Help
---

### Post by satimis on 2011-04-29
Hi folks,

Ubuntu 11.04 (newly upgraded)
Firefox

Accidentally click quit closing all windows of Firefox.  Please advise how to recover them.  I can't find history tab on Firefox to recover all tabs closed lately.

TIA

satimis

---

### Post by linuxyogi on 2011-04-29
press CTRL+H

---

### Post by satimis on 2011-04-29
> **linuxyogi said:**
> press CTRL+H

Thanks for your advice.

But I have to select the websites amongst the list.  Before upgrade on Firefox I can find the lately closed websites via history -> lately close website

Then I can find all of them without going through the list.  Because I have several windows (Firefox) opened.

Advice would be appreciated.  TIA

satimis

---

### Post by linuxyogi on 2011-04-29
Which version of FF are you using ?

Check if view >> toolbars >> **navigation ba**r is checked

---

### Post by satimis on 2011-04-29
> **linuxyogi said:**
> Which version of FF are you using ?

Check if view >> toolbars >> **navigation ba**r is checked

Where can I find its version?  There is no "Help" nor "view" tab on the top toolbar.  Nor can I find it on "Customize Toolbar".

$ apt-cache policy firefox```

firefox:
  Installed: 4.0+nobinonly-0ubuntu3
  Candidate: 4.0+nobinonly-0ubuntu3
  Version table:
 *** 4.0+nobinonly-0ubuntu3 0
        500 http://hk.archive.ubuntu.com/ubuntu/ natty/main amd64 Packages
        100 /var/lib/dpkg/status

```

B.R.
satimis

---

### Post by linuxyogi on 2011-04-29
Wow.

Okay backup the .mozilla folder from your /home/username (just in case)

Then

```
sudo apt-get purge firefox

sudo apt-get install firefox
```

Don't worry all your history & everything will remain intact. 

Plus you have your .mozilla folder backed up so in case something happens just close FF, replace the folder & start FF again.

---

### Post by linuxyogi on 2011-04-29
Damn !!! 

By any chance are you in fullscreen mode ?

Just press F11 & see if that helps.

---

### Post by satimis on 2011-04-29
> **linuxyogi said:**
> Damn !!! 

By any chance are you in fullscreen mode ?

Just press F11 & see if that helps.

No.  F11 starts fullscreen

$ mkdir /home/satimis/mozilla_backup

$ cp -R /home/satimis/.mozilla/* /home/satimis/mozilla_backup/

$ ls /home/satimis/mozilla_backup/```

extensions  firefox  firefox.last-version

```

$ ls /home/satimis/mozilla_backup/extensions/```

{ec8030f7-c20a-464f-9b0e-13a3a9e97384}

```

$ ls /home/satimis/mozilla_backup/firefox```

4fuplel4.default  Crash Reports  profiles.ini

```

$ sudo apt-get purge firefox
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox* firefox-globalmenu* icedtea-plugin* icedtea6-plugin*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 41.0 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 155241 files and directories currently installed.)
Removing icedtea6-plugin ...
Removing icedtea-plugin ...
Removing firefox-globalmenu ...
Removing firefox ...
Purging configuration files for firefox ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_HK.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...

```

$ sudo apt-get install firebox```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firebox
satimis@ub1004:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-globalmenu
Suggested packages:
  firefox-gnome-support firefox-kde-support latex-xft-fonts
The following NEW packages will be installed:
  firefox firefox-globalmenu
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/16.3 MB of archives.
After this operation, 40.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously deselected package firefox.
(Reading database ... 155140 files and directories currently installed.)
Unpacking firefox (from .../firefox_4.0+nobinonly-0ubuntu3_amd64.deb) ...
Selecting previously deselected package firefox-globalmenu.
Unpacking firefox-globalmenu (from .../firefox-globalmenu_4.0+nobinonly-0ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_HK.utf8.cache...
Processing triggers for python-support ...
Setting up firefox (4.0+nobinonly-0ubuntu3) ...
update-alternatives: using /usr/bin/firefox to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
update-alternatives: using /usr/bin/firefox to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (4.0+nobinonly-0ubuntu3) ...

```

Quit Firefox and restarted it.

Situation remains the same.  "View", "Help" etc. tools not visible.

satimis

---

### Post by linuxyogi on 2011-04-29
Sorry can't help you.

I guess something is wrong with your profile but cant ask you to delete that because all you want is your history.

---

### Post by imigueldiaz on 2011-04-29
> **satimis said:**
> 
Situation remains the same.  "View", "Help" etc. tools not visible.

satimis

Stupid question, but I'm lost...

I suppose that you are using 11.04 under Unity and global menu is in use, have you lost global menu from top panel?

Best

---

### Post by satimis on 2011-04-29
> **imigueldiaz said:**
> 
I suppose that you are using 11.04 under Unity and global menu is in use, have you lost global menu from top panel?

Hi,

Global menu?

On Firefox window
Top bar```

Back Forward URL_box Reload Stop Google_box Home
"Most Visited" "Getting Start" "Latest Headlines"

```

No Global menu

B.R.
satimis

---

### Post by satimis on 2011-04-30
Hi folks,

Following is my finding in re Firefox 4 on Ubuntu 11.04

- All icons(shortcut) are on the left vertical bar
- If no application started the top toolbar is black with only following tools on the right:
networking
loudspeaker
date/time
chat account/about me etc.
username
logout/restart/shut down/setting

After starting an application, e.g. Firefox
"Firefox Web Browser" will be displayed on the left top tool bar.  Placing the mouse pointer on it will popup following functions for selection;
File/Edit/View/History/Bookmarks/Tools/Help

The above functions are not displayed on Firefox window.

I think it needs time to understand all new arrangement/features of Ubuntu 11.04 !!!

B.R.
satimis

---


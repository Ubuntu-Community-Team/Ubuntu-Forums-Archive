---
title: "Cant access apps"
date: 2011-10-28
forum: General Help
---

### Post by TimEnid on 2011-10-28
Running 11.10. All of a sudden I can not get any access to my apps or dock. When i boot my PC all I get is the background pic. I can't even access the terminal. All I have is iin the upper left corner it has options for file, edit, view, go, bookmarks and help. Only thing I can do at this point is change my wallpaper. I can access my folders but no access to apps.

---

### Post by TimEnid on 2011-10-28
scratch that. I can get to the terminal if I choose Recovery Console during log in. but still no access to anything

---

### Post by e79 on 2011-10-28
If you were using Unity, try resetting it

```
unity --reset
```Also see if you can boot into the normal Gnome 2 GUI at login prompt, if it may help.

---

### Post by TimEnid on 2011-10-28
does it take a while? I tried that command in the terminal and its been at "setting update 'run_key" for about ten minutes now.

---

### Post by TimEnid on 2011-10-28
I logged in via gnome and can see my apps. I put in the reset command and got a bunch of errors:

```
tim@tim:~$ sudo unity --reset
[sudo] password for tim: 
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing mousepoll options...done
Initializing vpswitch options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
Initializing snap options...[ERROR]: Option "avoid_snap" already defined
[ERROR]: Option "snap_type" already defined
[ERROR]: Option "edges_categories" already defined
[ERROR]: Option "resistance_distance" already defined
[ERROR]: Option "attraction_distance" already defined
done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
Initializing session options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Initializing addhelper options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing debugspew options...done
Initializing decor options...done
Initializing expo options...done
Initializing extrawm options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing grid options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
```

---

### Post by TimEnid on 2011-10-28
another part of the problem is, the headers of my apps are gone. for example, the part at the top of the app that lets me drag it, minimize, close, etc are not visible for some reason.

---

### Post by dino99 on 2011-10-28
dont use "sudo" in such case, the good command is:
 unity --reset (for unity)
 gnome-panel --replace (for gnome)
 metacity --replace (for metacity)
 gnome-shell --replace (for gnome-classic)
 ...

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by gandaran on 2011-10-28
try re-installing compiz as the errors are due to missing compiz plugins

---

### Post by TimEnid on 2011-10-28
> **dino99 said:**
> dont use "sudo" in such case, the good command is:
 unity --reset (for unity)
 gnome-panel --replace (for gnome)
 metacity --replace (for metacity)
 gnome-shell --replace (for gnome-classic)
 ...

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

thanks. i ran the unity command without sudo and my last line is this
```
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a0000a
```

---

### Post by dino99 on 2011-10-28
sudo synaptic

search all the *compiz* installed packages, and purge them (complete removal), then reinstall compiz

and run again:

sudo dpkg-reconfigure -phigh -a

---

### Post by TimEnid on 2011-10-28
> **dino99 said:**
> sudo synaptic

search all the *compiz* installed packages, and purge them (complete removal), then reinstall compiz

and run again:

sudo dpkg-reconfigure -phigh -a

this worked. thanks a lot for the help.

---

### Post by TimEnid on 2011-11-10
this issue has returned. I am trying uninstall compiz and reinstall it but I'm not sure which packages have to be uninstalled. I tried uninstalling thru the software center and reinstalling but no luck. and after I uninstall Unity is also gone. I'm able to get it back but still no luck with compiz.

---

### Post by TimEnid on 2011-11-10
This is what i get when i do unity --reset

```
tim@tim:~$ unity --reset
The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity
tim@tim:~$ sudo apt-get install unity
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz compiz-gnome compizconfig-backend-gconf
Suggested packages:
  gnome-themes
The following NEW packages will be installed:
  compiz compiz-gnome compizconfig-backend-gconf unity
0 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/1,279 kB of archives.
After this operation, 5,317 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package compizconfig-backend-gconf.
(Reading database ... 203026 files and directories currently installed.)
Unpacking compizconfig-backend-gconf (from .../compizconfig-backend-gconf_0.9.5.92-0ubuntu2_amd64.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.9.6+bzr20110929-0ubuntu5_amd64.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.9.6+bzr20110929-0ubuntu5_all.deb) ...
Selecting previously deselected package unity.
Unpacking unity (from .../unity_4.24.0-0ubuntu2b1_amd64.deb) ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Setting up compizconfig-backend-gconf (0.9.5.92-0ubuntu2) ...
Setting up compiz-gnome (1:0.9.6+bzr20110929-0ubuntu5) ...
Setting up compiz (1:0.9.6+bzr20110929-0ubuntu5) ...
Setting up unity (4.24.0-0ubuntu2b1) ...
tim@tim:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing mousepoll options...done
Initializing vpswitch options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
Initializing snap options...[ERROR]: Option "avoid_snap" already defined
[ERROR]: Option "snap_type" already defined
[ERROR]: Option "edges_categories" already defined
[ERROR]: Option "resistance_distance" already defined
[ERROR]: Option "attraction_distance" already defined
done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
Initializing session options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Initializing animation options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Initializing animation options...done
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing cube options...done
Initializing debugspew options...done
Initializing decor options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing grid options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a0002d

```

---

### Post by soryu on 2011-11-10
same thing here i removed zeitgeist and all apps disappeared.
reinstalled zeitgeist apps didn't come back.
i can acces on the app that remained in the unity task bar.

this is the end of it.
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x36000e9

WARN  2011-11-10 19:23:33 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-10 19:23:33 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist

---

### Post by soryu on 2011-11-10
this worked 4 me.
[http://askubuntu.com/questions/45560/unity-stopped-working-after-zeitgeist-uninstall](http://askubuntu.com/questions/45560/unity-stopped-working-after-zeitgeist-uninstall)
and a restart

---

### Post by wildmanne39 on 2011-11-10
Deleted.

---

### Post by TimEnid on 2011-11-11
> **soryu said:**
> this worked 4 me.
[http://askubuntu.com/questions/45560/unity-stopped-working-after-zeitgeist-uninstall](http://askubuntu.com/questions/45560/unity-stopped-working-after-zeitgeist-uninstall)
and a restart

i did the unity --reset several times and restarted several times, still nothing. It seems as though i cant remove Compiz completely, in order for me to reinstall it.

---

### Post by wildmanne39 on 2011-11-11
Hi, try this please:
```
sudo apt-get install --reinstall compiz compizconfig-settings-manager
```
```
sudo apt-get install --reinstall ubuntu-desktop unity
```
Most of the time with 11.10 you can just type ccsm into the terminal when compiz settings manager opens uncheck and recheck unity plugin and that usually fixes the problem without reinstalling compiz, make sure you have ccsm installed after you install compiz.
Thank you

---

### Post by TimEnid on 2011-11-11
that didn't work either.

---

### Post by wildmanne39 on 2011-11-11
Hi, what is the complete output of the errors?
Thank you

---

### Post by TimEnid on 2011-11-11
After i type in those two commands, i dont get any errors.
```
tim@tim:~$ sudo apt-get install --reinstall compiz compizconfig-settings-manager[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0 B/1,215 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 203112 files and directories currently installed.)
Preparing to replace compiz 1:0.9.6+bzr20110929-0ubuntu5 (using .../compiz_1%3a0.9.6+bzr20110929-0ubuntu5_all.deb) ...
Unpacking replacement compiz ...
Preparing to replace compizconfig-settings-manager 0.9.5.92-0ubuntu1 (using .../compizconfig-settings-manager_0.9.5.92-0ubuntu1_all.deb) ...
Unpacking replacement compizconfig-settings-manager ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Setting up compiz (1:0.9.6+bzr20110929-0ubuntu5) ...
Setting up compizconfig-settings-manager (0.9.5.92-0ubuntu1) ...
Processing triggers for python-central ...
tim@tim:~$ sudo apt-get install --reinstall ubuntu-desktop unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0 B/893 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 203112 files and directories currently installed.)
Preparing to replace ubuntu-desktop 1.245 (using .../ubuntu-desktop_1.245_amd64.deb) ...
Unpacking replacement ubuntu-desktop ...
Preparing to replace unity 4.24.0-0ubuntu2b1 (using .../unity_4.24.0-0ubuntu2b1_amd64.deb) ...
Unpacking replacement unity ...
Processing triggers for man-db ...
Setting up unity (4.24.0-0ubuntu2b1) ...
Setting up ubuntu-desktop (1.245) ...
tim@tim:~$ 
```
I am doing this from Gnome. When i restart and try to into Unity, thats where i have the issues.

---

### Post by wildmanne39 on 2011-11-11
Hi, did you reboot?
Thank you

---

### Post by TimEnid on 2011-11-11
yes i did, just now.

---

### Post by wildmanne39 on 2011-11-11
Hi, type ccsm into the terminal when compiz settings manager opens uncheck and recheck unity plugin and give it a few seconds, it may require a restart but it did not when I did it.
Thank you

---

### Post by TimEnid on 2011-11-11
when i check the Ubuntu Unity Plugin box, i get "some key and edge bindings of Plugin Ubuntu Unity Plugin conflict with other plugins. Do you want to resolve the conflicts"

 i check to resolve the conflicts and get:
 The new value for the key binding for the action Key to execute a command in plugin Ubuntu Unity Plugin conflicts with the action Run Dialog of the Gnome Compatibility plugin.
 Do you wish to disable Run Dialog in the Gnome Compatibility plugin?
 options are; set key to execute a command; dont set key to execute command; disable run dialg

---

### Post by wildmanne39 on 2011-11-11
Hi, disable it then when it is done complaining reenable unity and that setting.
Thank you

---

### Post by TimEnid on 2011-11-11
Did that as well. No go.

I disabled the plugin, the enabled it. typed in those two commands and still nothing. I think im goin to have to reinstall the OS. I wanted to avoid that.

---

### Post by TimEnid on 2011-11-11
i uninstalled compiz and anything else that was checked as green, in synaptic. and im trying to reinstall it and i get
> compiz:
 Depends: compiz-core but it is not going to be installed
 Depends: compiz-plugins-default but it is not going to be installed
 Depends: compiz-gnome but it is not going to be installed or
 	compiz-kde but it is not going to be installed
 Depends: compiz-plugins-main-default but it is not going to be installed
 Depends: libcompizconfig0 but it is not going to be installed

---

### Post by wildmanne39 on 2011-11-11
Hi, I think compiz was good to go as far as the command I gave you looked like it reinstalled correctly.

I was trying to post more directions a long time ago and my computer just locked up for some reason, so I have just now been able to get back to you, you can have a look at this link and if it does not work then I am out of idea's.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
There is good information all the way down to the bottom of that page.

Also
> unity --reset never stops putting out errors after about three minutes just reboot and you should be ok with that command.
Thank you

---

### Post by TimEnid on 2011-11-12
fixed it. i completely removed compiz by typing in
 sudo apt-get purge compiz-core
 i checked the synaptic and it showed it was gone. I reinstalled. Rebooted, no Unity. Logged into a terminal and installed Unity, now its back up working again. Thanks again to everyone for their time and patience.

---

### Post by wildmanne39 on 2011-11-12
Hi, I am glad it is working.
Enjoy

---

### Post by dundacil on 2011-11-15
Well, I have the same problem (in dash, no apps icon; if I click on Network Apps in dash nothing happens)

I tried all sorts of things, without success (including as suggested here, uninstall and reinstall)

My configuration is a brand new installation of oneiric, on a formatted disk; I only imported "data" files from my backup. Also, the machine was installed last week, and nothing happened (read: everything was working smoothly) until yesterday when, out of the blue, the problem developed. 

If I go to a guest session, I have the Apps icon in dash, and everything works fine: I am fairly confident, hence, that there is something wrong with some of my config files - but they were pristine last week, and they were sound until yesterday.

Finally I noticed that when I click on the Network Apps in dash I do get an error in .xsession-errors:
unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
and before you suggest it, I did purge and reinstall   unity-lens-applications unity-place-applications

Any wisdom the comunity can share will be most welcome

Riccardo

Edit: SOLVED! After some trials and errors, I hit the solution (for my case): basically, it appears that I had a corrupted .cache. After removing $HOME/.cache and log out/log in, dash was as it should be, with the apps icon etc.

---


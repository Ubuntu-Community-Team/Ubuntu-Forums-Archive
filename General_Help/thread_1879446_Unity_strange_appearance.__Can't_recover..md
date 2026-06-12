---
title: "Unity strange appearance.  Can't recover."
date: 2011-11-11
forum: General Help
---

### Post by Randy Schilling on 2011-11-11
Hell0 -

I recently installed Ubuntu 11.10 and had just gotten my Unity desktop
configured nicely when I did something inadvertent.  
I don't know what I did though.
My Unity desktop has taken on a strange appearance:

    No notification area.

   No access to launcher with mouse or start key. 

    A menu: File Edit View Go Benchmark Help, appears in the
   upper-left corner as if a program, not sure what program, 
   possibly Nautilus, had taken over my desktop, full screen. 

    Restarting does not return the desktop to normal.

    Gnome desktop is unaffected by what I did.

Shaky mouse behavior.


WHAT HAPPENED?  Please help so I can get back to work.


Thanks and regards - Randy

---

### Post by BillyBoa on 2011-11-11
Try to reset icons of Unity and from a terminal


```
unity --reset-icons
```

or reset Unity

```
unity --reset
```

I don't know if it's Compiz problem so do a

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by Frogs Hair on 2011-11-11
Restart with switch on the computer and boot into Ubuntu 2D found on the session  list in the log in window . Open the terminal and run  ```
unity --reset
```

Logout or restart and try to log into Ubuntu . This may or may not work , but you won't be able to get terminal access from the screen your now in .

---

### Post by Randy Schilling on 2011-11-11
Hello and thanks for looking into this.

Will unity --reset return everything to default settings?


I should have mentioned that I Compiz Configuration Manager was open
when this happened.  I was reading about configuring Unity but hadn't made any
changes, any INTENTIONAL changes.


Randy

---

### Post by BillyBoa on 2011-11-11
Check here

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by TimEnid on 2011-11-11
same problem im having here
[http://ubuntuforums.org/showthread.php?t=1871081](http://ubuntuforums.org/showthread.php?t=1871081)

---

### Post by BillyBoa on 2011-11-11
As I see from Tim's thread the problem lies to Compiz. Somehow Compiz loses plugins and it's impossible to reinstall them.

Just try again to purge and reinstall all Compiz plugins through Synaptic 

and use the command from the terminal to reset Compiz

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by TimEnid on 2011-11-11
> **BillyBoa said:**
> As I see from Tim's thread the problem lies to Compiz. Somehow Compiz loses plugins and it's impossible to reinstall them.

Just try again to purge and reinstall all Compiz plugins through Synaptic 

and use the command from the terminal to reset Compiz

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```
thats the thing, when i mark compiz and all related files for complete removal, they get removed, but then when i go to reinstall them (thru synaptic), i get an error message that something wasnt found, so it wont be installed. I am not home to copy the error, but i will post it when i can.

why does this even happen? It happend to me when i was trying to change the Mouse pointer.

---

### Post by Randy Schilling on 2011-11-11
Hello and thank for lookin in on this.

I tried the following two things - without success.
I'm writing this under my Gnome desktop.

From this desktop I opened a terminal and entered unity --reset.
The system responded but quickly stalled at the statement
    Setting Update "run_key"
I waited ten minutes and tried to close the terminal, got a message
that there's a process running in the terminal and closing the terminal
would kill that process.  I waited a lttile longer and then decide to 
close the terminal

Should I have waited longer?

Then I logged out of Gnome and came up again under Unity2d, 
hit alt+F2, started to enter unity --reset when the system presented
that command as an option.  I click it.  The system responded but,
unlike the previous, there was no scrolling list of stuff flowing by.
The response was instantaneous.  
I restarted into Unity but it remained sick.  Like I said before, its 
like a program has taken over the entire screen.

Did I mention that Compiz Settings Manager was open when this happened?

I don't know what else to tell you.

---

### Post by TimEnid on 2011-11-11
> **Randy Schilling said:**
> 
From this desktop I opened a terminal and entered unity --reset.
The system responded but quickly stalled at the statement
    Setting Update "run_key"
I waited ten minutes and tried to close the terminal, got a message
that there's a process running in the terminal and closing the terminal
would kill that process.  I waited a lttile longer and then decide to 
close the terminal

  this is the same thing im experiencing. I was able to get it working one time as you can see from the thread i created, but this second time seems to be something different.

---

### Post by BillyBoa on 2011-11-11
Another thing

Go to "CompizConfig Settings Manager" (if you don't have it just install it from Ubuntu Soft Center).

From there search for the "Ubuntu Unity Plugin" and if it is not checked, just check it.

---

### Post by BillyBoa on 2011-11-11
If nothing of the above is working then try the last one

go to /home directory and push CTRL+H to see the hidden folders
and change name to the folder /.gconf

Change the name to something like /.gconf1 and reboot the computer.

---

### Post by Randy Schilling on 2011-11-11
Let me catch up.  

1. purge  all Compiz plugins through Synaptic
2. reinstall all Compiz plugins through Synaptic
3. then enter two command at these two command at the terminal:
      > gconftool-2 --recursive-unset /apps/compiz-1
      > unity --reset

How do you identify compiz plugins in Synaptic?

---

### Post by BillyBoa on 2011-11-11
Better try the 2 last options I gave you.

[LIST]
[*]From CompizConfig look if Unity plugin is checked

[*]Or rename the .gconf folder
[/LIST]

---

### Post by Randy Schilling on 2011-11-11
What step does changing the name of .gconf  replace?

---

### Post by BillyBoa on 2011-11-11
As I explained on comment #12 this is the last solution. Better just take a look for the Unity plugin to be checked. If not check it and restart.

---

### Post by Randy Schilling on 2011-11-11
Billy -

I've changes the name of .gconf.
What next?

---

### Post by Randy Schilling on 2011-11-11
I changed the name of .gconf, restarted, but Unity remains.

---

### Post by BillyBoa on 2011-11-11
Restart to see if Unity appears

---

### Post by Randy Schilling on 2011-11-11
I'm back up in Gnome, trying my best to keep up?
What next?

---

### Post by BillyBoa on 2011-11-11
Ok now you have to check the Unity plugin.

Go to "CompizConfig Settings Manager" (if you don't have it just install it from Ubuntu Soft Center).

From there search for the "Ubuntu Unity Plugin" and if it is not checked, just check it.

---

### Post by Randy Schilling on 2011-11-11
I changed the name of the folder, that's all.
Then booted into Unity - it's still strange.
What else should I have done?

---

### Post by BillyBoa on 2011-11-11
You should ask on Compiz Settings for this

[IMG]http://ubuntuforums.org/picture.php?albumid=2448&pictureid=8289[IMG]

---

### Post by BillyBoa on 2011-11-11
Sorry look now

[IMG]http://ubuntuforums.org/picture.php?albumid=2448&pictureid=8289[/IMG]

---

### Post by Randy Schilling on 2011-11-11
Ok Billy,

Renamed .gconf, checked Ubuntu Utility Plugin in Compiz Setting Manager, and booted into Unity.   
It looks good.  

The only difference that I can see is that my launcher icons are back to their default size.
I had set them up to be smaller.  Don't worry about this.  I can fix this.

What next?

What about the renamed folder?  Leave it?

Do you know what I did to create this problem?  How to keep it from happening again?

---

### Post by BillyBoa on 2011-11-11
> **Randy Schilling said:**
> Ok Billy,

What next?

What about the renamed folder?  Leave it?

Do you know what I did to create this problem?  How to keep it from happening again?

About the renamed folder you can delete it now, it was renamed to fall back, just in case the tweak was not working.
About the problem created, it's a Compiz problem, because it's a sensitive program and if you do something extraordinary, it's collapsing.

Don't worry, now you now how to fix it.

---

### Post by Randy Schilling on 2011-11-11
Many thanks and warm regards to my friend from the middle of Spain.
Adios and vaya con dios

---

### Post by BillyBoa on 2011-11-11
Don't mention it.

Only please check thread SOLVED from the (almost) top right of the page Thread Tools.

Adios

---

### Post by TimEnid on 2011-11-11
i changed the name of the folder, checked the box, and restarted. nothing. btw, i am doing this from gnome classic, when i restart, i log in thru Ubuntu and thats where the issue is.

---

### Post by TimEnid on 2011-11-11
when i check the Ubuntu Unity Plugin box, i get "some key and edge bindings of Plugin Ubuntu Unity Plugin conflict with other plugins. Do you want to resolve the conflicts"

i check to resolve the conflicts and get:
The new value for the key binding for the action Key to execute a command in plugin Ubuntu Unity Plugin conflicts with the action Run Dialog of the Gnome Compatibility plugin.
Do you wish to disable Run Dialog in the Gnome Compatibility plugin?
options are; set key to execute a command; dont set key to execute command; disable run dialg

not sure where to go from here

---

### Post by TimEnid on 2011-11-11
> **BillyBoa said:**
> Try to reset icons of Unity and from a terminal


```
unity --reset-icons
```

or reset Unity

```
unity --reset
```

I don't know if it's Compiz problem so do a

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

tried this and got
```
tim@tim:~$ gconftool-2 --recursive-unset /apps/compiz-1
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
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2a00017
```

---

### Post by stinkeye on 2011-11-11
When you open a terminal and run...
```
gconftool-2 --recursive-unset /apps/compiz-1
```
you will set compiz back to default.
In this default state the **unity plugin is not enabled**.


Then when you run
```
unity --reset
```
you will reset profile parameters in compiz and restart the Unity shell with default settings but it **does not enable the unity plugin** if it is disabled.
So you still **need to enable the unity plugin**.

The easiest way to fix compiz is to log in to the **ubuntu 2d** session and
open ccsm > preferences
Hit the **reset to defaults** button
then click on the back button and
**Enable the unity plugin**
Choose to resolve conflicts if asked and click on the far right button as they pop up.

Log out and back into your **ubuntu** session.


Quite often when I'm changing settings in compiz it will not reload properly 
and can be fixed by running
```
compiz --replace
```
If this doesn't work then go the reset to defaults method.

When you have compiz set up how you want use
ccsm > preferences to export your profile.
It will ask you "Do you want to skip default option values while exporting your profile?".
It doesn't matter which you choose.
If you choose **not** to skip default option values it just makes for a bigger file.
I choose to skip default option values.

Then if something stuffs up you can use 
ccsm > preferences to import your saved profile.
If you can't work effectively in your current session do it in the 2d session.

---

### Post by TimEnid on 2011-11-12
^^^^^^^^i did all the above and no luck. Its a lost cause. a frustrating lost cause.

---

### Post by stinkeye on 2011-11-12
The only other way of know of is to remove all your compiz config files.
Run one at a time.
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*
```

---

### Post by TimEnid on 2011-11-12
> **stinkeye said:**
> The only other way of know of is to remove all your compiz config files.
Run one at a time.
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*
```

and then reinstall? thru synaptic?

---

### Post by TimEnid on 2011-11-12
> **stinkeye said:**
> The only other way of know of is to remove all your compiz config files.
Run one at a time.
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*
```

i did this, and when i go to synaptic, its still installed. I right click and i see options for complete removal, reinstall and removal. Should i have an option to just "install" since i just put in those commands to remove it?

---

### Post by stinkeye on 2011-11-12
Those commands aren't to remove compiz.
They are to remove the configuration files in your home folder.
No need to uninstall this, reinstall that.

Another way to test if the config files are at fault is to 
create a new user and log into that account.

---

### Post by TimEnid on 2011-11-12
> **stinkeye said:**
> Those commands aren't to remove compiz.
They are to remove the configuration files in your home folder.
No need to uninstall this, reinstall that.

Another way to test if the config files are at fault is to 
create a new user and log into that account.

created a new user, issue is still there.

btw, thanks everyone for the help with this

---

### Post by stinkeye on 2011-11-12
> **TimEnid said:**
> created a new user, issue is still there.

btw, thanks everyone for the help with this
If your in a new account,in an ubuntu session, the proprietary gfx driver is activated and the unity plugin is enabled, and you said you had compiz running before, I really have no other answers.

With the uninstalling and reinstalling of compiz just make sure you still have **unity** installed
as this is removed when you uninstall compiz.

---

### Post by TimEnid on 2011-11-12
> **stinkeye said:**
> If your in a new account,in an ubuntu session, the proprietary gfx driver is activated and the unity plugin is enabled, and you said you had compiz running before, I really have no other answers.

With the uninstalling and reinstalling of compiz just make sure you still have **unity** installed
as this is removed when you uninstall compiz.

and how would i activate the proprietary driver. when im logged into Ubuntu under either account, all i can access is my folders and a terminal. I went and logged in to Gnome, and i dont see a way to access the Hardware Drivers.

---

### Post by stinkeye on 2011-11-12
So unity is still installed?

Probably easier to log into the ubuntu 2d session
and start typing "driver" in the dash.

What is your output for...
```
lspci -k | grep -A3 VGA
```

---

### Post by TimEnid on 2011-11-12
fixed it. i completely removed compiz by typing in
sudo apt-get purge compiz-core
i checked the synaptic and it showed it was gone. I reinstalled. Rebooted, no Unity. Logged into a terminal and installed Unity, now its back up working again. Thanks again to everyone for their time and patience.

---

### Post by stinkeye on 2011-11-12
> **TimEnid said:**
> fixed it. i completely removed compiz by typing in
sudo apt-get purge compiz-core
i checked the synaptic and it showed it was gone. I reinstalled. Rebooted, no Unity. Logged into a terminal and installed Unity, now its back up working again. Thanks again to everyone for their time and patience.

Yeah it does help to have unity installed. Bye bye. 
:rolleyes:=D>

---

### Post by Ruud.developer on 2011-11-13
edit: I was wrong below, my problem is not fixed. See my next post.

Some notes for people like me who are new to Linux and Ubuntu.

I had this problem and found that I could still start a terminal using CTRL+ALT+T. Using that I started firefox to read from this thread.
```
firefox
```Nautilus was also running in my case, so on the top of the screen use File->New window to see a Nautilus window so you can rename the /home/.gconf

Starting the "CompizConfig Settings Manager" can also be done from the terminal:
```
ccsm
```I also had to run these two commands though I unsure if I did both of them together and if either went before the ccsm
```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```In my case using Ubuntu 2d did not solve the problem, the normal version was still messed up. Using the above I was able to run it from the normal version.

---

### Post by Ruud.developer on 2011-11-13
My problem is not gone although below I thought it had. I also  tried removing compiz, reinstall and when I restarted only ubuntu2d was  available. So I figured out that's because Unity was not installed from  the posts in this thread. After reinstalling unity (sudo apt-get install  unity) I got back Ubuntu, but the problem remains.

When logged into Ubuntu I can start Unity from a terminal running unity  --reset. This start unity as it should until I close the terminal. "Luckily" unity outputs a whole lot when resetting. Perhaps that is of help? See below.

```
unity --reset
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:3094): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3094): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3094): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3094): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
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
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done

Screen geometry changed:
   0x0x1024x768

unity-panel-service: no process found
Initializing unityshell options...done
DEBUG 2011-11-13 13:17:19 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1024 h=768
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing debugspew options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "run_command_terminal_key"

(firefox:3179): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:3179): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:3179): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:3179): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
WARN  2011-11-13 13:17:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method InfoRequest proxy /com/canonical/unity/lens/music  does not exist
WARN  2011-11-13 13:17:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method SetActive proxy /com/canonical/unity/lens/music does  not exist
WARN  2011-11-13 13:17:28 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method InfoRequest proxy /com/canonical/unity/lens/files  does not exist
WARN  2011-11-13 13:17:28 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method SetActive proxy /com/canonical/unity/lens/files does  not exist
compiz (core) - Warn: unhandled ConfigureNotify on 0x120022e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2011-11-13 13:17:46 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method InfoRequest proxy  /com/canonical/unity/lens/applications does not exist
WARN  2011-11-13 13:17:46 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method SetActive proxy  /com/canonical/unity/lens/applications does not exist
WARN  2011-11-13 13:17:46 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands  does not exist
WARN  2011-11-13 13:17:46 unity.glib.dbusproxy GLibDBusProxy.cpp:255  Cannot call method SetActive proxy /com/canonical/unity/lens/commands  does not exist
WARN  2011-11-13 13:17:46 unity.iconloader IconLoader.cpp:509 Unable to  load contents of  file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg:  Error opening file: No such file or directory
WARN  2011-11-13 13:17:46 unity.iconloader IconLoader.cpp:509 Unable to  load contents of  file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg:  Error opening file: No such file or directory

```

edit:
I have some additional problems that may help pointing me in the right direction (I've tried every hint from every post in this thread and also tried other combinations of the commands that seemed to make any sense)

When I now start unity and I click shutdown, the computer does not shutdown, instead the user is logged out and the login screen appears again. Even when clicking shutdown there then the pc does not shutdown. But sudo shutdown -h now DOES, so a rights issue might be the problem here. And my user is registered as an Administrator, but I am no longer allowed to unlock the users screen to edit or add new users...

I'm at the point of a complete reinstall as I have only worked with Linux for 3 days now, of which one day was filled with problems that do not belong in such a distribution. I can reinstall everything within one day, so I would have been done had I started this morning.

---


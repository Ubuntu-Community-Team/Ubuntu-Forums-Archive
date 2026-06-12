---
title: "Unable to get Unity Panels in 11.10, only in GnomeClassic"
date: 2012-01-18
forum: General Help
---

### Post by bogan on 2012-01-18
I am running ubuntu 11.10 and 10.04 LTS in a Triple boot installation in two computers, one with Win7, the other with Win Vista. The first has Gnome3 installed, the later was an upgrade and I did not install either Gnome3 nor gnome-fallback.

In 10.04 and in 11.10 when logged in to Gnome Classic, on both m/c's, I have Panels working as well as Ubuntu 2D Launcher in  the later.

But when I log in to Ubuntu [ Unity ] I get no panels at all, only the Unity Launchpad - if that is what it is called - on the left. It contains exactly the same Launchers as I set up under gnome classic, except they are smaller, as changing their size in MyUnity, had no effect in Classic.

How can I get Panels to work in Unity.?
 In the Unity Man it says there must be at least one Panel; but as there is not, I cannot right-Click and add one. 
I have activated all the Unity Plug-ins and this is what shows: ```
alan@alan-MS-7616:~$ ps ax | grep unity
 2109 ?        S      0:01 /usr/bin/unity-window-decorator
 2114 ?        Sl     0:03 /usr/lib/unity/unity-panel-service
 2177 ?        Sl     0:00 /usr/lib/unity-lens-applications/unity-applications-daemon
 2179 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 2181 ?        Sl     0:00 /usr/lib/unity-lens-files/unity-files-daemon
 2212 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
 2827 pts/1    S+     0:00 grep --color=auto unity
alan@alan-MS-7616:~$ 
```In the top bar, or in the Launchpad, Right-Click+ Alt or R-C+Super+Alt have no effect.

I have seen mentions of Unity Panels and just saw a Thumbnail that clearly showed icons arranged along the top panel, so I know it can be done.

Hopefully,  ** bogan**.
                               :confused:

---

### Post by cariboo on 2012-01-18
Did you try:

```
unity --reset
```

---

### Post by bogan on 2012-01-19
Hi!,** cariboo907**,
You Posted> Did you try:```
 unity --reset
``` I had not, but I have now result:  DISASTER!!

Everything froze up when I closed the hung terminal and I had to power off to shut down.
 I am posting this unedited from another Win7 m/c.
```
19/01/12 Ubuntu 11.10  Win7 m/c. THIS IS WHAT I GOT FROM ENTERING:

root@alan-MS-7616:/home/alan# unity --reset
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Processing upgrade com.canonical.unity.unity.01.upgrade
profile: unity
number: 1
domain: com.canonical.unity
Initializing commands options...done
Initializing compiztoolbox options...done
Initializing fade options...done
Initializing zoom options...done
Initializing detection options...done
Initializing opacify options...done
Initializing obs options...done
Initializing clone options...done
Initializing cube options...done
Initializing decor options...done
Initializing move options...done
Initializing scale options...done
Initializing wall options...done
Initializing unityshell options...done
Initializing rotate options...done
Initializing gnomecompat options...done
Initializing screenshot options...done
Initializing text options...done
Initializing resize options...done
Initializing place options...done
Initializing ezoom options...done
Initializing neg options...done
Initializing put options...done
Initializing copytex options...done
Initializing regex options...done
Initializing shift options...done
Initializing scaleaddon options...done
Initializing inotify options...done
Initializing dbus options...done
Initializing imgsvg options...done
Initializing blur options...done
Initializing gtkloader options...done
Initializing composite options...done
Initializing annotate options...done
Initializing expo options...done
Initializing water options...done
Initializing kdecompat options...done
Initializing core options...done
Initializing imgjpeg options...done
Initializing snap options...done
Initializing debugspew options...done
Initializing bailer options...done
Initializing ring options...done
Initializing workarounds options...done
Initializing opengl options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing unitymtgrabhandles options...done
Initializing resizeinfo options...done
Initializing staticswitcher options...done
Initializing colorfilter options...done
Initializing grid options...done
Initializing imgpng options...done
Initializing animation options...done
Initializing session options...done
Initializing winrules options...done
Initializing switcher options...done
Initializing mag options...done
Initializing thumbnail options...done
Initializing wobbly options...done
Removed 0 items from active_plugins
Overriding value alt_tab_timeout
Completed upgrade com.canonical.unity.unity.01.upgrade
Processing upgrade com.canonical.unity.unity.02.upgrade
profile: unity
number: 2
domain: com.canonical.unity
Overriding value x_offset
Overriding value y_offset
Overriding value distance
Overriding value vp_distance
Overriding value vp_brightness
Overriding value vp_saturation
Overriding value reflection
Completed upgrade com.canonical.unity.unity.02.upgrade
compiz (expo) - Warn: failed to bind image to texture

(compiz:2275): GLib-WARNING **: In call to g_spawn_sync(), exit status of a child process was requested but SIGCHLD action was set to SIG_IGN and ECHILD was received by waitpid(), so exit status can't be returned. This is a bug in the program calling g_spawn_sync(); either don't request the exit status, or don't set the SIGCHLD action.

** (compiz:2275): WARNING **: Abnormal program termination when spawning command line `dbus-launch --autolaunch=840150fa426bcbe2b4ce18bb0000000c --binary-syntax --close-stderr': 

(compiz:2275): GLib-WARNING **: In call to g_spawn_sync(), exit status of a child process was requested but SIGCHLD action was set to SIG_IGN and ECHILD was received by waitpid(), so exit status can't be returned. This is a bug in the program calling g_spawn_sync(); either don't request the exit status, or don't set the SIGCHLD action.

** (compiz:2275): WARNING **: Abnormal program termination when spawning command line `dbus-launch --autolaunch=840150fa426bcbe2b4ce18bb0000000c --binary-syntax --close-stderr': 
WARN  2012-01-19 07:40:40 glib.glib-gobject <unknown>:0 invalid (NULL) pointer instance

Screen geometry changed:
   0x0x1280x1024

unity-panel-service: no process found
DEBUG 2012-01-19 07:40:41 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1280 h=1024
WARN  2012-01-19 07:40:42 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
WARN  2012-01-19 07:40:42 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window20971524: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-01-19 07:40:42 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application1559344916: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-01-19 07:40:42 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window20971524: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-01-19 07:40:42 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application1559344916: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "main_menu_key"
Setting Update "run_command_terminal_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e000db
.....
   [COLOR=DarkGreen] At this point it hung with a still cursor for 60 secs[/COLOR].:
.....
WARN  2012-01-19 07:41:41 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-01-19 07:41:41 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
.....
    [COLOR=DarkGreen]Repeats:[/COLOR]
.....
WARN  2012-01-19 07:41:41 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-01-19 07:41:42 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2012-01-19 07:41:42 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
....
 _
[COLOR=Red]|_| [/COLOR][COLOR=DarkGreen]At this point it hung again with a still cursor -- [/COLOR]
....
WARN  2012-01-19 07:47:06 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
....
 _
[COLOR=Red]|_|[/COLOR] [COLOR=DarkGreen]At this point it hung again with a still cursor -- [/COLOR]
....
[COLOR=Blue]    I then opened gedit from a GUI Launcher and copied the above text to save it.
 I then noticed the last line had been added at 07:47, and the following line as well:[/COLOR]
....
(gedit:2527): Gtk-WARNING **: Unable to retrieve the file info for `file:///home/alan/Documents/UnityPanels19.01.1': Error stating file '/home/alan/Documents/UnityPanels19.01.1': No such file or directory
....
 _
[COLOR=Red]|_| [/COLOR][COLOR=DarkGreen]At this point it hung again with a still cursor -- and then repeated the 'children line': [/COLOR]
....
  WARN  2012-01-19 08:02:03 glib <unknown>:0 Unable to fetch children: Method "Children" with signature ""
on interface "org.ayatana.bamf.view" doesn't exist  
```I have no idea what it all signifies. Have you??    :(

Edit: 14:30.
Note: Warn line:>   Failed to fetch view type at /org/ayatana/bamf/application1559344916: Nautilus does not show a /org/ folder; should there be one ?? 

Initially, at least, after a 'Cold Finger Reboot', logging in to Gnome Classic, everything seems to be as before.
Logging to Ubuntu also appears to be unchanged.
 Still no signs of a Panel. Launchers back to my old settings. [ They reverted to the defaults during the hiatus.
 'ps ax | grep unity' output also the same.
Chao!, **bogan**.

---

### Post by bogan on 2012-01-21
Hi! all you** Unity **believers,

Can someone tell me if there are supposed to be Panels in 11.10 Ubuntu, when logged in to 'Ubuntu', as there are when logged in to 'Gnome Classic'?

That is Panels that it is possible to create, move and adjust, not the Unity Launchpad, which I see referred to as a Panel, but is quite different and not adjustable in the same way.

I have "MyUnity" but the only option it gives for Panels is to set their transparency.

Are Panels actually part of Unity, or are they part of Gnome?

If they should be available, will some kind expert please tell me how to activate them.

Chao! & Thanks in advance,** bogan**,

:confused:

---

### Post by bogan on 2012-01-24
Hi!*** All Who ReaD tHIS***,

WOW! I do not believe this!!

Three Days and more than 150 visits to this thread and only one response.

Does no one know whether it is possible to get configurable Panels when logged in to Ubuntu [Unity] using 11.10,  3.0.0-15. ??

Even with the Launcher Icons reduced to the minimum there is only room for 18 in the Unity Launchpad with out scrolling - or "Task Management Area" as Unity manual calls it!! and 'Icons' are: "Application Indicators"!!

I have Avant Window Navigator [AWN] and so far that is the only way I have found to work, but it is not as friendly as Gnome Panels are.

Hopefully, **bogan**.

---

### Post by apochry on 2012-01-24
I do not think, that panels can be added to Unity. Why don't you simply use Gnome Classic if you don't like Unity?

---

### Post by bogan on 2012-01-24
Hi!, **apochry,**

Thanks for your response,
You Posted:> I do not think, that panels can be added to Unity. Why don't you simply use Gnome Classic if you don't like Unity?  It is not that I do not like Unity, and I **do** use Gnome Classic for the lack of functionality in Unity.

It is that according to the Forum gossip we are going to loose Gnome Classic, in a month or so, when 12.04 comes out, so I want to be prepared.

I have 10.04 and 11.10 Classic set up with three Panels, each grouping Launchers for specific activities: System, Graphics and Internet/Office; so I don't have to search through Dash or scroll the Unity LaunchPad.

I would like to setup Unity to do the same, but as you suggest, I begin to think too that it cannot be done, except by installing other Dock programs.

What surprises me is that I can't find any threads to suggest other people want the same. Those who do seem to have migrated to Gnome Shell or Mint.

Chao! **bogan**.

---

### Post by apochry on 2012-01-25
Hello Bogan,

I am not aware of those forum gossips about loosing GnomeClassic, but it won't surprise me too much.

Have you tried the "Gnome Pie" launcher. It's pretty functional, also very slick. You can use only him for launching apps and leave the whole space in the Unity launcher for the running apps's icons (for switching between windows, workspaces, etc.).  -> [http://www.omgubuntu.co.uk/2012/01/new-gnome-pie-release/](http://www.omgubuntu.co.uk/2012/01/new-gnome-pie-release/)

Regards,
Christo

---

### Post by bogan on 2012-01-26
Hi!,** apochry,**

Thanks for your suggestion,
You Posted:> Have you tried the "Gnome Pie" launcher. It's pretty functional, also very slick.  I had not stumbled across it, as I was concentrating on trying to get Unity to run how suited me, without adding lots of outsiders.

But I guess that is a lost cause.

Certainly, Gnome Pie is Slick, even Pretty, and it preserves the Clean Desktop ideal.

But it is a bit cronky, it keeps opening full-screen  Banshee Windows or Thunderbird Windows with no control buttons - they are hidden by its own name -  without my having done anything to select them, just closing Gnome Pie's Window triggers it.

I also found it quite difficult to set up as I wanted. The 'Man' page is a bit opaque.

Nonetheless I will give it a try. At least it works equally with Ubuntu [Unity] or Gnome Classic log-ins.

Chao!, **bogan**.

---


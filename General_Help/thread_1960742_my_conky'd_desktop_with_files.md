---
title: "my conky'd desktop with files"
date: 2012-04-18
forum: General Help
---

### Post by HiImTye on 2012-04-18
note: I'm completely rewriting these scripts to be more easily configurable

[SIZE=2]posting my conky setup with config files.
[ATTACH]216493[/ATTACH]


[SIZE=3][COLOR=DarkGreen]About[/COLOR][/SIZE]
[/SIZE][SIZE=2] included are conky configs that display:[/SIZE]
[LIST]
[*][SIZE=2]time/date[/SIZE]
[*][SIZE=2]whether updates are available and how many[/SIZE]
[*][SIZE=2]if the system needs to reboot[/SIZE]
[*][SIZE=2]the kernel currently in use[/SIZE]
[*][SIZE=2]the system's uptime[/SIZE]
[*][SIZE=2]GPU temperature (for nVidia adapters using proprietary drivers, if not, see below)[/SIZE]
[*][SIZE=2]a list of the processes using the most CPU (in reverse order)[/SIZE]
[*][SIZE=2]CPU Frequency[/SIZE]
[*][SIZE=2]system load[/SIZE]
[*][SIZE=2]graphs for each processor and both combined (you will need to add more if you have more than 2 cores)[/SIZE]
[*][SIZE=2]file system and memory usage (RAM&Swap)[/SIZE]
[*][SIZE=2]a list of processes using the most memory (in reverse order)[/SIZE]
[*][SIZE=2]disk IO. (if you use a file structure other than: base file system at '/' and storage at '/storage/' then see below)[/SIZE]
[*][SIZE=2]network usage[/SIZE]
[*][SIZE=2]connection lists, up and down (up to 11 connections each)[/SIZE]
[*][SIZE=2]MPD monitor + album art (see below)[/SIZE]
[*][SIZE=2]Deluge monitor (see below)[/SIZE]
[/LIST]
[SIZE=2][COLOR=Red][COLOR=DarkGreen][SIZE=3]Instructions[/SIZE]
**General**
[/COLOR] [/COLOR][/SIZE][SIZE=2]uncompress them into:
```
$HOME/Launchers
```**[COLOR=DarkGreen]Desktop Resolutions[/COLOR]**
I have included dynamic settings for both 1920×1080 and 1360×768. if you want to add more or edit them, the instructions are located inside:
```
$HOME/tconk.sh
```**[COLOR=DarkGreen]Non-nVidia GPUs or nVidia GPUs without the proprietary driver[/COLOR]**
if you don't use an nVidia GPU + the proprietary drivers then delete this line in .conkyrc-cpu:
```
${color2}GPU:${color3} ${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | grep -o '[0-9]\{2,3\}'}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C
```**[COLOR=DarkGreen]File System[/COLOR]**
if you have a file structure that differs from mine then you will need to edit .conkyrc-memory modifying or removing anything with:
```
/storage
```and/or adding your own mount points to it
**[COLOR=DarkGreen]Music Player Daemon[/COLOR]**
in order for MPD's conky display to display album art, you will need both:
[/SIZE] 
[LIST=1]
[*][SIZE=2]to put a picture in:```
$HOME/Launchers/.conkyrc-mpdPlaceholder.png
```(I have one included)[/SIZE]
[*][SIZE=2]to have your music separated by album and the album art for that album inside the album's folder (folder structure doesn't matter, so long as the album art is inside the album's folder)[/SIZE]
[/LIST]
[SIZE=2]**[COLOR=DarkGreen]Deluge Daemon[/COLOR]**
in order for Deluge to properly display you will need to install [conkyDeluge]("http://ubuntuforums.org/attachment.php?attachmentid=119519&d=1246404300") and replace:
```
/usr/share/conkydeluge/conkyDeluge.py
```with [this file]("https://raw.github.com/cas--/conkyDeluge/master/conkyDeluge.py") (right click and save link as)

[SIZE=3][COLOR=DarkGreen]Advanced Usage[/COLOR][/SIZE]
if you have a script located at:
```
$HOME/Launchers/.startupTasks.sh
```then tconk.sh (the main script) will launch it, and then move on. this is useful to me as I run PulseAudio not as a daemon (for running games with ALSA) and conky is the first thing I run when I resize my desktop (to load the conky settings for that resolution). this script replaces my .asoundrc (from my ALSA+Dmix settings to my PulseAudio settings) and restarts the PulseAudio server, without me having to manually run a variety of different scripts. I have included mine to give you an idea of how such a script could be set up and also the bash scripts and .asoundrc configuration files that it uses. just place these in ```
$HOME/Launchers/
```along with the rest of the files
if you pass a variable to tconk.sh then it will add a delay before it runs (giving time for the window manager to load, for instance). the variable doesn't matter, I just use:
```
$HOME/Launchers/tconk.sh 1
```and it does the trick for me
[/SIZE] [SIZE=2]
[SIZE=3][COLOR=DarkGreen]Customization[/COLOR][/SIZE]
if you do need to modify the files for whatever reason, I have them laid out to be as easy as possible to modify (except the actual conky configs, as anything after 'TEXT' displays on screen, making notation impossible)
[/SIZE][SIZE=2] 
[/SIZE]  [SIZE=3][COLOR=DarkGreen]Summary of files[/COLOR][/SIZE][SIZE=2]
each bash script is notated to allow for easy configuration/modification

inside conkyConfig.tar.gz:
[/SIZE]  
[LIST]
[*][SIZE=2] tconk.sh: bash script to launch various conky scripts (among other things) as well as controlling the position of the conky windows[/SIZE]
[*][SIZE=2] .conkyrc-cpu: conky config displaying CPU usage, and some other things[/SIZE]
[*][SIZE=2] .conkyrc-deluge: conky config displaying deluge's status[/SIZE]
[*][SIZE=2] .conkyrc-deluge.template: template file for controlling how conkyDeluge is formatted[/SIZE]
[*][SIZE=2] .conkyrc-memory: display of RAM/Swap/HDD usage, among other things[/SIZE]
[*][SIZE=2] .conkyrc-mpd: currently playing song in MPD + cover art + progress bar[/SIZE]
[*][SIZE=2] .conkyrc-mpd.sh: bash script to control displaying album art used by .conkyrc-mpd[/SIZE]
[*][SIZE=2] .conkyrc-mpdPlaceholder.png: placeholder picture for when no album art exists[/SIZE]
[*][SIZE=2] .conkyrc-netdown: open outbound IPs+Ports, download speed, etc[/SIZE]
[*][SIZE=2] .conkyrc-netup: same as .conkyrc-netdown but for inbound[/SIZE]
[*][SIZE=2] .conkyrc-restart.sh: bash script for .conkyrc-time to display when the system needs to be restarted due to an update[/SIZE]
[*][SIZE=2] .conkyrc-time: displays system time+date, whether a reboot is required and whether updates are available[/SIZE]
[*][SIZE=2] .conkyrc-updates.sh: a bash script to determine whether there are any updates, and if so, how many[/SIZE]
[/LIST]
[SIZE=2]inside startupTasks.tar.gz:
[/SIZE]
[LIST]
[*][SIZE=2] .startupTasks.sh: a bash script in charge of performing system tasks not related to conky[/SIZE]
[*][SIZE=2] .[/SIZE][SIZE=2]startupTasks-[/SIZE][SIZE=2]gnomeShell.sh: a loop to check if Gnome-Shell is running and start it if it isn't (in case it crashes for what ever reason)[/SIZE]
[*][SIZE=2].[/SIZE][SIZE=2]startupTasks-soundSystem[/SIZE][SIZE=2].sh: bash script to load or unload PulseAudio and swap .asoundrc configuration files
[/SIZE]
[*][SIZE=2].startupTasks-soundSystem-alsadmix[/SIZE][SIZE=2]: .asoundrc for sound mixing using ALSA without PulseAudio
[/SIZE]
[*][SIZE=2].startupTasks-soundSystem-alsapulse: .asoundrc for redirecting bad programs (such as Flash) to PulseAudio
[/SIZE]
[*][SIZE=2].startupTasks-soundSystem-osspulse: .asoundrc for using PulseAudio with OSS[/SIZE]
[/LIST]
  [SIZE=2]
[/SIZE] [SIZE=3][COLOR=DarkGreen] Updates[/COLOR][/SIZE][SIZE=1]
-various formatting changes and fixed a typing issue that made the mpd script always force the album to 'empty'
-change 'Placeholder.png' to '.conkyrc-mpdPlaceholder.png' to maintain conformity (and reduce clutter when not showing hidden files)
-added summary of files
-added support for multiple resolutions, loaded at run time and added resolution settings for  both 1920×1080 and 1360×768
-moved non-conky related tasks into a separate bash script, and now we skip it if it doesn't exist
-fixed some typing errors in the .startupTasks files
-edited tconk.sh to make it more clear how to add settings for a new display resolution
[/SIZE]

---


---
title: "Serious problem with graphical interface"
date: 2011-07-23
forum: General Help
---

### Post by sandman887 on 2011-07-23
First of all, I'm using Ubuntu 10.04 LTS. I couldn't correctly choose the correct version of Ubuntu because of this GUI problem. 

I started typing different values into System>Preferences>Startup Applications>Login sound because I wanted to change the login sound, and there was no easy way to do it, because they must have thought it was a good idea to make it more difficult. 

So anyway, I clicked edit on the login sound. I tried changing the "--id="desktop-login" to "$HOME/Music/mgssounds/gameover.ogg", and this didn't work. It just made no sound whatsoever. I had checked some forums, and this is what everyone said to do, because it worked. Well it didn't. So I deleted "--id="blah blah blah" and replaced it with "-f /$HOME/Music/mgssounds/gameover.ogg" that's right, with no quotes of any sort around the pathname after "-f". I would use the code button, but it doesn't work because of this GUI problem. 

So anyway, I log out and log back in, and no sound again. Then I see my system monitor indicator, and it shows blue all the way to the top, indicating that the CPU is maxed out. I have a Pentium D @ 2.6 GHz. So it's dual core. I checked "top -d 1", and it showed bonobo-activation-server was maxing out the CPU. So I did "killall bonobo-activation-server", and the CPU monitor went back down to normal levels. I logged out again, and logged back in, and the same thing happened. I had made a launcher on my panel to "gnome-session-properties", which shows the startup applications, and now when I click on it, it shows the titlebar, but the rest of the window is white, and unresponsive. The blue CPU meter is halfway used, indicating that one of the CPUs are maxed out. 

Even right now in Firefox, it's running funny. When I click on things, or try to select things with the mouse, it's like it's not even responding to the events. Also, the gray areas above the webpage window (like the menu, and all the toolbars, and even the tabs, and the status bar) are invisible, showing the gnome-terminal behind the browser window. 

When I log out, and back in, it doesn't fix it. Something is still messed up. I did "vlc $HOME/Music/mgssounds/gameover.ogg", and it plays it fine, so the file isn't corrupt. This stuff didn't happen until I started messing with the options for canberra-gtk-play. 

I tried the command: canberra-gtk-play -f $HOME/Music/mgssounds/gameover.ogg, and this is the error message I get: "Failed to play sound: File or data corrupt"

So my guess is that I possibly messed up some gtk file. I tried searching all the hidden directories and files in my home folder, but I can't figure out where this configuration file is that I need to fix. I can barely use this interface like this. 

Strangely enough, bash seems to work fine, except that when I use the history command, it doesn't show any commands that have been hidden when it has scrolled down. It only shows a window's worth of commands, even though they are numbered in the 500's. I wonder if this is because the screen is not refreshing anything above where the top line is in the terminal window. I just tried scrolling up in the terminal, and my suspicion has been confirmed, that the screen is not updating or refreshing. 

I suspect that gtk has been messed up, but maybe it's something else. 

I really can't use my computer at all like this. Thanks in advance!

System info: 
Pentium D (dual core) 2.6 GHz
2 GB RAM
Ubuntu 10.04
shredder@technodrome:~/Music/mgssounds$ uname -a
Linux technodrome 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

If anybody needs any more info, let me know, and I will provide it. Thanks!

---

### Post by sandman887 on 2011-07-23
OMG...Who knew how big of a problem editing that was! I rebooted, and after the Ubuntu splash screen came up, it said the /tmp partition or something was corrupt, or couldn't be read or something, so I hit a button to retry it...I can't remember now, it took so long to change to the next screen. 

BEFORE I rebooted, I viewed $HOME/.xsession-errors to look for clues as to what was going wrong. I then saw something wrong with ~/.config/somefile so I went there, because the profile name was "". This was giving an error early on in the .xsession-errors file. So I set it to ha instead of "". I thought it would be a good idea to name it something that I knew it really wouldn't be, because I didn't want to overwrite a real profile name when I saved the file. 

I also went into ~/.config/autostart/libcanberra-login-sound.desktop, and changed 
```

[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play -f /home/shredder/Music/mgssounds/gameover.ogg --description="GNOME Login"
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/sound/event_sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound

```

to 

```

[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/sound/event_sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound

```

Like I said, I did this before the reboot. After the reboot, it couldn't even finish booting up. It said errors booting the / partition, so it booted into a maintenance shell, with root@technodrome #. It said /home/shredder didn't exist, which freaked me out, thinking it had wiped out my entire home directory. So I did

```
df
```

and it showed the various partitions. It still showed that /home had 12% disk usage on the partition, which was a good sign, because it showed that the files were most likely still there. However, when I tried to cd to /home and did ls -slph, it showed nothing in there, even when I then tried it with the -a option. 

At this point, I was freaked. It said to hit Ctrl-D to finish trying to boot up, so I did, and it went to the graphical login screen. I was partially relieved, although I knew that I had not yet tried to log in. I logged in, and the login was successful, which showed that at least those system files were still intact, although it gave numerous errors because my home directory hadn't been found.

I still hadn't given up hope, because df showed that the /home partition was still containing a good amount of files. I was stuck, though, because I couldn't log out. Hitting Ctrl+Alt+Del just brought up the Shutdown/Restart/Suspend menu. So I thought what the hell, and restarted, hoping it would somehow come back to normal. 

And after the restart, after putting my hand over my eyes, not wanting to see another error message about the partitions, I finally peeked through, right when I heard the drums sound when the login screen comes up. It had booted up without any errors this time. I started getting excited, and hope had creeped into me that it might work this time. So I logged in, and it logged me in, with the normal tribal tune, or whatever it was (ie., /usr/share/sounds/ubuntu/stereo/desktop-login.ogg), and my desktop came up normally. 

After all this, I was so relieved. I definitely felt that I had gotten lucky. So anyway, BE VERY AWARE, EVERYONE, that editing your Gnome Login Sound in System > Preferences > Startup Applications can lead to serious, possibly irreparable problems unless you have a very good grasp on Linux and the system in general. 

I hope the Ubuntu team takes this into consideration, and puts an easy option to change the login sound again into the preferences. This will prevent problems like this from happening again.

---

### Post by sandman887 on 2011-07-23
I'm uploading my .xsession-errors file so you can look at it.

---


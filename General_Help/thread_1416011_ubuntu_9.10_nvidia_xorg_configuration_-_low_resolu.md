---
title: "ubuntu 9.10 nvidia xorg configuration - low resolution"
date: 2010-02-25
forum: General Help
---

### Post by johto on 2010-02-25
Installed fresh Ubuntu 9.10. Got a 21" CRT capable of running 1600x1200@85Hz. I have Nvidia 6600GT. Have used this configuration with differend linux distros just fine in the past years. This time this newest ubuntu gave me WTF!!!!

After installing the Nvidia drivers, my resolution is locked at 640x480.
Pff, yeah next you guys will say: "Just edit your xorg.conf and fix the resolutions etc..." ...PFF!! I checked the /etc/X11/xorg.conf what did i find? ITS <snip> empty :I

...next, "aaah, lets run the good old command: 'dpkg-reconfigure xserver-xorg' to populate the fckup default one! 

NOPE! This command seems to be out of date, and been removed. WTF AGAIN?


WTF guys? I cant believe it! I'v been using linux'es like 20 years. I have been using last 2 years purely OS X, and wanted to check how linux was doing(surely the development has went further?) ..Seems to me that its gone BACKWARD! 

Its 2010 for crist sake...maybe i'v been spoiled with my Mac, but somehow i'm no longer interested to tweak these systems just for tweaking?

...ok, i'v been trying to google latest ubuntu 9.10 + nvidia + low resolution + xorg with this raped desktop im running(640x480...nice browsing experience...well could be even worse, command line with linx)...pfff. Too pissed off to type more, gotta go smoke some cigs and continue with my 24" iMac <3

Please feel free to add someting important or not so important about the topic.

---

### Post by dardack on 2010-02-25
I've installed nvidia drivers direct fron Nvidia (beta even) many times on many systems and never had an issue.  I just say yes when it wants to update my xorg.conf file.  Than use nvidia-settings command to change any resolution/etc i want.

But side note, if you coming in with that attitude many people are less inclined to give help.  Stick with OsX for all I care.

---

### Post by maghoxfr on 2010-02-27
Hi, I hope someone can help me with this problem because it's been a while and I'm unable to solve it. I tried many things (which I don't fully understand, I'm a new user). I can switch the resolution to the one I want (1024x768 ) on Xserver but it doesn't let me save it so when I restart session I'm back to the older one. I read this link on another post but don't really know what to do. (it's on the third item i think). I have a nvidia 8400 gs and the current driver I have is the 185. Thank you

[http://linux.die.net/man/1/nvidia-settings]("http://linux.die.net/man/1/nvidia-settings")

---

### Post by pbrane on 2010-02-27
> **maghoxfr said:**
> Hi, I hope someone can help me with this problem because it's been a while and I'm unable to solve it. I tried many things (which I don't fully understand, I'm a new user). I can switch the resolution to the one I want (1024x768 ) on Xserver but it doesn't let me save it so when I restart session I'm back to the older one. I read this link on another post but don't really know what to do. (it's on the third item i think). I have a nvidia 8400 gs and the current driver I have is the 185. Thank you

[http://linux.die.net/man/1/nvidia-settings]("http://linux.die.net/man/1/nvidia-settings")

Set the resolution ( and any other settings ) using **nvidia-settings**. You may have to run this from a terminal. Once your settings are how you like them, go to the nvidia-settings Configuration ( bottom, on the left side of nvidia-settings ), click *Save Current Configuration*. This will save the settings to ~/.nvidia-settings-rc

Then add **nvidia-settings --load-config-only** to *System->Preferences->Statup Applications*.

Each time you log in *nvidia-settings* will run.

This is from the *man nvidia-settings*:
```

3. Loading Settings Automatically
       The NVIDIA X driver does not preserve values set  with  nvidia-settings between
runs  of  the X server (or even between logging in and logging out of X, with xdm(1),
gdm, or kdm ).   This  is  intentional,  because different users may have different
preferences, thus these settings are stored on a per-user basis in a configuration file 
stored in the user's home directory.

       The configuration file is named ~/.nvidia-settings-rc.  You can specify a
different configuration  file  name  with  the  --config  commandline option.

       After you have run nvidia-settings once and have generated a configuration file,
you can then run:

            nvidia-settings --load-config-only

       at any time in the future to upload these  settings  to  the  X server again.  For
example, you might place the above command in your ~/.xinitrc file so that your settings
are applied automatically when  you log in to X.
```

I haven't had any success with the ~/.xinit.rc option.

---

### Post by maghoxfr on 2010-02-27
Thanks for the reply, I must be doing something wrong though. This is what I've done.

I open a terminal and type: 
                            **sudo nvidia-settings**

The xserver opens up and I configure the resolution, go to nvidia-settings Configuration and click Save Current Configuration. Then click quit, a sign that says "do you really want to quit?" pops up, I click quit. Then I go to System->Preferences->Statup Aplications, clik on "add" and in the command tab I type:
                     **nvidia-settings --load-config-only.**

Now, restart session: 
                    ** sudo /etc/init.d/gdm restart**

and the old resolution is back. I'm frustrated!!! But I feel that your solution is the closest one I've tried. Do you what I'm doing wrong?

---

### Post by pbrane on 2010-02-28
When you run **sudo** *nvidia-settings* you are saving the config file to the root account, I think. You don't need need to run nvidia-settings as root. I never have, and this works fine for me. Are you sure that the resolution you want is one supported by your monitor, or card? Mine is set to **Auto** in the **X Server Display Configuration** section of nvidia-settings. Is that where you are setting your resolution? I use the native resolution of my monitor.

Check to see if you have a file called .nvidia-settings-rc in your home dir. And make sure it is owned by you, not root. If you do have the file with correct permissions then something else is going on.

I added nvidia-settings to my System->Administration menu. Most changes you make are immediate. So you can play around with the settings.

---

### Post by Richard1979 on 2010-02-28
> WTF guys? I cant believe it! I'v been using linux'es like 20 years.

So why are you asking here...:popcorn:

---

### Post by maghoxfr on 2010-02-28
> Check to see if you have a file called .nvidia-settings-rc in your home dir. And make sure it is owned by you, not root. If you do have the file with correct permissions then something else is going on.
I have that file but,*feeling like an idiot here*, i don't know how to make sure it's owned by me. On the xserver I change the resolution to 1024x768 and 60hz, I can actually use it but next time I start session the old resolution is back so I change settings every time time I log in. I've found this video but I can't do a couple of things in there (there's a comment of mine in youtube).
[http://www.youtube.com/watch?v=V0_uCQnK_t4]("http://www.youtube.com/watch?v=V0_uCQnK_t4")
i'm reading a lot of forums and manuals, I'm a bit overwhelmed because i'm not a programmer, I'm switching from windows, having a hard time sometimes. Thanks for the help, really.

---

### Post by realzippy on 2010-02-28
run in terminal:

**nvidia-settings**

choose "nvidia settings Configuration" and hit 

"save current configuration".

(if home folder is not default,change it)

if you already have *nvidia-settings --load-config-only* added to autostart,it should work.
If configfile is not owned by you,it will complain about permissions.Generally right-click on a file to see its owner and read/write permissions.

---

### Post by realzippy on 2010-02-28
If it does not work (again),can you post your (empty) xorg.conf file please?

---

### Post by maghoxfr on 2010-02-28
I checked the xorg.conf file and permissions are for root not for me. Here's my xorg.conf

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@leucaena)  Wed Dec 23 23:29:52 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Feb  1 03:17:59 PST 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Envision CT500g"
    HorizSync       30.0 - 56.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_60 +0+0; 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


how can I change permissions, I've seen a guy in youtube who does so just by right-cli9cking and choosing open as administrator, I don't have that option.

---

### Post by realzippy on 2010-02-28
...you have the option as admin.Type

[B]gksudo nautilus
[/B]
to run nautilus as root.But which file permission you want to change?xorg.conf *has* to be owned by root.Do not change this.

is there no option in nvidia-settings for 1600x1200 ?
Your xorg.conf says you chose 1024x768...
([I]Option "metamodes" "1024x768_60 +0+0; 1024x768 +0+0")
[/I]

---

### Post by maghoxfr on 2010-02-28
> to run nautilus as root.But which file permission you want to change?xorg.conf has to be owned by root.Do not change this.

Ok, I thought I had to change it, I don't really know what I'm doing. Yes that's the resolution I've chosen the problem is that it allows me to use it as long as I'm logged in but I can't save it so when I restart my pc it's back the 800x600 and I have to reset it to 1024x768 every time.
This is what comes up when I type gksudo nautilus in terminal.

> 
gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:4984): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4984): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4984): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio *this means that the folder does not exist*
Please ask your system administrator to enable user sharing.


I have been trying to do one of this things that seem to work for some people, but I'm too ignorant for doing it myself.

[http://www.youtube.com/watch?v=V0_uCQnK_t4]("http://www.youtube.com/watch?v=V0_uCQnK_t4")

[http://linux.die.net/man/1/nvidia-settings]("http://linux.die.net/man/1/nvidia-settings")

---

### Post by realzippy on 2010-02-28
Have you partiallly run commands from the links you gave?Changed permissions?Edited files....?Want to say it makes things not easier,so
I would suggest to "start from scratch" with the actual NVIDIA driver,
with a new useraccount (to ensure "vanilla" config files.If it runs you can later one delete this new account).
So,first create a new user.
Log in into *that* new account and download this driver:
[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run&lang=us&type=GeForce)
if running 64 bit ubuntu:
[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run&lang=us&type=GeForce)
to your Desktop.
Please do not make any resolution settings.
If you are at this point,post.

---

### Post by maghoxfr on 2010-02-28
> If you are at this point,post.
Yes I did some things those links said. So starting from the scratch should be the best solution. I followed your advice and created a new user with administrator rights, and without changing anything it started with the resolution I wanted (1024x768 ) so I restarted just to see if it stuck and it did! I didn't get any driver or anything I just created a new user. Now I have an extra user (the one I was using before), do I erase it? Thanks very much.

---

### Post by pbrane on 2010-02-28
try this in your home directory:
```

ls -l .nvidia-settings-rc

```

you should see something like this:
```

-rw-r--r-- 1 user user 1203 2010-02-28 08:47 .nvidia-settings-rc

```
As you can see *user* owns the file. If this says *root* then you can change this to your username by typing this in a terminal:
```

sudo chown user:user .nvidia-settings-rc

```
replacing *user* with your username.

removing that extra user is up to you. 

If you have a **.nvidia-settings-rc** in your home dir and you are running **nvidia-settings --load-config-only** in startup then you shouldn't need anything else. In my xorg.conf file there is no resolution information. You shouldn't need any there if you run nvidia-settings.

---

### Post by houseworkshy on 2010-03-01
I had and eventually solved this problem very soon after 9.10 came out.  What the problem was then was the driver itself and the fix was to download a beta and use that. 
I followed the advice here 
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)
Things seem to have changed again.  I have just tried this ( invalid ppa ) and methods such as posted above, for both 9.10 and 8.04.4 on my sisters machine and failed.     I suspect mvidia have updated the driver but don't actually know.
 If that is what has happend the best advice for people who are thinking of reinstalling is don't yet.  If you must then, until you see solved threads for your own nvidia version, don't add the hardware drivers as the driverless resolution is just use-able for browsing and word processing but drops even further once the hardware driver goes in.  My own system is fine but I won't allow any nvidia updates until the forums suggest things are ok again.   If the situation is the same as in the first couple of weeks following the 9.10 releace then the only real fix is to hang fire for a while.
Had I not had to reinstall for her tonight I wouldn't have known as my own system which was last installed a couple of months ago, is still fine. Unfortunately the fixes which worked for a fresh install then don't now, at least not for me.

---

### Post by realzippy on 2010-03-01
Sorry for delay,but it was real late here in europe...
I would [COLOR="Red"]not[/COLOR] suggest to use your new account with administrator privileges,
lack of any security.Wanted you to create a new user with
"desktop user" privileges,sorry I did not make this clear.So
please create another one...and see if resolution still works.

---

### Post by underquark on 2010-03-01
Nobody mentioned trying xrandr yet to set new settings?

One description [here](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html).

I had trouble getting 1280x1024 to stick on a 19" AOC LCD monitor and followed the advice on using xrandr to add a new setting (1280x1024_60) and called it "default".  Couple re-boots later (one forced because of a power-cut) and it's working.

---

### Post by realzippy on 2010-03-01
> **underquark said:**
> Nobody mentioned trying xrandr yet to set new settings?

One description [here](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html).

I had trouble getting 1280x1024 to stick on a 19" AOC LCD monitor and followed the advice on using xrandr to add a new setting (1280x1024_60) and called it "default".  Couple re-boots later (one forced because of a power-cut) and it's working.

You use NVIDIA drivers?

---

### Post by underquark on 2010-03-01
> **realzippy said:**
> You use NVIDIA drivers?Yes.  I'm at a different machine at present but I think it was the 180 NVIDIA driver (not the Dev one) with built-in graphics (NVIDIA GeForce 7025) on an Asus motherboard, 2Gb on the machine with 0.5Gb shared for graphics.  Monitor AOC LM965 if I recall correctly.

Machine booted with quite small fonts for login and password (thus suggesting it was in high-res) then monitor displayed "Mode not supported" and then desktop kept coming up in glorious 640x480 with enormous dialog boxes.  Able to change to 1280x1024 with System...Display and then using the proprietary tools.  Initially wouldn't save changes to xorg.conf but I changed the permissions and it then appeared to save them.  On restart, back to low-res and xorg.config back to vanilla.  Manually editing xorg.config had the same results (i.e. back to low-res on restart).  Using xrandr to detect modes and then adding in a newmode of --addmode default 1280x1024_60 sorted it.

I've found another link that might explain it better:
[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

---

### Post by groping_blindly on 2010-03-01
If you're through struggling with xorg, and NOTHING is working, you might want to try Envy:  [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Envy is an automatic driver installer for ATI and nVidia that detects your card for you, pulls down the drivers and configures xorg.  It's great for users (like me) that don't know much more than how to copy and paste terminal commands.  Kudos to it's developer, who has saved my desktop a couple of times now.  I cannot describe how awesome this thing is, especially after a couple of hours of despondent and unsuccessful hacking. 

Most recently, my system shat itself in the usual way (low res, tiny fonts at login etc) and the most recent backup of xorg.conf appeared to be a duplicate of the current non-functional one.  Tip: if you're using Nvidia and under 'hardware drivers' there's a little empty check box next to 'NVIDIA accelerated graphics driver (latest cards)' DON'T TICK THE BOX.  NOT EVEN IF YOU WANT TO SEE WHAT HAPPENS.

I'm running Ubuntu 8.04 and a GEforce 6 series.  Not sure if Envy works for 9.10 and up, but if you're reading this, it probably can't make your situation any worse.  Good luck!

---

### Post by ykd on 2010-03-01
Hello all.  I'm a new user to Ubuntu and need some help badly! I originally started to build a HTPC for my living room, however it's turned into a month and half long battle between Ubuntu and Nvidia. To start from the beginning of my journey. I installed Ubuntu 9.10 on a Compaq D5, 1GB of RAM, on board Intel video, and sound card. I then installed 2 video cards purchased from BestBuy BFX GeForce 8400GS PCI, and Hauppauge PVR160 for mythtv. The installation of Ubuntu went well, the on board video displays a picture without flickering but the Nvidia driver will not install. I've tried every freakin method, work around what have you. I'm tired of reinstalling the OS which I've done 10 plus times. WHAT GIVES!!!!!!!!:mad: I'm not here to bash people or linux but I thought this was better then windoze.  How come Nvidia and the linux community have not found a way to install a driver that works for everyone on any machine? What's the point in using linux when drivers are accessible and work most of the time in Windoze? Valid questions anyone who's planning to leave Windows for Ubuntu would ask and however for some reason or another are not solved completey. Now I'm done letting of some steam.  I would like to move forward using Ubuntu and not revert to Windows Media Center. Here's a list of my recent steps on my box. All advice is much appericated! Thanks in advance!

By the way Envyng did not work for me and i'm always receving the stupid message that i'm not running nvidia-settings as root when i launch the nvidia app. I've added gksudo before the command but I'm still getting the message, plus i gave the user video rights.:frown:

1. Installed kubuntu
2. Installed Gnome desktop via sudo apt-get install ubuntu-desktop
3. Performed sudo apt-get upgrade
4. Installed the driver using "hardware driver" under systems

---

### Post by cariboo on 2010-03-01
This works for me, make sure you have the horizontal and vertical refresh rates for your monitor, then drop to a console (Ctrl-Alt-F1) at the prompt type:

```
nvidia-xconfig
```

The above command will create a new /etc/X11/xorg.conf file. Once the new file has been created, open the xorg.conf file for editing:

```
nano /etc/X11/xorg.conf
```

and replace the horizontal sync and vertical refresh rates that nvidia-xconfig added to the file and replace them with the ones specified for your monitor, once finished editing the file reboot, and you should get the resolution you want.

---

### Post by maghoxfr on 2010-03-02
> create a new user with "desktop user" privileges. So please create another one...and see if resolution still works.

Ok, I'll try that tonight (that's in about 12 hours here) if the resolution sticks, what do you think I should do? I also tried Envy a while ago to install the drivers; the drivers were installed succesfully but resolutions issues remained.

---

### Post by realzippy on 2010-03-02
> **maghoxfr said:**
> Ok, I'll try that tonight (that's in about 12 hours here) if the resolution sticks, what do you think I should do? I also tried Envy a while ago to install the drivers; the drivers were installed succesfully but resolutions issues remained.

If new desktop-user account works (resolution),you could keep it as yours and delete the other 2 accounts...
Back tonite...

---

### Post by maghoxfr on 2010-03-02
> If new desktop-user account works (resolution),you could keep it as yours and delete the other 2 accounts...
Back tonite...

Yes, It worked again, thanks for the help! I tried many things, complicated to me but the solution was so simple...Now I'll backup some info and I'll be good to go. Just another question, the user I'll be keeping must have administrator rights or just "desktop"?

---

### Post by realzippy on 2010-03-02
Beware of admin rights,e.g.you should not surf the internet with "root" account(!!)...,"desktop user" is right choice.

---

### Post by maghoxfr on 2010-03-02
ok, but if I want to have just one account, can I use it only as desktop user? Because I use internet a lot and frankly i'd like to have only one user (unless it's not recommended). Thanks for the tips

---


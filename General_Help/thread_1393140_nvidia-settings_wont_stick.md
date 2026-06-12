---
title: "nvidia-settings wont stick"
date: 2010-01-29
forum: General Help
---

### Post by as08 on 2010-01-29
HI,
I have been using ubuntu and these forums for about three months and have learned so much, but i have not found a solution to this problem so this is my first post.

I am running ubuntu 9.10 kernel 2.6.31-17 with nividia GeForce 9400 GT graphics card hooked via hdmi to a sony bravia HDTV. I am trying to change the overscan compensation in nvidia-settings I have opened it via "gksu nvidia-settings" and have saved to xorg.conf but every time i reboot the overscan compensation disapears and it goes to original nividia settings. I am currently running the beta drivers (195.30) but have also tryed 190. I have also tryed using "nvidia-xconfig" and then applying the settings but to no avail.

I am attempting to create a mythtv frontend/backend system and have got these drivers working with mythbuntu 9.10, but somehow corrupted the system and a reinstalled with ubuntu. Sorry if the post is lengthy any help is appreciated!

Also, as soon as i open nvidia-settings the overscan compensation takes effect

---

### Post by Madmoose on 2010-01-29
I don't know if this will help you, but it shouldn't hurt to give it a try. My nvidia setting would reset every time I logged off, and this thread made them stick for me. I hope the thread below will help you out.
[URL="http://http://ubuntuforums.org/showthread.php?t=1321327&highlight=nvidia+setting+save"]
http://ubuntuforums.org/showthread.php?t=1321327&highlight=nvidia+setting+save[/URL]

---

### Post by as08 on 2010-01-29
i think that link is dead

i have errors in the terminal upon opening nvidia-settings similiar to this
[http://ubuntuforums.org/showthread.php?t=422805&page=2](http://ubuntuforums.org/showthread.php?t=422805&page=2) (post #19)

and have tried deleting xorg.conf...

```
sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup
```

create new xorg.conf...

```
sudo nvidia-xconfig
```

save settings to X...

```
sudo nvidia-settings
```

Following these steps, when I go to nvidia-settings, even with new xorg.conf, It goes to what I previously attempted to save, but upon restart it reverts to defult nvidia, is ubuntu selecting a wrong config file?

I am lost, reinstall and pray....?](*,)

---

### Post by hikaricore on 2010-01-29
Nvidia settings aren't meant to stick.
Read the documentation for the nvidia-settings tool.

---

### Post by Ordes on 2010-01-29
u can save them... i dont know the terminal command for nvidia confi as i am not on my pc. But u should be able to figure it out...Its the nvidia control panel. Where u get all the specs and settings about your card

u just need open this with
$ sudo <command>

and than the save button in the panel will work...

if u dont sudo it the save button wont work....

---

### Post by howefield on 2010-01-29
Try this after backing up xorg.conf.

```
sudo rm /etc/X11/xorg.conf
```

```
gksu nvidia-settings
```

Then save to a new xorg.conf after you have changed the settings.

---

### Post by as08 on 2010-01-29
> **howefield said:**
> Try this after backing up xorg.conf.

```
sudo rm /etc/X11/xorg.conf
``````
gksu nvidia-settings
```Then save to a new xorg.conf after you have changed the settings.

Followed this when starting nvidia-settings my terminal spits out this:

```
loljk@mythbox:~$ gksu nvidia-settings
ERROR: Cannot open display 'mythbox:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line
       34 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).

```I changed the overscan as well as the resolution to 1280x720 hit apply then saved to /etc/X11/xorg.conf upon reboot the resolution is correct but there is no overscan compensation.

I know what xorg.conf is but have no idea what any of it means or how to edit it. Is it possible nvidia-settings is just not writing the overscan to xorg.conf? Here's what nvidia writes to xorg.conf:

---

### Post by ebharv on 2010-01-29
Here's a thought it's just a guess so let me know if it works. I'm not at my Ubuntu machine and can't try it right now.

The reason you got those errors was because you deleted the xorg.conf file that nvidia-settings reads.
Go back and do a ```
sudo nvidia-xconfig
``` this will create a **NEW DEFAULT** xorg.conf file.
Then do ```
gksu nvidia-settings
``` change what you want and click the save button.
in the dialog navigate to '/root/', click save, reboot.

From the errors you posted it looks like the settings are loaded from .nvidia-setting-rc in the root folder. If this is so it will explain why my settings have also failed to stick. I however have never gotten the error you posted.

---

### Post by as08 on 2010-01-29
Thanks for the replies, but i have tried all of your instructions and am still stuck.

I have tried creating new xorg.conf with nvidia-xconfig then launching gksu nvidia-settings

I have tried cut and pasting the preview of xorg.conf in nvidia-settings to xorg.conf
 
And I have tried saving it to "/root" like the previous post suggest, but these all failed. It worked with mythbuntu 9.10, maybe I will try a fresh install of that, hopefully it wont crash after i setup myth...sigh:roll:

---

### Post by hikaricore on 2010-01-30
> **hikaricore said:**
> Nvidia settings aren't meant to stick.
Read the documentation for the nvidia-settings tool.

^  Running nvidia-settings as root will not make my original statement untrue.
You will need to read the documentation for examples of how to use this tool.
Please don't make me repeat myself again.  There are also several tutorials for this tool around the internet.

---

### Post by stinkeye on 2010-01-30
```
man nvidia-settings 
```
Look at this section
```
USER GUIDE
   Contents
       1.   Layout of the nvidia-settings GUI
       2.   How OpenGL Interacts with nvidia-settings
       [COLOR="Red"]3.   Loading Settings Automatically[/COLOR]
       4.   Commandline Interface
       5.   X Display Names in the Config File
       6.   Connecting to Remote X Servers
       7.   Licensing
       8.   TODO
```

---


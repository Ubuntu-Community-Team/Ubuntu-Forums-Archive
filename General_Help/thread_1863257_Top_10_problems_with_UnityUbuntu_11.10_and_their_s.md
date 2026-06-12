---
title: "Top 10 problems with Unity/Ubuntu 11.10 and their solutions"
date: 2011-10-17
forum: General Help
---

### Post by Meelad on 2011-10-17
I think we are done now with the reactions to the new version of Ubuntu and Unity, and it's time now to start trying to fix its most important problems..

This thread is NOT for bashing Unity or Ubuntu 11.10.. This thread is to try to solve the problems of the people who are willing to give it a try (me included).

Now I don't have all the solutions but we'll try to solve them all one by one together, or at least confirm that there is no way at the moment to solve this problem so that everybody will be informed..

We'll begin with listing the problems, and I'll keep updating the OP in this thread when new problems/solutions are established.. I'll begin now..


[SIZE=4][COLOR=black]**1- Unity crahses after playing with Compiz..**[/COLOR][/SIZE]
[B]
Suggested solution:[/B] log out (using CTRL+ALT+DEL) and try to log in with Unity 2D or as a guest.. The idea is to get access to the terminal.. In the terminal window run:
```
gconftool-2 --recursive-unset /apps/compiz-1
```
and then re-enable the Unity plug-in in CCSM. If it doesn't work run the following code in the terminal:
```
unity --reset
```and log out and in again (using Unity). Unity should start normally now. If it still doesn't start, go through the same steps and run this command in the terminal instead:
```
unity --replace
```**Cause of problem:** Activating some plugins in Compiz could automatically disable essential plugins that unity uses, leading to disabling it.. Resetting Unity's settiings should solve this problem.
**Solution status:** waiting to be confirmed..
**System Installation:** Ubuntu 11.10, final release, both upgraded and fresh installations.



[SIZE=4]**2- Buggy (extremely slow) wireless internet connection**[/SIZE]
I need more information about this one, since I confirm that I don't have this problem after a fresh installation of 11.10.. (I can download at 2.0 Megabyte per second through a wireless connection with moderate signal)
[B]
Suggested Solution:[/B] This solution seems to work for some people.. Give it a shot.. Open the terminal and run:
```
sudo gedit /etc/modprobe.d/iwlagn.conf
```And change:
```
options iwlagn 11n_disable=1 11n_disable50=1
```to:
```
options iwlagn 11n_disable=1
```And then reboot.. If the above file doesn't exist just create one and enter the line above, and then reboot..

**Cause of Problem:** Unclear. Although it seems to happen more often with upgrade to 11.10 than with fresh 11.10 installations, but it may be caused by specific types of hardware. (The solution aims to disable the 802.11n connectivity)
**Solution Status:** waiting to be confirmed..
**System Installation:** Ubuntu 11.10, final release. Mostly in upgraded systems.



[SIZE=4]**3- Ubuntu 11.10 ignores the default applications set in System Settings**[/SIZE]
The problem is when I change the default Music player for example in System Settings => System Info => Default Applications, Ubuntu ignores my new choice and keep running music files with Banshee by default..

**Suggested Solution:** It's not a pretty solution but at least you won't have to change the default application for every single file extension.. You can in one command in the terminal change the default application for every extension the current app is default for.. First create a backup for the file we are going to change (just in case):
```
sudo cp /etc/gnome/defaults.list /etc/gnome/defaults.list0
```Then run:
```
sudo sed -i s/[current-default-app-name]/[new-default-app-name]/g /etc/gnome/defaults.list
```Example:
```
sudo sed -i s/banshee/audacious2/g /etc/gnome/defaults.list
```This will change the default music app from banshee to Audacious.

Then, log out and in again and you should be able to run ALL of your music files with Audacious through double clicking..

There is a drawback though.. There is a possibility that Audacious can't run ALL the files that banshee can run, the command above won't differentiate between those files, as it will just replace banshee with Audacious as the default app for all the file types banshee was associated with.. If you don't think this is a problem for you, then go for it.. In general I don't expect you to face a lot of problems with files that banshee can run but Audacious can't, in which case you can change this single file type back to banshee through Right Click on the file => Properties => Open With => Choose banshee and click on Set As Default.

If anything goes wrong you can always switch back to the old settings using the backup we created earlier with this command:
```
sudo cp /etc/gnome/defaults.list0 /etc/gnome/defaults.list
```**Cause of Problem:** Ubuntu 11.10 associates files types individually with apps by default. So it doesn't matter if you change the default app for music in the System Info settings, because banshee will remain associated with all the individual music files types, which seem to have the priority over the general default app setting. At the moment I don't understand what the Default Application settings in System Info are for.
**Solution status:** waiting to be confirmed..
**System Installation:**  Ubuntu 11.10, final release, both upgraded and fresh installations.



[SIZE=4]**4- Can't run Unity 3D after upgrading the system**[/SIZE]
[B]
Suggested Solution:[/B] Make sure the additional drivers for your graphics card are installed (if not install them through More Apps => Customization => Additional Drivers) then run in the terminal: 
```
gedit /home/[Your Home Directory]/.config/compiz-1/compizconfig/config
```And replace its content with:
```
[general_ubuntu]
profile = 
integration = true

[gnome_session]
profile = 

```Log out and in again.

**Cause of Problem:** Old settings from older version of Ubuntu. With fresh 11.10 installation you should not have this problem.
**Solution Status:** waiting to be confirmed..
**System Installation:** Ubuntu 11.10, final release. In upgraded systems.



[SIZE=4]**5- Unable to mount ipod - Unhandled Lockdown error (-5)**[/SIZE]

**Suggested Solution:** Run the following code in the terminal:
```
sudo apt-get install ifuse libimobiledevice-utils
idevicepair unpair && idevicepair pair
```**Cause of Problem:** Missing plug-ins.
**Solution Status:** Confirmed.
**System Installation:** Ubuntu 11.10, final release, both upgraded and fresh installations.


-----------------------------------

**Helpful advices:**

1- Don't upgrade to Ubuntu 11.10.. A fresh installation seems to be much more stable than upgrades.
2- Don't play with Compiz too much, and be careful when you do that not to disable important plug-ins that Unity needs.
3- Always update your 11.10 system. I just updated my fresh 11.10 installation through System Update, and programs seem to run faster now.. The team seem to be busy now making adjustments to increase the stability of the system. One of those adjustments may solve one or more of your problems. 

--------------------------------

Feel free to share your experience.

**Note:** The idea behind making one thread to list the 10 most common problems with Unity/Ubuntu 11.10 is to make the transition easier for new users, by knowing beforehands what to expect in most cases and by making access to the solutions of the most common problems much easier..

---

### Post by ajgreeny on 2011-10-17
Great idea!

You forgot the need to reset compiz as well as unity with your solution, which I think should be
```
gconftool-2 --recursive-unset /apps/compiz
unity --reset
```unless the change to gnome3 has removed the need for that first command.

I am unable to run unity 3D on my machines, so can't even attempt these in any really useful way.

---

### Post by Meelad on 2011-10-17
> **ajgreeny said:**
> Great idea!

You forgot the need to reset compiz as well as unity with your solution, which I think should be
```
gconftool-2 --recursive-unset /apps/compiz
unity --reset
```unless the change to gnome3 has removed the need for that first command.

I am unable to run unity 3D on my machines, so can't even attempt these in any really useful way.

Thanks for your input.. I'll add it to the solution above..

Feedback from people trying this solution is appreciated.

Also feel free to list more problems (especially the most important ones) that you encounter with Unity and 11.10.

---

### Post by philinux on 2011-10-17
General Help sticky thread. ;)

---

### Post by Meelad on 2011-10-17
I'm working now on a solution for the wireless internet connection problem (which I see is quite common) and the default applications problem (for music and video for example)..

If anybody can help I appreciate it...

---

### Post by alexvy13 on 2011-10-17
Yea, my internet has been slower since I've been using alpha 2 of oneiric
Windows Partition works normal speed, but ubuntu doesnt.

---

### Post by Meelad on 2011-10-17
> **alexvy13 said:**
> Yea, my internet has been slower since I've been using alpha 2 of oneiric
Windows Partition works normal speed, but ubuntu doesnt.

Did you upgrade to 11.10 or made a fresh installation?

---

### Post by Meelad on 2011-10-17
A suggested solution for the default app problem was added.. Waiting for your feedback..

I can definitely use some help here guys.. :D

On to the next problem..

---

### Post by Meelad on 2011-10-17
OP updated. New problem added..

---

### Post by Armaeddon on 2011-10-17
I had the first issue mentioned here, and when i tried to log on to the terminal, it tells me that Authentication has failed. What do i do?I know my username and password are correct.

edit: i was able to do it by searching for "terminal" and launching that. Thanks a ton!

---

### Post by Meelad on 2011-10-17
> **Armaeddon said:**
> I had the first issue mentioned here, and when i tried to log on to the terminal, it tells me that Authentication has failed. What do i do?I know my username and password are correct.

edit: i was able to do it by searching for "terminal" and launching that. Thanks a ton!

You are welcome..

OP update with a solution to problem number 2..

---

### Post by WanderingAlbatross on 2011-10-18
On your internet connection problem.  I haven't noticed a drastic change in the speed of my internet.  I upgraded from 10.04 to 11.04 a while back, now to 11.10.  This means I am not using a fresh install.  Hope this helps.

---

### Post by Bobik-s on 2011-10-18
Me and several guys from Russian Ubuntu forum got the issue with screen brightness.  The brightness of the laptop screen (Intel video, standard  driver) always resets to minmized when screen turns off and on again.  While trying to make it maximized using standard keys the brightness  progress bar does not function properly - if one presses continuously  "brightness up" the progress bar goes up and then down with every press.  Still after several presses it's possible to maximize the brightness of  the screen.

The solution is still unknown. The bug's discribed here and you can vote for it if you're affected
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/876711](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/876711)

---

### Post by Meelad on 2011-10-19
> **WanderingAlbatross said:**
> On your internet connection problem.  I haven't noticed a drastic change in the speed of my internet.  I upgraded from 10.04 to 11.04 a while back, now to 11.10.  This means I am not using a fresh install.  Hope this helps.

You haven't noticed a big change in speed after the upgrade or after trying the solution in this thread?

> **Bobik-s said:**
> Me and several guys from Russian Ubuntu forum  got the issue with screen brightness.  The brightness of the laptop  screen (Intel video, standard  driver) always resets to minmized when  screen turns off and on again.  While trying to make it maximized using  standard keys the brightness  progress bar does not function properly -  if one presses continuously  "brightness up" the progress bar goes up  and then down with every press.  Still after several presses it's  possible to maximize the brightness of  the screen.

The solution is still unknown. The bug's discribed here and you can vote for it if you're affected
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/876711](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/876711)

Bug is confirmed and they are working on a solution there.. Keep an eye there and your problem should be solved in a short time..

By the way, new problem with solution added.. And if I am going to make it to 10, I'd have to have some help here.. Otherwise, a top 5 would do, and I hope it could help some of the people who want to try 11.10..

---

### Post by mati.mati on 2011-10-19
I solved this (Problem #1) by opening Compiz Configuration Settings Manager from terminal (ccsm command) and then under Desktop section setting Ubuntu Unuty plugin option ON.

---

### Post by linuxwin2 on 2011-10-20
Thanks for this threads.
I have a problem:
I can't use xfsce (xdm): when I put the password in xdm, no thing happen
But I can use gnome (gdm) and I can access to my Graphic Desktop.

---

### Post by zero2xiii on 2011-10-20
> 1- Unity crahses after playing with Compiz..

 Suggested solution: log out (using CTRL+ALT+DEL) and try to log in with Unity 2D or as a guest.. The idea is to get access to the terminal.. In the terminal window run:

Just a suggestion to this. Why not just "Ctrl + Alt + F1"? for a terminal.

And just another thought. Please add to the "Solution status:" area the indications of what version and kernel version the suggested solution works. I have noticed a lot of people reporting issues have an Alpha 1/2 or even a Beta version. Very few people run the official released version. And some issues HAS been fixed from the beta to the release version (Atleast most of the issues I had). So i suggest adding that, and maybe include if it was an upgrade or a fresh install. Since that also plays a HUGE part (Since jumping from gnome2 to gnome3 is a pretty big step)

But I love the idea behind this thread, will contribute as much as I can. If you need specific tests on code etc, shout. I can run a few virtual machines and test different issues and there possible solutions.

Cherz

---

### Post by stinkeye on 2011-10-20
> **Meelad said:**
> 1- Unity crahses after playing with Compiz..

 Suggested solution: log out (using CTRL+ALT+DEL) and try to log in with Unity 2D or as a guest.. The idea is to get access to the terminal.. In the terminal window run:
Code:
gconftool-2 --recursive-unset /apps/compiz
For 11.10 the command should be 
```
gconftool-2 --recursive-unset /apps/compiz-1
```
and then you will need to re-enable the unity plugin in ccsm.

---

### Post by Meelad on 2011-10-20
Thanks guys for your input. I'm not really an expert in Ubuntu myself, so you'd expect me to make some mistakes, and probably miss some easier solutions, that's why I appreciate your input to comment or correct me if I'm wrong..

**mati.mati** and **zero2xii** you are right. But sometimes (it happened to me too) when Unity crashes you can't even run other programs. I ran the terminal, but I couldn't type anything in it (crashed), that's why I had to log in again in a working environment. But if you can still run the terminal, then it's definitely worth trying because it's much easier.. What I tried to put there is an easy solution that can work for most people to keep it as simple as possible.

**linuxwin2**, you're welcome.. I'm not really sure about your problem.. I'll see if more people are having this problem and try to find a solution for it, but this thread is mainly about the most common problems with Unity and Ubuntu 11.10 which some people seem to be having problems with, mostly because it's newly introduced and most people are still unfamiliar with its most common bugs and their solutions.

**zero2xii**, good points.. I'll add a field named (System Installation) which covers the version, the release, and the type of installation. But I'd need more input to be able to know if this problem is happening more in upgraded systems or fresh installation, or if that's a no factor.
And I definitely need help to verify the code I put there.. As I said, I'm not an expert myself, I've just had a lot of help on this forum and I'm willing to give something back, especially for the people who are new to Ubuntu..

**stinkeye**, thanks! Problem #1 updated.

---

### Post by badperson on 2011-10-21
For issue number 1....how long does it take for those utilities to run? I'm using the byobu terminal, and it's been going for a couple hours...seems stuck on 

> (unity-window-decorator:2484): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


after running

> unity --reset
although it does seem like it writes new line every so often

---

### Post by Shoriminimoe on 2011-10-21
I'm having an issue with #1 and tried resetting Unity but I get a long string of errors.

This is what I get:
> sam@Suzie:~$ gconftool-2 --recursive-unset /apps/compiz
sam@Suzie:~$ unity --reset
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
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
Initializing staticswitcher options...[ERROR]: Option "next_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "next_no_popup_button" already defined
[ERROR]: Option "next_no_popup_key" already defined
[ERROR]: Option "prev_no_popup_button" already defined
[ERROR]: Option "prev_no_popup_key" already defined
[ERROR]: Option "next_panel_button" already defined
[ERROR]: Option "next_panel_key" already defined
[ERROR]: Option "prev_panel_button" already defined
[ERROR]: Option "prev_panel_key" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "auto_change_vp" already defined
[ERROR]: Option "popup_delay" already defined
[ERROR]: Option "mouse_select" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "brightness" already defined
[ERROR]: Option "opacity" already defined
[ERROR]: Option "icon" already defined
[ERROR]: Option "icon_only" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "row_align" already defined
[ERROR]: Option "focus_on_switch" already defined
[ERROR]: Option "bring_to_front" already defined
[ERROR]: Option "highlight_mode" already defined
[ERROR]: Option "highlight_rect_hidden" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "highlight_border_color" already defined
[ERROR]: Option "highlight_border_inlay_color" already defined
done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Starting unity-window-decorator
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x34000e9


I'm still having issues with my toolbars disappearing and otherwise. What do I need to do?

---

### Post by vegegoku on 2011-10-23
what about the create launcher problem, we cant create a new launcher by left clicking the desktop, is there an easy way to create  a new launcher?

---

### Post by vegegoku on 2011-10-23
another problem related to screen resolution, ubuntu 11.04 didnt detect my new desktop monitor resolution but i was able to fix the problem by adding xrandr commands in the gdm initial scripts, now for ubuntu 11.10 i cant find any place to put these commands and make them work. i cant figure out where to put these commands for lightDM.

---

### Post by stinkeye on 2011-10-23
> **vegegoku said:**
> what about the create launcher problem, we cant create a new launcher by left clicking the desktop, is there an easy way to create  a new launcher?

You can drag a program from the dash to the desktop.

---

### Post by vegegoku on 2011-10-23
i know about this , but what about if i want to add a costume launcher or a launcher for an executable file that does not appear in the dash

---

### Post by stinkeye on 2011-10-23
On 11.10 you need to install gnome-panel
```
sudo apt-get install --no-install-recommends gnome-panel
```
to use the old create launcher dialogue.

Then hit alt+F2 and paste(ctrl+v) in this command
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

Can also save this script as **Create_Desktop_launcher** for a right click nautilus script item.
```
#!/bin/bash

gnome-desktop-item-edit ~/Desktop/ --create-new
```

Place in **~/.gnome2/nautilus-scripts/** and make executable.


> ...but what about if i want to add a **costume** launcher...
for a **costume** launcher, follow the same process while wearing a rubber nose. :wink:

---

### Post by vegegoku on 2011-10-24
> **stinkeye said:**
> On 11.10 you need to install gnome-panel
```
sudo apt-get install --no-install-recommends gnome-panel
```
to use the old create launcher dialogue.

Then hit alt+F2 and paste(ctrl+v) in this command
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

Can also save this script as **Create_Desktop_launcher** for a right click nautilus script item.
```
#!/bin/bash

gnome-desktop-item-edit ~/Desktop/ --create-new
```

Place in **~/.gnome2/nautilus-scripts/** and make executable.



for a **costume** launcher, follow the same process while wearing a rubber nose. :wink:
that was really helpful, thanx a lot

---


---
title: "Upgraded to new kernel, NO UNITY!"
date: 2012-09-05
forum: General Help
---

### Post by Jedcurtis on 2012-09-05
Hello all,
I just ran the update manager which upgraded my kernel to the new 3.2.0-30.  Now when logging in, if I choose Ubuntu (which is the Unity DE) all I have on login is my pretty background image!  I can still start a terminal and run stuff from the command line, but I have no Panel, Launcher, and conky isn't starting.  Just a desktop picture.  Is there a problem with the new kernel, or have I busted something?
I'm logged in right now using the Gnome selection at login.  Everything is just fine when I do so.  Everything starts just fine as it did last time I logged in using Gnome.  It seems the only problem is if I choose Ubuntu before login.  What gives?  Any ideas?

Thanks everyone...

Jed

---

### Post by exploder on 2012-09-05
I upgraded the kernel last on two of my machines last night. I did not have any problems but both of my installs are pretty much stock. Unity 3D is working on both computers.

---

### Post by vasa1 on 2012-09-05
> **Jedcurtis said:**
> Hello all,
I just ran the update manager which upgraded my kernel to the new 3.2.0-30.  ...
No problems with **32**-bit after the update. Unity 3D is fine.

---

### Post by Jedcurtis on 2012-09-05
Yeah, I'm pretty perplexed!  The update manager showed up in the launcher, which means there are updates to install, I clicked on it, sure enough there were 6 or 7 updates all having to do with a kernel update to 3.2.0-30.  I'd been running 3.2.0-29 just fine using Unity.  Now, like I said, I can login to Gnome, Gnome Classic, no prob.  I choose Ubuntu and bang, just my desktop picture.
I also ran the startup applications from the terminal and told it to autostart the cairo dock which did start but it was surrounded by black boxes...
Any ideas anyone?
Thanks,
Jed
PS, I was just starting to enjoy Unity in the last couple of weeks too.  Figures!  Oh well, Gnome seems to be fully functional, so I at least am able to work but I do want my Unity back!!!
Just logged out and back in, and Ubuntu 2D is fine....  This is really weird....

---

### Post by Jedcurtis on 2012-09-05
How do I revert back to the previous kernel?

Jed

---

### Post by mcduck on 2012-09-05
What kind of graphics card do you have, and are you using the drivers from Ubuntu's repositories or manually installed ones from AMD/nVidia web site?

If you are using manually installed graphics drivers you might have to reinstall the driver after eacjh kernel update, as the driver installer builds some kernel modules which are specific to the kernel version you run at the moment, and therefore fail to work with new kernel versions installed by nomrla system updates.

(also, if the graphcs drivers are working fine, you can try simply resetting the Unity settings to defaults. "unity --reset" in a terminal should do that for you)

---

### Post by Jedcurtis on 2012-09-05
Ok, so I rebooted, went into GRUB, selected the previous kernel and I'm still getting the same results.  Very weird.  I haven't installed or uninstalled anything recently, but somehow it seems I've broken the 3D version of Unity.  Unity 2D is working fine.  For that matter, Gnome is working fine as well.  I have 3 different selections when logging in to choose from for Gnome.  Gnome, Gnome Classic, and Gnome Classic (no effects).  There are also some options for logging in using cairo dock, and when I choose the one that says Cairo Dock Unity the same thing happens.  Just my nice desktop picture with nothing else on the screen.
I'm totally stumped here.  The only change is the kernel.  However, like I said, when I change to the previous kernel on reboot using GRUB the same thing still happens so I can't rationally blame the kernel upgrade.
I do have the Optimus for video.  Any ideas anyone?

Thanks,
Jed

---

### Post by Jedcurtis on 2012-09-05
Holy crap Mcduck, your a genius.  I've been seeing your name all over the place the last couple of days!  That did the trick it seems.  Using the 'unity --reset' appears to have it all back in order.  I'll reboot one more time to be sure, but hopefully that solved this...

Thanks a bunch,
Jed

---

### Post by Jedcurtis on 2012-09-05
%$#&, spoke to soon.  No love.  On re login same thing again.  I have the bumblebee installed for graphics as I have Optimus.  I've heard to many horror stories about installing the stand-alone nVidia drivers so I never have.  Just always relied on Bumblebee.
Wonder whats happened?

Jed

---

### Post by Jedcurtis on 2012-09-05
@mcduck,

Here is what shows up in terminal after typing 'unity --reset'...

> jed@jed-XPS-15Z:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:4122): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/jed/.compiz/session to /home/jed/.compiz-1/session
[LOG]: Copied file /home/jed/.compiz/session/102da03c463a4929e9134683667830335700000028380049 to /home/jed/.compiz-1/session/102da03c463a4929e9134683667830335700000028380049
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:4130): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
ERROR 2012-09-05 05:22:18 unity.gtk <unknown>:0 gtk_icon_info_get_filename: assertion `icon_info != NULL' failed
ERROR 2012-09-05 05:22:18 unity.gtk <unknown>:0 gtk_icon_info_free: assertion `icon_info != NULL' failed
ERROR 2012-09-05 05:22:18 unity.gtk <unknown>:0 gtk_icon_info_load_icon: assertion `icon_info != NULL' failed
ERROR 2012-09-05 05:22:18 unity.gtk <unknown>:0 gtk_icon_info_free: assertion `icon_info != NULL' failed
WARN  2012-09-05 05:22:18 unity.launcher LauncherIcon.cpp:433 Unable to load 'workspace-switcher' from icon theme: 
Starting gtk-window-decorator
WARN  2012-09-05 05:22:18 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.

(gtk-window-decorator:4144): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
WARN  2012-09-05 05:22:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810

WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810

WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch icon: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch name: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810

WARN  2012-09-05 05:22:19 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x17a4810

WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x17a4810
WARN  2012-09-05 05:22:19 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window46137349
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
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
ERROR 2012-09-05 05:22:19 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"

Don't know what to make of it...

Jed

---

### Post by mcduck on 2012-09-05
> **Jedcurtis said:**
> %$#&, spoke to soon.  No love.  On re login same thing again.  I have the bumblebee installed for graphics as I have Optimus.  I've heard to many horror stories about installing the stand-alone nVidia drivers so I never have.  Just always relied on Bumblebee.
Wonder whats happened?

Jed

That's strange, if resetting Unity fixed the problems one would assume it would work even after a reboot. There must be something that's messing the settings again...

I'm not too familiar with Bumblebee, as Optimus is disabled on my laptop by the manufacturer, so I have no idea if it might have something to do with the problem. I suppose it could be related, I'll take a look if I can find somehting...

There is also a more powerful version, "compiz --reset", which will reset all COmpiz settings instead of just the Unity-related ones. But if resetting Unity didn't work, then I doubt that would do much good either.

You could try creating another user acocunt on the system, just to see if the problem is limited to your user only. And if it is, you'd then know that it's some config file in your user's home directory that's causing the problems. I don't know if Bumblebee, for example, has such user-specific config files...

---

### Post by Jedcurtis on 2012-09-05
Stranger and stranger!  When trying to do the 'compiz --reset' it tells me the following;

> compiz (core) - Warn: Unknown option '--reset'

compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
When I actually open the Compiz Configuration Settings Manager and go to preferences, it has unity selected and underneath I can click on "Reset to defaults".  When I do, the panel and the launcher both disappear!  I'll try the new user idea...
By the way, I also lose the window bar at the top of my applications which let me minimize, maximize or close....
Jed

---

### Post by Jedcurtis on 2012-09-05
In system settings under "Details" it is now telling me I've got the 'Intel Sandybridge Mobile' Graphics.  Before this kernel upgrade it always said 'Unknown'.  Not sure what to make of this.

Jed

---

### Post by Jedcurtis on 2012-09-05
@mcduck

Created a new user account, and I can successfully login to Unity.  Any suggestions now?
I guess I must have broke something in my original user account?
Thanks,
Jed

---

### Post by mcduck on 2012-09-05
take a look at all the hidden files & directories in your user's home, is there anything that might be related to bumblebee? You could try moving/renaming it to make sure it's not causing the problem. And also, does running "unity --reset" work every time? Would simply restarting Unity instead of resetting ("unity --replace") work as well?

---

### Post by Jedcurtis on 2012-09-05
Still no love.  'unity --replace' exhibits the same behavior.  I created a user with admin rights named tester, logged in fine.  I log out and back in as my original username, and voila, problems again.  Also I'm not seeing any bumblebee directory in the /Home directory.

Thanks,
Jed

---

### Post by Jedcurtis on 2012-09-05
How would I go about 're-installing' Bumblebee?  Is that even possible?

Jed

---

### Post by mcduck on 2012-09-05
> **Jedcurtis said:**
> How would I go about 're-installing' Bumblebee?  Is that even possible?

Jed

That should be possible, but I'm not sure if it would help anything. Since the problem doesn't affect the new user, it must be because of some messed up configuration file in your user's home. And reinstalling the package wouldn't help with that, as the package manager never touches any user-specific configuration files.

...actually after taking a look at bumblebee's wiki pages, I doubt it's causing the problem. It doesn't seem to have any user-specific settings or anything like that. Of course that means I have no idea what could be behind your problems. :/

But on the other hand, if "unity --reset" or "unity --replace" gets things working, at least temporarily, you could maybe add one of thse commands to your startup applications. At least that could make it easier for you to access your own user acocunt while trying to find out what's causing the problems...

---

### Post by Jedcurtis on 2012-09-05
@mcduck,
Thanks for all your efforts to help me!  It is much appreciated!  I just went ahead and did a reinstall of Ubuntu.
Matter of fact I just finished grabbing my files from UbuntuOne.  I can't imagine why the whole world isn't using Ubuntu.  It all took around a half hour.  I spent 7 or 8 times that long trying to fix whatever it was I broke.  Anyway, with the right partitioning scheme, a reinstall is pretty painless and in my case this time, it worked!
It definitely wasn't the kernel, as I'm logged in and running fine.  I hate that I don't know what I did wrong.  In my defense, my wife and kids sometimes sneak onto my laptop.  It is the only explanation I have, as nothing to my knowledge had been changed.
25 years as a network engineer, and I sure wish it had all been with Linux...
What a great user community we have here at ubuntuforums!  I try to tell everyone I know to switch to Linux as fast as they can.
Again, thank you for your help and patience.  No other OS in the world can offer the support we get here for free!

Jed

I'd mark as solved, but I don't see the option...

---

### Post by mcduck on 2012-09-05
No problem, and great that you got everything working again, even though the actual problem remains a mystery...

---


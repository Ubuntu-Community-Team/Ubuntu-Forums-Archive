---
title: "Oneiric known Bugs WITH Work Arounds"
date: 2011-10-14
forum: General Help
---

### Post by cariboo on 2011-10-14
Please post the bugs you have run into and how you **[COLOR="Red"]worked around them[/COLOR]** here.
Do not post your problems, please raise a support thread thanks.

Keep in mind, that Linux is infinitely customizable, you don't have to stick with Unity as a desktop environment. Gnome-shell and gnome-session-fallback. the GTK-3 version of the 2 panel interface are in the repositories. 

Synaptic package manager is no longer installed by default, but if you have the universe repositories enabled, it is easily installed. 

To get the most out of Unity, install compizconfig-settings-manager.

**Update** It was suggested that I also mention that Thunderbird is now installed as a mail client, instead of evolution, as in previous versions.

---

### Post by The Bright Side on 2011-10-14
I have run into a number of bugs / grievances, though I have found no workarounds for most of them yet.

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1847941](http://ubuntuforums.org/showthread.php?t=1847941) - I get the same battery icon
[*]"Startup programs" no longer contains a full list of programs run on startup (like bluetooth, login sound, remote desktop, Ubuntu One), thus depriving me of the ability to customize what gets loaded
[*]According to preview articles, the Alt-Tab switcher should show previews of windows. On my system, it doesn't.
[*]Audacious' Status Icon plugin no longer works. Fixed this issue by whitelisting 'audacious' in the dconf-editor.
[*]Dash sometimes does not show up when moving mouse to the left screen edge while a window is maximized. I hear that this is a known issue and will be fixed very soon.
[/LIST]

Overall, I find it sad that liberties that Ubuntu used to provide are being removed from one release to the next: the most recent example being the ability to fully control which programs load on startup. Also, I get the feeling that many of the system settings have been stripped down majorly, e.g. it is no longer possible by default to configure a theme, and there are no screensavers. I presume that some of this is WIP, but I have trouble understanding the reasoning behind these kinds of decisions, especially since one of the major advantages of Ubuntu over competing operating systems, IMHO, was that it gave maximum control to the user.

That said, I have only worked with 11.10 for a couple hours so far, but I think it has great potential. Once the community has all the right tweak tools to unlock its full powers, it will be a very good OS.

EDIT: in 11.04, I found it great that I could move my mouse cursor to the top left of the screen to bring up the dash without delay. Now that it has been removed from there, I can only bring it up by moving the mouse to the left edge and waiting for a second. I can see this driving me crazy down the road.

---

### Post by cheesekiller on 2011-10-14
my wobbly windows sometimes "STICK"  that rly gets on my nerves.

also how the hell can i add menu items?   before i'd type menu into the dash and press enter and then add it with the menu editor but now i can't. i suspect some of this (like no screensavers) is gnome 3s doing but idk.... at any rate i have a lump sum of programs that need to be added to my dash and they can't be.......    seriosuly  it feels faster and more fluid but if i can't add programs manually (because believe it or not the software center doesnt have everything) then im going back to 11.04 (the good unity with the nice top button)



also i like my launcher set to size 32 and to open to top left and now i have to go to top left and move down for the dash to open.......................      i liked it when it just came open when i threw my mouse to the corner............

---

### Post by Henkdroid on 2011-10-14
For the Alt+Tab you press the down key and it previews it.

---

### Post by howefield on 2011-10-14
> **The Bright Side said:**
> Overall, I find it sad that liberties that Ubuntu used to provide are being removed from one release to the next: the most recent example being the ability to fully control which programs load on startup.

In terminal use the commands..

```
cd /etc/xdg/autostart/
```

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Startup applications should now show up.

---

### Post by Tman5293 on 2011-10-14
I encountered a bug involving the xorg.conf file, the fglrx driver for AMD/ATI graphics cards, and Catalyst Control Center. This is the problem I found (quoted from my thread in the General Help section):

> **Tman5293 said:**
> I just did a fresh install of 11.10 and I'm having some trouble getting the ATI graphics drivers working properly. I downloaded the drivers from AMD's website but after installing them, Ubuntu would boot to a blank black screen. I ended up uninstalling those via the command prompt. Then I tried the proprietary drivers that said post release updates and those have a bug that does not allow them to install properly. After I cleaned up that mess I installed the regular FGLRX proprietary drivers and rebooted and now it seems to be sort of working.

My problem now is this: I have two monitors. When I try to set them up as a side by side configuration with Catalyst (the default is a cloned display on both monitors) it crashes. I am currently only able to use my main display and was forced to disable my second monitor. They are different sizes and therefor different resolutions. I want to use the second display as an extended desktop just like I did in 11.04. But I can't do anything because Catalyst crashes every time I try to enable the second display as an extended desktop and not a cloned display.

Does anyone have a solution to this? I really would like to be able to use both of my monitors.

I was eventually able to find a work around/solution to this:

Here's how I did it:

I opened the terminal and started messing around with aticonfig. I ended up using this code which creates as many monitors as you want in the xorg.conf file. Heads is the number of displays:

```
sudo aticonfig --initial --heads=2 --adapter=1
```

After that I rebooted and then tried to set it up with Catalyst. Catalyst recognized my second monitor and allowed me to set it as an extended desktop with the correct resolution. After I applied that, Catalyst told me that I needed to restart my PC in order for the changes to take effect. After the restart my second display was still not working. I went to Catalyst to see what was up and my monitor was there but all options for it were grayed out. I couldn't even set it as a cloned display. So I closed Catalyst and went to the Ubuntu display settings and turned on the second monitor through that and I was pleasantly surprised when it actually worked! I opened Catalyst back up and sure enough, there was my second monitor shown side by side with my primary monitor as an extended desktop.

So it turns out it was a bug in the xorg.conf file.

---

### Post by CharlesA on 2011-10-14
This thread is ***not*** for criticism about the release. Such posts will be removed.

---

### Post by glaubersm on 2011-10-14
Search for files and folders is not working, nothing happens when I click to start the search (when search is open by unity or gnome-shell menu). 
Search works only in nautilus.
Is there some workaround?

---

### Post by sgage on 2011-10-14
In a fresh install of OO, and using Gnome Shell, incoming messages in Thunderbird were not triggering either a popup notification or putting the icon in the bottom right hand dynamic "tray" thing. 

Solution: I had to manually install the package notification-daemon.

This was not a problem throughout the entire dev cycle, and only appeared when I did a clean install of the final release.

---

### Post by CharlesA on 2011-10-14
> **Patak said:**
> ...so why remove my post then? and which thread ***is*** for criticism?
There are plenty of threads for criticism already, but most of them turn into flamefests and are closed. Also I PMed you regarding your post.

---

### Post by uRock on 2011-10-14
> **glaubersm said:**
> Search for files and folders is not working, nothing happens when I click to start the search (when search is open by unity or gnome-shell menu). 
Search works only in nautilus.
Is there some workaround?

This thread is for posting known workarounds. You may want to start a thread to ask for help.

---

### Post by glaubersm on 2011-10-14
> **uRock said:**
> This thread is for posting known workarounds. You may want to start a thread to ask for help.

ok, thanks and sorry. :)

---

### Post by hojjat on 2011-10-14
Thanks for sharing this solution. I tried it and I didn't get notification after installing notification-daemon. Can you elaborate how you did it (i think there is some configuration involved?)

---

### Post by Retor on 2011-10-14
Could not log in to account

Fixed with: sudo dpkg --configure -a

Now I'm working on getting Unity 3D to work on all accounts, not just one :)

Btw: I've tried unity --reset

---

### Post by rft183 on 2011-10-14
This may be fairly application-specific, so I don't know if this is the right place to post it, but...  I had problems getting Moneydance 2011 to work in 11.10 64-bit. I installed Oracle Java, but that didn't help.  It turns out that the Moneydance deb installs its own version of java, which is 32-bit.  I guess that's what caused the problem.  To fix, I had to delete the /opt/Moneydance/jre/ directory and create a link from /opt/Moneydance/jre/ to my new Oracle Java installation.  It would probably work to create the link to the OpenJDK installation, but I haven't tried reverting my changes.

---

### Post by drs305 on 2011-10-14
**Nautilus crashes when a new folder is opened.**

[COLOR="DarkRed"]UPDATE 17 Oct 11: The launchpad mailing list indicated this problem has been fixed. Once I updated to *ubuntuone-client-gnome 2.0.1-0ubuntu2* nautilus no longer crashes for me.[/COLOR]

For many of us not using Ubuntu One, removing *ubuntuone-client-gnome* appears to stop the crashing.
```
sudo apt-get purge ubuntuone-client-gnome
```

Other users have reported success by removing *nautilus-open-terminal*:
```
sudo apt-get purge nautilus-open-terminal
```

---

### Post by rft183 on 2011-10-14
I also had an issue under 64-bit 11.10 using an Nvidia graphics card.  When I would switch users, my screen would get all garbled.  I had opted not to change my graphics driver when the proprietary driver message box popped up.  It said I was already using the proprietary one, version 173.  After having the garbled graphics issues, I activated the "Recommended" driver.  It did not have a version number.  It seems to have solved the graphics problems for me.

---

### Post by glaubersm on 2011-10-14
> **drs305 said:**
> **Nautilus crashes when a new folder is opened.**

For many of us not using Ubuntu One, removing *ubuntuone-client-gnome* appears to stop the crashing.
```
sudo apt-get purge ubuntuone-client-gnome
```

Other users have reported success by removing *nautilus-open-terminal*:
```
sudo apt-get purge nautilus-open-terminal
```

Crashes stop here when I remove nautilus-terminal. :)

---

### Post by cariboo on 2011-10-14
> **The Bright Side said:**
> I have run into a number of bugs / grievances, though I have found no workarounds for most of them yet.

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1847941](http://ubuntuforums.org/showthread.php?t=1847941) - I get the same battery icon
> [*]"Startup programs" no longer contains a full list of programs run on startup (like bluetooth, login sound, remote desktop, Ubuntu One), thus depriving me of the ability to customize what gets loaded

you can populate gnome-session-properties, using the following commands:

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

> [*]According to preview articles, the Alt-Tab switcher should show previews of windows. On my system, it doesn't.

Alt-Tab works here, see screenshot

> [*]Audacious' Status Icon plugin no longer works. Fixed this issue by whitelisting 'audacious' in the dconf-editor.

> [*]Dash sometimes does not show up when moving mouse to the left screen edge while a window is maximized. I hear that this is a known issue and will be fixed very soon.

Just click the BFB at the top of the launcher to see the dash.

[/LIST]

> Overall, I find it sad that liberties that Ubuntu used to provide are being removed from one release to the next: the most recent example being the ability to fully control which programs load on startup. Also, I get the feeling that many of the system settings have been stripped down majorly, e.g. it is no longer possible by default to configure a theme, and there are no screensavers. I presume that some of this is WIP, but I have trouble understanding the reasoning behind these kinds of decisions, especially since one of the major advantages of Ubuntu over competing operating systems, IMHO, was that it gave maximum control to the user.

A lot of what has been removed, is because of Gnome 3, the gnome devs have decided what's best for us. There are many work arounds, to fix some of what is missing, to change themes and fonts, plus many other things, install gnome-tweak-tool, it will install gnome-shell as a dependency. Keep in mind that that it took over 9 years for gnome 2.X to get to the way we all liked, gnome 3 is still in it's infancy, and should get more configurable with add-ons as time goes on.

> That said, I have only worked with 11.10 for a couple hours so far, but I think it has great potential. Once the community has all the right tweak tools to unlock its full powers, it will be a very good OS.

> EDIT: in 11.04, I found it great that I could move my mouse cursor to the top left of the screen to bring up the dash without delay. Now that it has been removed from there, I can only bring it up by moving the mouse to the left edge and waiting for a second. I can see this driving me crazy down the road.

You can set the delay time for the launcher to show in compizconfig-settings-manager, that is in the repositories.

**Note** about the screenshot, before anyone asks, I'm using a dual monitor setup

---

### Post by webfiend on 2011-10-14
**Issue:** Pressing "Enter" occasionally results in the pointer freezing until I reboot.

**Workaround:** System Settings -> Mouse and Touchpad -> uncheck "Disable touchpad while typing"

I don't know if it's the best workaround available, but my pointer hasn't frozen since I did that.

---

### Post by The Bright Side on 2011-10-14
Thanks for the answers! This is becoming a very helpful thread.

I have been experiencing another bug: I am currently unable to log into my admin account, as the password is rejected and I am automatically returned to the login screen.

This is a known issue and a fix has already been posted on Ubuntu Forums, here it is:
[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233)

I will try this when I get home tonight.

---

### Post by cariboo on 2011-10-14
We came up with a solution to the problem of not being able to login, in the Oneiric testing  sub-forum try Ctrl-Alt-F1 to get  to a console, then enter the following commands:

```
whoami (make sure you're logged in with the same account that is trying to login on lightdm)
sudo service lightdm stop
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm start
```

---

### Post by stinkeye on 2011-10-14
**Problem:** After installing nautilus-gksu "Open as administrator" fails to 
appear in the nautilus right click menu.

**Fix:**```
sudo cp /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0/
```

---

### Post by The Bright Side on 2011-10-15
Problem (is this a bug? I sure hope so):
In GNOME Shell, I am copying about 80 GB of data from my backup disk to my main disk as I'm typing this. When I started copying, the small "file operations" window appeared, but then disappeared (while I was in Firefox). It is now copying my files, but I have no way to see how far it is or if there are problems (I suppose it will tell me, or at least I hope so).

Workaround:
Enable the status bar in Nautilus and press F5 regularly. If the free space on your hard disk diminishes between F5 presses, you know that copying is still in progress.

Anybody else experience this?

---

### Post by glaubersm on 2011-10-15
> **The Bright Side said:**
> Problem (is this a bug? I sure hope so):
In GNOME Shell, I am copying about 80 GB of data from my backup disk to my main disk as I'm typing this. When I started copying, the small "file operations" window appeared, but then disappeared (while I was in Firefox). It is now copying my files, but I have no way to see how far it is or if there are problems (I suppose it will tell me, or at least I hope so).

Workaround:
Enable the status bar in Nautilus and press F5 regularly. If the free space on your hard disk diminishes between F5 presses, you know that copying is still in progress.

Anybody else experience this?

Yes. One more stupid problem.
[http://ubuntuforums.org/showthread.php?t=1860482](http://ubuntuforums.org/showthread.php?t=1860482)

---

### Post by lovinglinux on 2011-10-15
**Issue:** after logging off or rebooting, Unity 3D doesn't launch properly and displayed only a top panel with a weird menu.

**Context:** clean install, preserving home config files, from Kunbuntu 11.04.

**Error:** after trying "Unity -reset" on a termninal, I've got the following error.

```
I/O warning : failed to load external entity
"/home/me/.compiz/session/10f9d0a87f9328c22130451756883507900000027170038"
```

**Solution:** deleting **~/.compiz-1/session** contents and **~/.config/compiz-1/compizconfig/config** file solved the problem.

---

### Post by drs305 on 2011-10-15
**Synaptic fails with 'out_of_range' or 'SIGBART' error**

If Synaptic (not installed by default) won't run and generates one of the above messages, disabling the Accessibility settings appears to fix it:
[LIST]
[*]Open Universal Access (Dash/Home > Universal Access; or System Settings (upper right) > Universal Access)
[*]Seeing tab > Screen Reader; Off
[/LIST]

---

### Post by moorhead98 on 2011-10-15
One killer bug is that if you have a nVidia Go 7xxx series driver, unity/gnome-shell won't work.
There is a small workaround, adding UNITY_FORCE_START=1 to someplace (see askubuntu thread [here]("http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity").) But unity and gnome shell run very slow, and there is a plethora of bugs that i think could be because of it.
Also, look at the shadows in the pictures. Thats what every application looks like. 
And (not as much a bug as a complaint) nautilus 3 has far less functionality and goodness as nautilus 2, or nautilus elementary. and it doesnt look to good in ambiance
If there are any fixes please post them

---

### Post by ianp5a on 2011-10-15
To clarify the method to **disable Unity and restore the Classic Gnome desktop,** in the "Ubuntu Software Centre", search for "gnome-session-fallback".
Install it, then log out. At the login screen, click the gear wheel and choose "GNOME Classic" before logging in. it will then always log in to the previous desktop style including the Application and Places menus until you choose any other option.
A different method has been suggested elsewhere that uses the command line window. This method is for those who don't want to do it that way and shows that it is not necessary.

---

### Post by drs305 on 2011-10-15
> **moorhead98 said:**
> One killer bug is that if you have a nvidia 7xxx series driver, unity/gnome-shell won't work.

I'm using the Nvidia 7600GS and it's working fine with the nvidia current driver. I had striping very early on in pre-alpha testing, especially when I resumed from suspend. Now I get striping for about a second after resuming from suspend and then the screen returns to normal. Otherwise it's fine. Unity's speed doesn't seem to be an issue for me.

It may be a problem on some or many Nvidia 7xxx cards, but not for me.

---

### Post by lovinglinux on 2011-10-15
> **drs305 said:**
> I'm using the Nvidia 7600GS and it's working fine with the nvidia current driver. I had striping very early on in pre-alpha testing, especially when I resumed from suspend. Now I get striping for about a second after resuming from suspend and then the screen returns to normal. Otherwise it's fine. Unity's speed doesn't seem to be an issue for me.

It may be a problem on some or many Nvidia 7xxx cards, but not for me.

I just edited the original post. The  problem is actually about Geforce **Go** 7300/7400. 

I have nVidia 7300 GT and it works.

---

### Post by moorhead98 on 2011-10-15
> **lovinglinux said:**
> I just edited the original post. The  problem is actually about Geforce **Go** 7300/7400. 

I have nVidia 7300 GT and it works.

My bad, I forgot that
Is there a fix for the geforce go 7xxx drivers? I went to launchpad and saw the bug report and I'm confused by it. It says for a couple of things that it was fixed but I don't know (Sorry, I'm very launchpad illiterate)
Here's a pic

---

### Post by lovinglinux on 2011-10-15
**Issue:** mouse mysteriously grabbing the window on it's own

**Solution:** launch CCSM and disable *Unity MT Grab Handles* plugin

---

### Post by bclintbe on 2011-10-15
I'm a teacher, and the gradebook program my school uses runs in Java. I have restricted extras added (so I've got java + icedtea plugin, etc) just like I've always done, but if I click on the link to start my gradebook, it only gives the option to open it with Firefox itself, not icedtea. My only workaround so far is to save the applet to my Downloads folder, then right mouse click on the file and choose Open With to start Icedtea. I know this isn't much of a workaround, but I haven't seen any way to get Firefox to use IcedTea as the default way to start applets in the browser. Any other suggestions are welcome!

---

### Post by concomitantelegy on 2011-10-15
The HP 2000 219dx has a hardware switch, F12, to enable wifi. It works in 11.04. The key doesn't respond in 11.10. The workaround is to blacklist hp_wmi and reboot. After you login, press the button; it will turn from orange (disabled) to white (enabled). (You may have to press it twice.)The computer can then detect wireless networks.

[FONT=Courier New]~$ sudo gedit /etc/modprobe.d/blacklist.conf[/FONT]
blacklist hp_wmi
Save and quit.
Reboot.
Login.

Before blacklisting, [FONT=Courier New]~$ rfkill list[/FONT] returns two interfaces that are likely soft and/or hard blocked. After blacklisting, I get one interface, phy0, that is neither hard nor soft blocked. Success.

---

### Post by SushiAddiction on 2011-10-16
Dual Monitor only works in mirror mode

xorg.conf was renamed to
/etc/X11/xorg.conf.dist-upgrade-201110070100 
and replaced with a new xorg.conf with only a few lines in it.

fix 
gksu nautilus (nautilus may crash :( Install thunar)
and rename xorg.conf to xorg.conf.crap
then rename xorg.conf.dist-upgrade-201110070100 to xorg.conf

Restart

---

### Post by uRock on 2011-10-16
> **SushiAddiction said:**
> gksu nautilus (nautilus may crash :( Install thunar)There's a fix for the nautilus crashes listed above. :)

---

### Post by Tman5293 on 2011-10-16
> **SushiAddiction said:**
> Dual Monitor only works in mirror mode

xorg.conf was renamed to
/etc/X11/xorg.conf.dist-upgrade-201110070100 
and replaced with a new xorg.conf with only a few lines in it.

fix 
gksu nautilus (nautilus may crash :( Install thunar)
and rename xorg.conf to xorg.conf.crap
then rename xorg.conf.dist-upgrade-201110070100 to xorg.conf

Restart

Does this only work if you upgraded? I did a fresh install of 11.10 and I was unable to find xorg.conf.dist-upgrade-201110070100. Only had the new, bugged xorg.conf.

---

### Post by mc4man on 2011-10-16
Folders opening with something other than nautilus in upgrade installs on certain actions

The issue is 11.10 no longer uses an entry for  - 
inode/directory= in the [Default Applications] section of ~/.local/share/applications/mimeapps.list

Because of that an existing line there will not be overwritten & the one from natty usually will be specifying a .desktop that no longer is used  - nautilus-folder-handler.desktop
To fix - either go to location & delete the mimeapps.list file
```
nautilus ~/.local/share/applications
```

Or open the file in an editor & under the **[Default Applications] **section remove this line entirely, it's not needed
inode/directory=

```
gedit  ~/.local/share/applications/mimeapps.list
```

Edit: for users of the Classic session
the best thing to do is  to change that line to this in
 [Default Applications]

```
inode/directory=nautilus-home.desktop
```

---

### Post by Mega_Mike on 2011-10-16
I had the same issue with the ugly battery status icon when I tried to use the Faenza icon set in 11.10.  My hacky workaround was this:

[LIST]
[*]Put the theme back to 'ubuntu-mono-dark'
[*]sudo gedit /usr/share/icons/ubuntu-mono-dark/index.theme
[*]change the line 'Inherits=Humanity-Dark,gnome,hicolor' to 'Inherits=Faenza-Darkest'
[/LIST]

This make most of the icons Faenza with a proper battery icon...not exactly perfect

> **The Bright Side said:**
> I have run into a number of bugs / grievances, though I have found no workarounds for most of them yet.

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1847941](http://ubuntuforums.org/showthread.php?t=1847941) - I get the same battery icon

[/LIST]


---

### Post by MartinusEx on 2011-10-16
I upgraded from 10.10 to 11.10 via LiveCD

One of several issues:
The update deleted all user accounts besides the "admin"

The home directories where NOT deleted

After adding a new user via sytem settings -> user admin I had a new user login which bounced back to the login.

Reason was group permissions/settings for /home/user and underlying files and folders, which where buggy imported from 10.10 (The group ID / user ID where stated like #1002 etc. )

chown user:user /home/user -R did the job
Afterwards the user could login

---

### Post by drs305 on 2011-10-16
Not a bug, but this may stop unnecessary searching:

**Resume from suspend without password request.**

This option is no longer available through gconf-editor but is available via dconf-editor (install dconf-tools).

From the terminal, to avoid having to input the user password when resuming from suspend:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```
Note: This can also be run as root.

Added: Forum member *Gitominoti* has informed me that on his system just going to Dash and the Screen settings page disables the password necessity from resuming. This would of course be the logical way of a screen lock to work, and hopefully mine is an isolated case and it works normally for others without having to run the dconf command.

Note 2: If you run the dconf command, the Screen settings command is frozen and cannot be changed unless you unlock it via dconf...

---

### Post by clegends on 2011-10-16
***Mods***, seems you're being a bit heavy handed with your moderating of this thread... I posted a work around for the compiz edge bindings not working, and it was removed. I can't set the edge bindings to anything other than the defaults for the unity launcher; it either won't work properly, or causes supreme system instability. One workaround is to manually change the settings on each login in ccsm, adding back in the edge bindings for the scale and expo plugins. It works, though there must be better solutions. Does anyone have a better workaround?

This post is about a *workaround*. I have already posted something else in the main threads for support, and a launchpad bug is being filed. Could you please have the courtesy to contact me directly if you need to remove this post, rather than just assuming this doesn't meet your quality requirements and removing it? Thanks.

edit: Here's another workaround. Install easystroke, and configure a mouse gesture to take the place of the edge binding. It works, but not quite as convenient as the actual edge binding working. I guess that's the point of a work around...lol.

---

### Post by drs305 on 2011-10-16
@ clegends,

I have searched this thread for a deleted message (which the mods can still see), other forums to which it may have been moved, and the Jail. I cannot find such a post. 

We would normally notify the poster if we move a post, and in any event as the poster you would usually still be redirected to the new location. 

Your concerns are noted here. The best course of action now is to take this up in the Resolution Center if you are sure the post actually made it into the thread and wonder what happened.

This thread originator or another moderator may move your last post and mine into the Resolution Center regardless, as that is the place for these issues to be discussed. I posted here since others have probably read your post.  Please limit further posts on this to the Resolution Center.

---

### Post by kooldino on 2011-10-16
Moving the mac-style File / Edit pulldowns at the top of the screen to the particular window that they belong to:

[http://ubuntuforums.org/showthread.php?t=1859565](http://ubuntuforums.org/showthread.php?t=1859565)

---

### Post by uRock on 2011-10-16
> **kooldino said:**
> Moving the mac-style File / Edit pulldowns at the top of the screen to the particular window that they belong to:

[http://ubuntuforums.org/showthread.php?t=1859565](http://ubuntuforums.org/showthread.php?t=1859565)

What is this mac-style thing you are speaking of? Please be more descriptive.

---

### Post by kooldino on 2011-10-16
Machine would not load the desktop post-install.  It would hang at the battery check.

Solution:
[http://ubuntuforums.org/showthread.php?t=1741512&page=2](http://ubuntuforums.org/showthread.php?t=1741512&page=2)

---

### Post by kooldino on 2011-10-16
> **uRock said:**
> What is this mac-style thing you are speaking of? Please be more descriptive.


How the File/Edit/etc Pull-down menus would be stuck to the global bar at the top of the screen rather than being attached to the window that would normally contain them.  I don't know how else to describe it.

---

### Post by MartinusEx on 2011-10-17
I upgraded 10.10 to 11.10 using a Live CD:

I had several users set up under 10.10, all the user accounts where gone, the home/user directories have NOT been deleted though.

Adding one previous user gave login, but the login bounced back.
Since disk space is OK I assumed group rights to be messed up.

I found the /home/user directory was set to user #1002 (which is the ID) but not the user/group setting I just added and which the account had under 10.10

I remedied this using "chown user:user /home/user -R" in the terminal. Now the user is able to log in
*********************************************************

Oneiric removed Evolution, which I reinstalled, but it has changed a bit.
Now my imap accounts can not be displayed (gettting error messages instead) but I can see that there are new mails.

I got this one solved by killing my imap accounts and setting then up "from scratch"
Now Evolution can display content and all is back to normal


*********************************************************
A mounted partition /mnt/data is gone  (the mounting point)
which I hopefully remedied by adding it to /etc/fstab

I remember to have added the mount point using gnome-disk-utility (palimpsest).

**********************************************************
No sound from the PC speaker:

Gnome-Alsa-Mixer does not work (does not open)

Another Alsa-Mixer-GUI only shows two settings and I am  not able to add other mixer elements.

Opening alsamixer in the terminal works OK.
Changing the settings does not give sound on the PC speaker.

Line out not yet tested.

**********************************************************
Other issues to follow

Martin

---

### Post by miahotrod on 2011-10-17
Bug Shutdown does not work from the switch user screen.
type shutdown in the apps menu and shutdown form thire

---

### Post by lovinglinux on 2011-10-18
> **rft183 said:**
> I also had an issue under 64-bit 11.10 using an Nvidia graphics card.  When I would switch users, my screen would get all garbled.  I had opted not to change my graphics driver when the proprietary driver message box popped up.  It said I was already using the proprietary one, version 173.  After having the garbled graphics issues, I activated the "Recommended" driver.  It did not have a version number.  It seems to have solved the graphics problems for me.

On the other hand, I am having a better experience with 173 driver. For instance, I was able to enable Wobbly in Compiz and now I can.

---

### Post by lovinglinux on 2011-10-18
**Problem:** Unity launcher (dock) does not appear if window is maximized.

**Workaround:** open the Unity plugin settings on Compiz Config Settings Manager and set the "Hide Launcher" option to "Autohide".

---

### Post by pheonixcoder on 2011-10-18
> **lovinglinux said:**
> **Issue:** after logging off or rebooting, Unity 3D doesn't launch properly and displayed only a top panel with a weird menu.

**Context:** clean install, preserving home config files, from Kunbuntu 11.04.

**Error:** after trying "Unity -reset" on a termninal, I've got the following error.

```
I/O warning : failed to load external entity
"/home/me/.compiz/session/10f9d0a87f9328c22130451756883507900000027170038"
```

**Solution:** deleting **~/.compiz-1/session** contents and **~/.config/compiz-1/compizconfig/config** file solved the problem.

I faced the same issue with Ubuntu 11.10 when i installed compiz config settings. I have a ATI 4 series 1GB card (Dell Studio XPS 1647 i5 system) and using Open Source Drivers.

Didn't try the Unity reset
I upgraded from 11.04 to 11.10.

**Fix**: Created a back up of data and did a clean install for Unity to work again.

Will try to get Compiz config settings again and apply the Fix which you have mentioned

> **Solution:** deleting **~/.compiz-1/session** contents and **~/.config/compiz-1/compizconfig/config** file solved the problem.

---

### Post by EddieGal on 2011-10-18
> **moorhead98 said:**
> My bad, I forgot that
Is there a fix for the geforce go 7xxx drivers? I went to launchpad and saw the bug report and I'm confused by it. It says for a couple of things that it was fixed but I don't know (Sorry, I'm very launchpad illiterate)
Here's a pic
I would like to know the workaround to this too.

Searched the forums but didn't find anything

11.10 hangs on start.

---

### Post by Rick Myers on 2011-10-19
I experienced issues getting my Dell T3500 with 4625 ATI card to dual-head with graphic effects after proprietary driver installation.

Getting the machine to "see" the dual-head;
In a terminal: sudo aticonfig --initial=dual-head --screen-layout=left

I also noted that Catalyst (admin) doesn't run properly from a lens (clicking the apply button just closed the window, changes unsaved). Run it from a terminal to overcome this issue: sudo amdcccle

Using Xinerama caused the graphic effects problem - compiz not functional. In Catalyst > Display Manager select Multi-dsiplay desktop with display(s) 2. 

With Catalyst setup this way I was able to get the full Ubuntu experience.

---

### Post by javi_m on 2011-10-19
PROBLEM: After installing it, the screens freezes at "checking battery state" / 

WORKAROUND: 1º: Try get into the OS by the "previous linux versions" option in GRUB. Then, you need to try different solutions:

A: If the nvidia propietary driver it's already installed, change it for another option. (In my case, change Version 173 to current version). Reboot. If that not helps, go to B

B: Roll back and activate the previous driver. Reboot. Go to C

C: in a terminal, type sudo apt-get install --reinstall nvidia-XXX, where XXX it's the driver version you want (nvidia-current, nvida-173, etc)



-----------------

This problem it's kinda weird. i Reinstalled 11.10(format included everytime) 3 times, and every time this issue was present, but in different ways.

---

### Post by apple_cat on 2011-10-19
Problem:
X11 crashes with signal 11 when opening certain applications .

Fix:
Uninstall xfs (X font server)

Bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/835483](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/835483)

I found this while following a guide to install Maya 2012 on Ubuntu, wherein it recommends you install xfs along with a bunch of other packages. 

Removing xfs seems to fix the problem of X11 crashing with signal 11, with no negative side effects noticed so far.

---

### Post by lovinglinux on 2011-10-19
**Problem:** after installing Broadcom 43xx driver, the wireless is not detected anymore.

**Solution:** [http://ubuntuforums.org/showthread.php?t=1745437](http://ubuntuforums.org/showthread.php?t=1745437)

---

### Post by ldkronos on 2011-10-20
> **pheonixcoder said:**
> I faced the same issue with Ubuntu 11.10 when i installed compiz config settings. I have a ATI 4 series 1GB card (Dell Studio XPS 1647 i5 system) and using Open Source Drivers.

Didn't try the Unity reset
I upgraded from 11.04 to 11.10.

**Fix**: Created a back up of data and did a clean install for Unity to work again.

Will try to get Compiz config settings again and apply the Fix which you have mentioned


I've had this issue of the Unity inteface disappearing on me twice this week ( [http://ubuntuforums.org/showthread.php?t=1864061](http://ubuntuforums.org/showthread.php?t=1864061) ). When it happened today, I simply opened CompizConfig (since you have no Unity dash, you have to use Nautilus to find and launch it) unchecked the Unity plugin, logged out and back in, rechecked it, and all is well.

---

### Post by MartinusEx on 2011-10-20
> **uRock said:**
> What is this mac-style thing you are speaking of? Please be more descriptive.

Here I may help out:

OS X on a Mac uses the same way to serve with menus like oneiric now does. The menu bar on top always shows menu elements according to the program which has the focus.

One thing I like here personally. ;)

rgds

Martin

---

### Post by sieve on 2011-10-20
Bug - Wireless connection drops every few minutes

Solution - I changed the MTU setting to 1500 from Auto

---

### Post by sieve on 2011-10-20
> **MartinusEx said:**
> 
No sound from the PC speaker:

Gnome-Alsa-Mixer does not work (does not open)

Another Alsa-Mixer-GUI only shows two settings and I am  not able to add other mixer elements.

Opening alsamixer in the terminal works OK.
Changing the settings does not give sound on the PC speaker.

Line out not yet tested.



I've had problems with this in the past when upgrading.
To fix it, I opened alsamixer in terminal and found that one of the settings was muted for some reason.  TAB between the settings and then increase the volume on any items that are at 0db.

---

### Post by techvish81 on 2011-10-21
display not upto the mark with a good gpu? (it is not for weird display problems)

install startup manager from package manager, run it and select 24 bit and resolution (1200*1400 etc i dont know the exact numbers) corresponding to your screen size in it.

u will see a noticeable difference in the quality of display.

---

### Post by BlinkinCat on 2011-10-22
I found that "Recovery Console" and "User Defined Sessions" were NOT options on the logon screen -

To include -

Fix - 

Install gdm package from Software Center and select lightdm as the default login Manager.

---

### Post by Colin Keenan on 2011-10-23
> **mc4man said:**
> Folders opening with something other than nautilus in upgrade installs on certain actions

The issue is 11.10 no longer uses an entry for  - 
inode/directory= in the [Default Applications] section of ~/.local/share/applications/mimeapps.list

Because of that an existing line there will not be overwritten & the one from natty usually will be specifying a .desktop that no longer is used  - nautilus-folder-handler.desktop
To fix - either go to location & delete the mimeapps.list file
```
nautilus ~/.local/share/applications
```

Or open the file in an editor & under the **[Default Applications] **section remove this line entirely, it's not needed
inode/directory=

```
gedit  ~/.local/share/applications/mimeapps.list
```

Edit: for users of the Classic session
the best thing to do is  to change that line to this in
 [Default Applications]

```
inode/directory=nautilus-home.desktop
```
The reason I found this suggestion of yours was that when I clicked on the trash icon in the Unity launcher panel, it would run a custom gksu .desktop file asking me to enter my password. I discovered that any gnome-open a folder command would do that.

After removing the inode/directory= ... from the [Default Applications] as you recommended, gnome-open worked for everything except trash://, which was still running the gksu .desktop file.

I found and deleted the inode/directory= ... from the [Added Associations] section of ~/.local/share/applications/mimeapps.list which finally stopped gnome-open trash:// from running the gksu .desktop file. However, now gnome-open trash:// does nothing at all.

To fix this so that I can open the trash by clicking on the trash icon in the Unity launch panel, I created a new .desktop file called userapp-nautilus.desktop and put it in ~/.local/share/applications as follows:
[Desktop Entry]
Encoding=UTF-8
Version=
Type=Application
Exec=nautilus %u %f
Name=nautilus
Comment=
NoDisplay=true

Then in the [Added Associations] section of ~/.local/share/applications/mimeapps.list, I added the following line:
inode/directory=userapp-nautilus.desktop

Now my trash icon finally works.  Looks like inode/directory is still needed after all. I'm surprised nobody else is complaining about the trash icon not working. If it could be removed from the launcher, that's what I would've done and just accessed trash from within nautilus which was working fine from the beginning. Since it couldn't be removed, I decided might as well make it do something.

---

### Post by breek on 2011-10-23
in order to have autologin on ubuntustudio 11.10 file /etc/lightdm/lightdm.conf must be created like this
```

[SeatDefaults]
user-session=xfce
greeter-session=lightdm-gtk-greeter
autologin-user=your_user_name
autologin-user-timeout=0

```

---

### Post by Bobhuber on 2011-10-23
11.10 - Gnome 3 - Fresh install - Cairo-Dock BZR 2.5.0

I have used Cairo-Dock in every other version of Ubuntu but wasn't going to load it in Oneric (didn't really need another dock) untill I decided I wanted the mail notification app that comes with the dock. I decided to make up some custom launchers for the dock to launch some things as root when I needed them and not put them in the main launcher. 
Wow what a difference. I'm not sure if it's because it runs thru DBUS or that I,m running the open GL version of the dock or whats going on but all of the apps launched from the dock open immediately (no cursor wait) and seem to run much faster. I'm pretty sure it's directly associated with the Open GL but well worth the effort of installing the package and creating the launchers on the dock instead of the sidebar.

---

### Post by gippeswyc on 2011-10-24
> **moorhead98 said:**
> One killer bug is that if you have a nVidia Go 7xxx series driver, unity/gnome-shell won't work.
There is a small workaround, adding UNITY_FORCE_START=1 to someplace (see askubuntu thread [here]("http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity").) But unity and gnome shell run very slow, and there is a plethora of bugs that i think could be because of it.
Also, look at the shadows in the pictures. Thats what every application looks like. 
And (not as much a bug as a complaint) nautilus 3 has far less functionality and goodness as nautilus 2, or nautilus elementary. and it doesnt look to good in ambiance
If there are any fixes please post them

After my update to 11.10 I couldn't get it to boot to a GUI. I suspected nVidia drivers and did the following:

sudo apt-get remove nvidia*

All fine now, just have to sort out numerous other problems.

---

### Post by Bobhuber on 2011-10-24
11.10 - Gnome 3 - Fresh install

Every time I opened a program from the sidebar (launcher) the load times and hourglass wait time have been terrible on a high end system . I had Gnome 3 set to default with auto login enabled using (sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell ). After playing around a bit I discovered that using Alt + F2 to launch a program or using Cairo-Dock launchers would fix the problem. Windows opened much quicker, CPU usage dropped etc.etc. I finally came on this solution which is a bit of a pain but definitely makes a big difference. By disabling auto-login in the system settings and leaving the defaults set to gnome the problem disappeared. Windows open normally, mouse appears instantly and the desktop is now usable. 
I have no clue as to what is causing the problem and not thrilled having to log in as a single user but at least its a temporary fix until things get straightened out.

---

### Post by wdaniels on 2011-10-24
> **MartinusEx said:**
> 
No sound from the PC speaker:

Gnome-Alsa-Mixer does not work (does not open)

Another Alsa-Mixer-GUI only shows two settings and I am  not able to add other mixer elements.

Opening alsamixer in the terminal works OK.
Changing the settings does not give sound on the PC speaker.

Line out not yet tested.


I have a similar problem with no sound on my Asus EeePC 701, I assumed it must be a driver bug in snd_hda_intel for some chipsets because my 11.10 desktop is fine. lspci tells me the chipset on the Asus is:

```
Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
```

...so interested to know what your sound hardware is?

NB: Intention to update post with solution once I've found it.

UPDATE: Well it seems to fall more into the category of hardware quirks now. I tried rmmod/modprobe on the module chain to no effect, all kinds of alsa and pulseaudio fiddling, setting different module options, updated to the 3.1 kernel from precise...nothing worked. So I installed the old natty kernel to check that it did work before and while trying to figure out how to get into the grub menu now, ended up cycling the power instead of the usual soft "reboot". Still ended up booting 3.1 but somehow magically I have sound again :S

So I don't suppose it qualifies as a known issue & workaround, but for anyone else having sound trouble, maybe worth trying a hard reset :D

---

### Post by OzzyFrank on 2011-10-24
**_Problem_**: **[COLOR="Red"]Safely Removing USB Drive Causes System Freeze/Kernel Panic[/COLOR]** (in Kernel 3.0.0-12)

**_Fix_**: Go to [http://people.canonical.com/~ogasawara/lp844957/](http://people.canonical.com/~ogasawara/lp844957/) and into the folder for your architecture (i386 or amd64). Install the 3 .debs located therein, and reboot. You should now be able to successfully remove the drive without issue.

**_NOTE_**: What you're actually doing here is replacing the 3 main kernel packages, but for me and a bunch of others affected, there were no issues, with kernel 3.0.0-13 replacing the old one in GRUB, booting into Ubuntu just fine, and resolving the freezing when trying to remove USB drives.

---

### Post by gwm on 2011-10-25
I view this as a bug in the install process.

The way I remember the process, the upgrade option is only available if the current Ubuntu release is up to date and if an Internet connection is available for updating.

My upgrade from the live CD crashed after several hours, near the end, while getting updates from the Internet with about 3 minutes to go. My guess is that the cause was an intermittent internet connection. In the third world, we have to live with 384KB/s shaped (heavily shaped) connections and poor line quality too.

I feel that the Internet update should be divorced from the upgrade script and regard this as a bug. In other words, first we do an offline upgrade (which is quick) and then execute an update (which may take many hours). Then my upgrade would have been complete and the update could have been run again. The advantage of this is that software updates cache downloaded files, giving a sort of restart functionality.

WORKAROUND
Instead of 10 minutes rerunning the software update, I had to do a clean install, which was quick. Then I had many hours of software update and I still have many hours ahead of me, reinstalling and recovering third part applications etc.

:(

---

### Post by sarv_jeet on 2011-10-26
unable to browser files on phone using bluetooth. clicking on the phone icon in nautilus results in error 

'could not display obex://xxxxxxxxxxxxxx'
 dbus error org.freedesktop.DBuserror.serviceunkown The name 1.268 was not provided by any.service files

can send and receive file . no problem in connecting to internet using bluetooth. only file browse on mobile is giving error.

---

### Post by fermilesi on 2011-10-26
Problem: After upgrade (11.04 to 11.10) in an Optimus laptop (Asus M53) lost all Unity effects (snapping windows, graphical application and workspace switcher, fixed icon size at launcher, cant activate unity handles in compiz, etc)

It seems that during the upgrade, Ubuntu installed nvidia drivers or Xorg was switched to nvidia drivers (and nvidia card is not supported on Optimus laptops). So Unity3D was not available and it defaulted to Unity2D (on Vesa drivers, I guess).

Solution: removed nvidia packages (I guess nvidia-current was the critical thing in my system) and xserver-xorg-video-nvidia packages

After reboot, Unity3D was allowed and effects were back!

---

### Post by bbmak on 2011-10-28
Laptop: Presario 2100 & Portege 2000

When freshly install Ubuntu 11.10 CLI, the screen will go blank on reboot. I have to press the ctrl, alt, fn, F2 to get to terminal. I hope in the future such bug will not happen because it is CLI mode. The GUI mode is okay.

---

### Post by gamblor01 on 2011-10-29
I didn't have this problem on any of my systems but my dad's laptop wouldn't do anything related to wireless when I installed 11.10.  Forgive me, this was like a week ago when I did this so I don't remember all of the details exactly.

I checked in the networking applet (on the top menu bar in Unity) and both network and wireless were enabled but it didn't detect any networks and didn't have an ip address when I checked with ifconfig.

I then tried running "sudo ifconfig up wlan0" and I don't remember the exact error message that it printed but it led me to realize that the device was disabled.  There is no hardware kill switch for the wireless card on this laptop so I simply used rfkill to unblock all devices.  I didn't check the man page just now but I think this is the syntax?

```

sudo rfkill unblock all

```

After unblocking all devices the wireless card began working fine and has been stable ever since.

---

### Post by scicode on 2011-10-30
I had some very serious problems with lightdm:
First of all I **could not connect to any networks** anymore other than the wireless networks I had already configured before with the network manager. I made my wired network work again by editing /etc/network/interfaces
```
sudo vim /etc/network/interfaces
```
adding 
```
auto eth0
iface eth0 inet dhcp
```
then restarting the network manually
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

the network manager only said
```
no network devices available
```

I also played around with /etc/dbus-1/system.d/NetworkManager.conf
set some entries (I do not remember which though because i ended up setting all) to **allow** I was able to see wireless networks again. Though I could not connect to them :(

Then I was **unable to mount usb devices**, whenever I plugged a usb device it said
```
Unable to mount USB
Not Authorized

```

Also I recognized that updates showed up but I was **not able to install the updates** with the update manager, I was able to install them in the shell though
```
sudo apt-get upgrade
```

Other problems I remember: hibernate disappeared/shutdown menu incomplete/..., battery status was strange, shutdown did not work properly (stalled during the process and only finished if I pressed the power button one more time), last but not least lightdm was at 100% cpu in the last session before I found my solution

**[COLOR="#ff0000"]FINAL SOLUTION [/COLOR]**that fixed all problems:

After looking around for quite a while most hints pointed to lightdm and after going to the shell and starting
```
sudo dpkg-reconfigure lightdm
```
and setting it to use gdm
everyting works again :D

---

### Post by Topazkitty on 2011-10-30
Does anyone know how to solve the iso bug with DVDstyler for 11.10 I am unable to render dvds now with segmentation faults.

Terminal code:

amanda@Amanda-1525:~$ dvdstyler

(dvdstyler:13134): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:13134): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:13134): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:13134): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[ac3 @ 0x1759a60] max_analyze_duration reached
[ac3 @ 0x1759a60] Estimating duration from bitrate, this may be inaccurate
[ac3 @ 0x22ab8a0] max_analyze_duration reached
[ac3 @ 0x22ab8a0] Estimating duration from bitrate, this may be inaccurate
Output #0, mpeg2video, to '/tmp/dvd-tmp/menu1-0.mpg_bg.m2v':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
[mpeg2video @ 0x22abe00] rc buffer underflow
[mpegvideo @ 0x14a1c60] max_analyze_duration reached
[mpegvideo @ 0x14a1c60] Estimating duration from bitrate, this may be inaccurate
[ac3 @ 0x14a1c60] max_analyze_duration reached
[ac3 @ 0x14a1c60] Estimating duration from bitrate, this may be inaccurate
Segmentation fault
amanda@Amanda-1525:~$

---

### Post by inameiname on 2011-11-01
For those who use Nautilus Actions, you may or may not know that there is an error with the latest 'nautilus-actions' package in the official Oneiric repos (version 3.1.2). The error is mentioned in the bug reports below, causing the 'nautilus-actions-config-tool' to not open. 

[https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/818987](https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/818987)
[https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/820197](https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/820197)

Anyway, I have been able to make a Debian package that does work in Oneiric. It is the latest version, 3.1.4. So far so good on my machines. So should be fine for you as well. Of course, use at your own risk. 

To note, unfortunately the import/export of made nautilus actions doesn't seem to work. I am not sure why. But other than that, it works great. So, until an actual working version lands in the repos, this beats having a fully broken package.

[http://www.2shared.com/file/F3ouEEEN/nautilus-actions_314-1inameina.html](http://www.2shared.com/file/F3ouEEEN/nautilus-actions_314-1inameina.html)

---

### Post by AJuri on 2011-11-01
hy , i cant instal it , it's says :
     
              An error accurred :
      
             unsubscriptable object

                for more information , pllease see the log file :

  c/users/user ..... what i do? please help im new

---

### Post by inameiname on 2011-11-01
> **AJuri said:**
> hy , i cant instal it , it's says :
     
              An error accurred :
      
             unsubscriptable object

                for more information , pllease see the log file :

  c/users/user ..... what i do? please help im new


What did you get the error from? Do you mean the link about Nautilus Actions that I had just posted? If so, what is the error, and where/when does it happen?

---

### Post by u2nTu on 2011-11-02
This Compiz Configuration Settings Manager (ccsm)-related disturbance happened to me a few days ago and I wanted to post the quick fix for others who may be stricken with it.

Symptom:
Unity Launcher and Panel disappear after logout or reboot following use of ccsm

**_[COLOR=Red]DON'T[/COLOR]_:**

[LIST]
[*]Panic
[*]Get angry and uninstall 10.11
[*]Uninstall ccsm (most important)
[/LIST]

**_[COLOR=DarkGreen]DO[/COLOR]_:**

[LIST]
[*]Ctrl-alt-t to open a terminal
[*]Run 'ccsm' again
[*]Navigate to Preferences
[*]See that Profile is 'Default' (If gibberish, pick the other one.)
[*]Be sure Backend is GConf Configuration Backend (not Flat File)
[*]Goto Plugin List tab and uncheck 'Automatic pulgin sorting' and confirm
[*]Under 'Disabled Plugins', pick 'unityshell'
[*]Hit right-arrow to move it over to 'Enabled Plugins' column
[*]Exit ccsm
[/LIST]
After a logout or reboot, Unity should be back.

It is known that ccsm is currently buggy, but most features do work. My first reaction after the experience ("No such bug-riddled program shall remain on my system.") was to uninstall it. It's now back and I look forward to updates fixing it.

---

### Post by Wbbswonder on 2011-11-02
Many users are experiencing no headphone output. Internal speaker works until headphone plugged in and then neither work. 

I have put in a bug. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882170](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/882170)

Please go to the bug and record it affects you, then there is a slim chance it will get fixed. 

As a work around Go to Sound settings>hardware>profile change from Analogue Stereo Duplex input to Analogue input and back again to Analogue Stereo Duplex and now it works until headphones unplugged and plugged back in. I have not tested whether this solves the same microphone problem.

---

### Post by vinay_wagh on 2011-11-03
Many users have reported missing "Shutdown button". 

I was able to retrieve the same by (re?)installing indicator-session
```
 sudo apt-get install indicator-session 
``` Hope this helps.

BY the way is this package not in the list of "default" installed on 11.10? I had the same installed on my 11.04 but went missing during the upgrade...

-- VInay

---

### Post by inameiname on 2011-11-03
> **vinay_wagh said:**
> Many users have reported missing "Shutdown button". 

I was able to retrieve the same by (re?)installing indicator-session
```
 sudo apt-get install indicator-session 
``` Hope this helps.

BY the way is this package not in the list of "default" installed on 11.10? I had the same installed on my 11.04 but went missing during the upgrade...

-- VInay


If you are referring to the missing shutdown button in Gnome-Shell, you can also fix that by installing gnome-shell-extensions-alternative-status-menu. Most distros have this in the repos (although, I do not know if Ubuntu does, I just use WebUpd8 GNOME3 PPA's version). Here is info about it (note, not Ubuntu-specific, but should show you what this is).

[http://mixeduperic.com/linux/how-to-add-the-shutdown-option-to-the-gnome-3-status-menu.html](http://mixeduperic.com/linux/how-to-add-the-shutdown-option-to-the-gnome-3-status-menu.html)

So to install it, just:

```

sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-alternative-status-menu

```


Also, I do not believe indicator-applet-session is in the official 11.10 repo (at least not with the Gnome Classic/Fallback session). However, it was recently ported by Jason Contito Gnome3. Check this link out:

[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

```

sudo add-apt-repository ppa:jconti/gnome3 
sudo apt-get update 
sudo apt-get install indicator-applet indicator-applet-appmenu indicator-applet-complete indicator-applet-session

```

---

### Post by philinux on 2011-11-07
If you experience this i.e no drum roll at login and no sound at desktop then it's this bug.

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/310199](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/310199)

I know it looks old and it's at fix released but it affects oneiric.

Post #4 has a workaround if you need it.

If it affects you click the affects me linky.

---

### Post by sandyd on 2011-11-08
Watch out if your using LUKS LVM2 on an alternate installer. Bug is still here and will make it look like your computer died in the middle of booting.

[https://bugs.launchpad.net/ubuntu/oneiric/+source/grub2/+bug/745960](https://bugs.launchpad.net/ubuntu/oneiric/+source/grub2/+bug/745960)

Might only affect users using RAID, but its a bit unclear ATM.

---

### Post by BinaryMn on 2011-11-08
I've been logged out two times in 30 minutes without any warning. No errors in any log files. My screen goes black and I see a bunch of text related to my X server starting back up (it's almost like GDM dies and restarts) and then I'm back at the login screen.

Both times, I've been actively using Firefox, reading a few different things, but both times, I was browsing two different sites and doing nothing specific that would explain this.

Never had this with 11.04. I've only experienced this with 11.10 and once or twice over the past few weeks, but nothing this frequent. Are there any fixes?

---

### Post by linuxuser12345 on 2011-11-08
Has the battery life issue been fixed yet?

---

### Post by cloyd on 2011-11-09
I had a problem with slow wireless on an Intel WiFi Link 5100 card. I found the solution here:
[http://ubuntuforums.org/showthread.php?t=1874668&page=2](http://ubuntuforums.org/showthread.php?t=1874668&page=2)

I'll quote the relevant paragraph here:
"**Atheros wireless drivers:** This one seems to be haunting  Linux.  For older type cards (lspci outputs "Intel Corporation Ultimate N  WiFi  Link 5300") it seems the full series of Oneiric alphas, and betas  so  far, has a regression as far as cryptography in the "iwlagn" driver   goes. To work around it and get decent wifi speed again, add "options   iwlagn swcrypto=1" to /etc/modprobe.d/iwlagn.conf . For newer cards, add   "options ath9k nohwcrypt=1" if you're having really slow wifi.   Hopefully these will be nailed (again) before the final Oneiric  release."

Note that the passage starts talking about Atheros drivers, but then talks about intel drivers.

I had to create the config file . . . it did not exist in  /etc/modprobe.d. This one line is the content of the config file. Also  had to start gedit with sudo because couldn't save the file without  sudo.

Later, another user offered a slightly different fix by adding the same line
     
     iwlagn swcrypto=1 
 
 to another file that already existed (etc/modules) rather than creating a new file ( /etc/modprobe.d/iwlagn.conf) which didn't exist on my machine.

The original thread is here
[http://ubuntuforums.org/showthread.php?t=1874668&page=2](http://ubuntuforums.org/showthread.php?t=1874668&page=2)
but I think this is all the relevant information. Hope this is helpful.

---

### Post by taddygrrr on 2011-11-09
I've had this problem when I upgraded, and now when I updated. This fix is specific to ATI cards:
[http://ubuntuforums.org/showthread.php?t=1855750](http://ubuntuforums.org/showthread.php?t=1855750)

---

### Post by ACGilbert on 2011-11-09
> **cariboo907 said:**
> We came up with a solution to the problem of not being able to login, in the Oneiric testing  sub-forum try Ctrl-Alt-F1 to get  to a console, then enter the following commands:

```
whoami (make sure you're logged in with the same account that is trying to login on lightdm)
sudo service lightdm stop
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm start
```
Thank you cariboo907.
I was finally able to log in following your advice in post #22.
AC

---

### Post by quequotion on 2011-11-13
This bug is ancient, and has been reported "fixed" here and there, but the issue has actually never been dealt with properly.

If you try to **dpkg-reconfigure -a** it will eventually stop with the message "*dpkg-maintscript-helper: error: couldn't identify the package*".

Notably this happens with **cron** and very few users have gotten past this point.

The solution/workaround is to edit files in **/var/lib/dpkg/info/**

The files are ***package*.postinst**, ***package*.preinst**, ***package*.postrm**, and ***package*.prerm** where *package* is the name of the package installed by apt. Not every package has all four files.

ie, for **cron** edit **/var/lib/dpkg/info/*cron*.postinst** etc.

After the line ```
set -e
``` add ```
export DPKG_MAINTSCRIPT_NAME=*scriptname*
``` where *scriptname* is postinst, preinst, postrm, or prerm (matched to the end of the filename)

Find the line ```
dpkg-maintscript-helper rm_conffile */path/to/conffile* "*packageversion*" -- "$@"
```

After "*packageversion*" add the package name like ```
dpkg-maintscript-helper rm_conffile */path/to/conffile* "*packageversion*" *packagename* -- "$@"
```

So for **cron**, **/var/lib/dpkg/info/cron.postinst** will change from: ```
#!/bin/sh
set -e

# Copy existing allow/deny files
crondir="/var/spool/cron"
pausemessage="F"
for fname in allow deny ; do
    if [ -f $crondir/$fname ] ; then
	if [ ! -f $/etc/cron.$fname ] ; then
	    mv $crondir/$fname /etc/cron.$fname
	    echo " "
	    echo "Moving $crondir/$fname to /etc/cron.$fname to comply with Debian policy"
	    pausemessage="T"
	else
	    echo " "
	    echo "Warning:"
	    echo "Both $crondir/$fname and /etc/cron.$fname exist -- cron will"
	    echo "use /etc/cron.$fname"
	    pausemessage="T"
	fi
    fi
done

# Conffile has become obsolete
dpkg-maintscript-helper rm_conffile /etc/cron.monthly/standard "3.0pl1-113" -- "$@"
```
to: ```
#!/bin/sh
set -e
**export DPKG_MAINTSCRIPT_NAME=postinst**
# Copy existing allow/deny files
crondir="/var/spool/cron"
pausemessage="F"
for fname in allow deny ; do
    if [ -f $crondir/$fname ] ; then
	if [ ! -f $/etc/cron.$fname ] ; then
	    mv $crondir/$fname /etc/cron.$fname
	    echo " "
	    echo "Moving $crondir/$fname to /etc/cron.$fname to comply with Debian policy"
	    pausemessage="T"
	else
	    echo " "
	    echo "Warning:"
	    echo "Both $crondir/$fname and /etc/cron.$fname exist -- cron will"
	    echo "use /etc/cron.$fname"
	    pausemessage="T"
	fi
    fi
done

# Conffile has become obsolete
dpkg-maintscript-helper rm_conffile /etc/cron.monthly/standard "3.0pl1-113" **cron** -- "$@"
```

I had to do this for several packages, including **cron**, **gnome-menus**, **lib32asound2** and **libgphoto**. There may be more packages with the same problem.

Note that **kbd** has a similar, but more complicated problem. I worked around it by commenting out the **dpkg-maintscript-helper** lines (probably not a great idea). In the case of **kbd**, this line is missing both the package version and the package name. Because I don't fully understand what to do with the package version (sometimes it's the current version but other times it's an obsolete version), I didn't try to fix this myself.

I could not get past **libreoffice-common**. This package also has a similar error, but my fix does not work. **libreoffice-common** wants both the **DPKG_MAINTSCRIPT_NAME** and **DPKG_MAINTSCRIPT_PACKAGE** variables declared. I tried to export both, but continued to get the same error.

I am a little confused as to why this bug persists. My fix is based on some old reports in debian's bugtracker.

At least one of the old reports for bugs against dpkg-reconfigure claims that it is fixed (in debian).

There are not bug reports against the affected packages (as far as I could google).

Perhaps there is some confusion as to whether this is a bug in dpkg-reconfigure, failure of packagers to use proper syntax, or failure of dpkg developers to specify a proper syntax.

---

### Post by mentat5kyu on 2011-11-21
I have 2 machines with ubuntu, with a HP Photosmart D110. I don't know when, but this month both stopped printing.

All I have to do for them to come back to work is to restart cups. Both were fresh oneiric installs. All I did were the updates from update manager.

---

### Post by DrMilo on 2011-11-21
> **howefield said:**
> In terminal use the commands..

```
cd /etc/xdg/autostart/
```

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Startup applications should now show up.

Thank you! Although why that should be necessary I won't dwell on...

---

### Post by SushiAddiction on 2011-11-21
Disappearing / Missing window title bar
This happens intermittently when resizing windows. It's been there since 11.04 $#!% 
Alt+F2
```
gtk-window-decorator --replace
```You wan't to run this with a desktop launcher but "create launcher" does not exist $#!%

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```EDIT> I can reproduce the Disappearing Window Title Bar by using SMPlayer (but not limited too)EDIT>> GIMP does it too in a different way.
open SMPlayer > Maximise Window > Then double click on video area to switch to full screen and BAM  Window Title Bar Disappears.

I'm a little brain damaged after some vaccinations 4 years ago. Lots of cognitive problems. Can someone report this to the proper place for me or if not possible, point me in the right direction. Thanks

---

### Post by matiasw on 2011-11-22
> **webfiend said:**
> **Issue:** Pressing "Enter" occasionally results in the pointer freezing until I reboot.
**Workaround:** System Settings -> Mouse and Touchpad -> uncheck "Disable touchpad while typing"
I don't know if it's the best workaround available, but my pointer hasn't frozen since I did that.

Thanks - and for those with a frozen pointer, this fix:
```
synclient Touchpadoff=0
```
from [a related bug report]("https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/868400") worked for me. :KS

---

### Post by kanhiya on 2011-11-26
How many of u have tested bluetooth on UBuntu 11.10, i have tested the same on many laptops of my friends , all of them having same problem, Bluetooth doesn't work any more. Detect device & add them successfully but using them is a Headache. No mobile is working, send or receive files.

here is temporary fix.

ubuntu.igameilive.com/2011/11/temporary-problematic-bluetooth-fix-in.html

---

### Post by StevenStip on 2011-11-29
hi, I'm having this problem with my sound settings.
when I plug in my headphones to my laptop: cr500 the output connector(that's what it's called in the sound settings) setting changes to headphone and I'm not able to get any output anymore, this was no problem in the earlier releases.
A workaround is to just go to settings and change it back to speakers(where it works fine, using headphone jack if something is plugged in and speakers if not) everytime you plug in the headphones.

---

### Post by philinux on 2011-11-29
Inability to customise the unity launcher location.

See link in my Sig to move it to the bottom. Please read all the caveats in the link.
It requires adding a ppa.

---

### Post by yoramdavid on 2011-12-06
I am not sure if this thread is just for system bugs or also for packages.

Anyway, I assume an application is made to function and since gshudown does not seem to do anything (it never did for me in any distribution I used it with) without changing parameters.

**Problem**:
gshutdown or just log off instead of shuting down.

**Solution**:
Change the settings of gshutdown as follows:
Edit-Preferences
Select customized command and under shutdown enter:
shutdown -h now

to reboot:
reboot

to logoff:
/usr/bin/gnome-session-save --kill --silent

Also, select "execute a command before the action" and type:
nautilus -q

If after that you still find it does not work (it was my case), you must run it as root. I solved that by adding```
gksu
```before the link to the application. I used alacarte to do that. It asks your password to run gshutdown with this...

---

### Post by pretty_whistle on 2011-12-08
Sometimes Ubuntu 11.10 with Unity doesn't resume after suspending it.

Here's an askubuntu about it:
[http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep](http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep)

Workaround:
 

> You can resume ok if you enter your password in as though you got the login screen (even if you have automatic login enabled).

Apparently the login in screen is there but is "out of view".  Just treat the screen you're seeing as a click-through by assuming the cursor is in the password field.  Put the password in and it'll resume.Solves the problem of having to do a hard shutdown and startup to reach the desktop.

---

### Post by Backzlider on 2011-12-12
I had the problem of not being able to log in.

I tried all the variations of deleting .Xauthority, but to no avail.

I then looked at the .xsession-errors file and it showed that there was a syntax error in .profile.

How this can be is beyond me as this is a fresh install of Ubuntu.

Help thread posted here:  [http://ubuntuforums.org/showthread.php?t=1894111](http://ubuntuforums.org/showthread.php?t=1894111)

---

### Post by sozo on 2011-12-12
**HTTPS Hotmail,Facebook,Gmail login solved.** 			 			 			 		   		 		 		Hello everyone this is my first and hopefully a very helpful post.

I have struggled for over a year now trying to get Ubuntu to log into my  Hotmail, Facebook, Ebay, Gmail accounts etc, through my web browser,  while connecting via my wireless network. My connections to these were  just freezing and would not be able to complete the connection,and so,  not enabling them to log in, regardless of which browser i was using.  This would continue until a time out error was shown.

Now after constant reading and searching i have found a permanent  solution for me, all my accounts now log in in seconds, and no more time  outs. I was reading on my 3UK mobile network support docs and noticed  it mentioned about the possibility of the MTU settings being too high in  my connection settings, and this causing possible connection problems.  so i tried it and it has worked.

So onto what i did.

Apparently the default is set allot of the time too high in the network settings.

They recommended MTU settings starting at 1300 and then working your way lower until successful connection is achieved

So in Ubuntu (NOTE * my current Ubuntu is 11.10 but the same issue  occured in all versions i installed) Where you have your network  connections icon at the top right of the Ubuntu screen, click that then  go down to edit connections.

Then select wireless connections. At the bottom is MTU. This was  originally set to automatic. So i changed this setting to the first one  recommended by my isp. MTU 1300

That is all i did. I saved this available for all users. rebooted the  laptop. opened the browser ( default Ubuntu 11.10 Firefox) and hey  presto, all is solved.

So it would seem that all this time nearly 1 1/2 yrs, ive been  struggling with this, all i had to do was reduce the MTU to solve the  issue.

Believe me i have tried everything ese, firewalls etc and nothing else  solved the problem. Im not highly technical and do not fully understand  the implications of why this has worked but it has. So here is my post  to tell you of my solution to my issue.

Just start at 1300 and work your way down until you get your connection,  also lowering the mtu seems to have made general browsing a smoother  experience too, with pages loading a little faster.

ok so thats it. Have a go and see if it resolves your issue if your having the same problems i did.

My first post, and i hope its been a helpful one. i will no doubt post  again if i have a positive contribution to make in the future.

Take care all.

Regards
Sozo

---

### Post by drs305 on 2011-12-12
> **sozo said:**
> 

My first post, and i hope its been a helpful one. i will no doubt post  again if i have a positive contribution to make in the future.

Welcome to the Ubuntu Forums.  :-)

Congratulations on figuring out your dilemma and for posting to help other forumites.

---

### Post by SushiAddiction on 2011-12-19
Jockey - "Addional Drivers" does not properly install "ATI/AMD proprietary FGLRX graphics driver (post-release update)"

solution
```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```got this from [http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem](http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem)

After you update, Jockey/"Addional Drivers" will not show you are using the FGLRX graphics driver but don't worry you are.

The advantage to this is that gnome 3 will almost work with your ATI video. You will now be able to read the menu text that did not work before but the screen has glitches now and then. At least now you can test out gnome 3.

---

### Post by IanW on 2011-12-21
Firefox - Disappearing menu

I'm not sure if this applies to fresh installs, as I only recently updated from Maverick to Oneiric.

If Firefox is closed & later reopened, the new instance will not show any menu in the top bar.

To fix this:-
1: Install & run CCSM
```
sudo apt-get install compizconfig-settings-manager
ccsm
```
2: Click on "Utility"
3: Enable then click on the "Workarounds" plugin
4: Select "Firefox Menu Fix"
5: Close CCSM

Given that Firefox is Ubuntu's default browser, I am surprised that this fix is not enabled by default.
(I am currently unable to check for or file a bug against this as Launchpad's search is timing out for me)

---

### Post by Superdude_123 on 2011-12-29
When using LIRC, it seems that there are two instances of IR, one from the kernel and one from LIRC. The work around was to make LIRC only respond to all IR commands. The fix was found [http://ubuntuforums.org/showthread.php?p=11525835](http://ubuntuforums.org/showthread.php?p=11525835) and the fix it self was to run:

sudo sed -i '$i echo lirc > /sys/class/rc/rc0/protocols' /etc/rc.local

---

### Post by silverhaze06 on 2012-01-07
I just bought a new Hp Pavilion G6-1c58dx and installed Ubuntu 11.10 AMD-64-Bit. The first thing I encountered was the screen going blank once it got to the splash and login screens. 

I plugged in my laptop to my tv via the HDMI port and everything was showing up on there. Once I logged in, the additional drivders window poped up and I activated the ATI/AMD Proprietary FGLRX Graphics Driver. Once that was activated my screen started working immediately.


Other than that I temporarily had a problem with usb mice all of a sudden not working and causing pretty weird problems (they worked fine before). When one was inserted during bootup, it was making the screen go blank when splash screen is supposed to come up.  But it would come back on if I quickly pressed the power button. Then the system would freeze after typing in only a few letters of my password. If one wasnt in it would boot up just fine. But once I plugged in a mouse after logging in, it still wouldent work, and after that it would not recognize any other type of usb devices for the rest of the session.

I wasn't able to fix this and and the next day I was about to re-install everything when I figured I would try to see if the mouse would work one last time since any other type of usb device would work fine and not cause problems. It didn't work again. So I plugged it back in one last time and it seems to have magically fixed it's self, because right when I was about to give up it started working again and stopped causing the problems at startup. Luckily it hasn't done it since, but I would still like to know why it was doing that in the first place.

More details about that here... [http://ubuntuforums.org/showthread.php?t=1904699]("http://ubuntuforums.org/showthread.php?t=1904699")

---

### Post by silverhaze06 on 2012-01-09
> **silverhaze06 said:**
> I just bought a new Hp Pavilion G6-1c58dx and installed Ubuntu 11.10 AMD-64-Bit. The first thing I encountered was the screen going blank once it got to the splash and login screens. 

I plugged in my laptop to my tv via the HDMI port and everything was showing up on there. Once I logged in, the additional drivders window poped up and I activated the ATI/AMD Proprietary FGLRX Graphics Driver. Once that was activated my screen started working immediately.


Other than that I temporarily had a problem with usb mice all of a sudden not working and causing pretty weird problems (they worked fine before). When one was inserted during bootup, it was making the screen go blank when splash screen is supposed to come up.  But it would come back on if I quickly pressed the power button. Then the system would freeze after typing in only a few letters of my password. If one wasnt in it would boot up just fine. But once I plugged in a mouse after logging in, it still wouldent work, and after that it would not recognize any other type of usb devices for the rest of the session.

I wasn't able to fix this and and the next day I was about to re-install everything when I figured I would try to see if the mouse would work one last time since any other type of usb device would work fine and not cause problems. It didn't work again. So I plugged it back in one last time and it seems to have magically fixed it's self, because right when I was about to give up it started working again and stopped causing the problems at startup. Luckily it hasn't done it since, but I would still like to know why it was doing that in the first place.

More details about that here... [http://ubuntuforums.org/showthread.php?t=1904699]("http://ubuntuforums.org/showthread.php?t=1904699")


Also, once the driver for my graphics card was activated, it wasnt performing that great. So anyone with AMD based processors/graphics cards should follow this thread to get the most out of their hardware. After I did, everything looks a lot better than before. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

---

### Post by vaslat29 on 2012-01-09
When I am working with Firefox or Chrome, I am thrown out suddenly back to the log-in screen. I have re-installed 11.04 and it now works fine.

---

### Post by D0Z on 2012-01-17
Xubuntu 11.10

**1. Hardware**
	
	_1.1	Logitech Dinovo keyboard._

		The Logitech Dinovo Edge keyboard does not work on Xubuntu 11.10 right out of the box. 		This problem has occured on previous releases of (X)Ubuntu. 
Hook up another (usb) keyboard to fix this problem as following;

		Edit the file:* /lib/udev/rules.d/62-bluez-hid2hci.rules*
		Search for the following line and edit. Use: *“sudo leafpad /lib/udev/rules.d/62-bluez-			hid2hci.rule”* to open the file as root.

		[I]# Logitech devices
		KERNEL=="hiddev*", ATTRS{idVendor}==.............
		KERNEL=="hidraw*", ATTRS{idVendor}==.............

		Save file and reboot.[/I]


**2. Operating system**

	_2.1	Thunar slow file opening fix_

		*“sudo leafpad  /usr/share/gvfs/mounts/smb-browse.mount” *

		Change automount to false, so the result looks like this.

			[I][Mount]
			Type=smb-network;smb-server
			Exec=/usr/lib/gvfs/gvfsd-smb-browse
			DBusName=org.gtk.vfs.mountpoint.smb_browse
			AutoMount=false
			Scheme=smb[/I]

		Save file, log out and log back in.


	_2.2	Xubuntu keyring issue_

		Browse to: *home /.gnome2/keyrings*. Delete the two existing files, log out and log back in.

---

### Post by dsevil on 2012-01-27
If you're seeing warnings like these

```

** WARNING: There appears to be one or more degraded RAID devices **
<snip>
md1 : inactive sdb1[1](S)
        976759936 blocks

```

your system may actually be booting too fast, especially if your root is on an SSD or something.  You'll know this is the case if you decide to answer yes when asked if you want to boot with the "degraded" array, wait a few seconds, log in, cat /proc/mdstat, and see the [UU] indicating everything's fine now:

```

md1 : active raid1 sdc1[0] sdb1[1]
      976759936 blocks [2/2] [UU]

```

If that's your problem, here's your workaround:

```

echo -e '#!/bin/sh\nsleep 10' >/etc/initramfs-tools/scripts/local-top/easy-there-horsey
update-initramfs -u

```

(you can make that script a little smarter if you want, but that'll work just fine)

---

### Post by bogan on 2012-02-05
**Re: Failure To Recover From Suspend/Hibernation or Loss Of WiFi Internet Connection**.

There are many Threads/Posts reporting the failure to recover, or the loss of Internet connection after resuming from Suspend or Hibernation.

Hence requiring a re-start or re-boot, losing any unsaved data, and having to re-run any software; thus defeating the whole purpose.

In the case of my two Desktop computers, each with 11.10 and 10.04 installed, although they do not recover with Mouse movement or Mouse Clicks, they nearly always respond to an 'Enter' keystroke.

Usually, though by no means always, the Realtek RTL8191S Wlan Wireless Adapter retains its connection on recovering.

When it does not, I have found that plugging in an USB Wlan Dongle, that I know works with the installed drivers, triggers the Network Manager into re-scanning, recognizing the Network and both Adapters, and re-makes the connection.

Thus saving having to do a Power-off re-boot.

Chao!, bogan.

---

### Post by STA2034 on 2012-02-11
[B]White screen with vertical black lines during boot up - normal log in screen appears 
[/B] 
**Symptoms:**
1.  I was doing a first time install of Ubuntu.  I had never used Ubuntu prior to this, other than running on the CD.  No other OS was installed on the computer.

2.  The install went well, and everything displayed properly, until final boot into the system.  After the install finished, and I did a final boot, I had an unreadable screen.  The screen was white, with vertical black lines, and resembled something like a bar code.

3.  After the boot process, the login screen appeared, and I was able to log in and use the system.  Pressing the escape key, during boot, to close the splash screen, did not help.   There was screen activity, but the display was still corrupted.

4.  Several searches on Google, and in the Ubuntu forums led me to trying various fixes, none of which solved the issue.  These fixes included, but were not limited to:

a.  Trying various nVidia drivers, from older previous versions, through to the latest Beta version.

b.  Disabling the splash screen.

c.  Adding nomodeset to the Grub configuration.

d.  There were several other "fixes" that did not work, and seemed to be too complicated for beginners and newbies to understand.

**Solution:**
The solution turned out to be quite simple, really!

The screen I was using would not sync properly with the resolution being used by grub on boot!  My monitor and video card did not like anything that was too low or too high a resolution.

**How To Fix:**
1.  Open a terminal and edit the grub boot menu using the command:
[INDENT] [SIZE=1]gksudo gedit /etc/default/grub[/SIZE]
[/INDENT]2.  Add or change to the following lines to the menu (Some may already be there)
[INDENT] [SIZE=1]# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

GRUB_GFXMODE=1024x768
[/SIZE][/INDENT]3.  Save the file and exit the editor.

4.  Update the grub boot loader with the saved file using the command:
[INDENT] [SIZE=1]sudo update-grub[/SIZE]
[/INDENT]5.  Reboot the system.  The system should now boot in a graphic mode compatible with your video card and monitor.

**NOTE:**  You may have to try several different modes, to find one you prefer.  I selected the lowest possible one that worked, as higher resolutions produced a very fine and hard to read print.

Cheers!
STA2034

**My System:**
Ubuntu 11.10 New Install (First time using Ubuntu - No other OS installed)
Asus A8N-E Main Board
AMD Athlon 64x2 Dual Core 3800+
4 GB RAM
nVidia gForce 6600 w/1 GB RAM
Samsung SyncMaster 226bw Monitor

---

### Post by kohoutek1 on 2012-02-17
In Gnome 3.2.1 on Oneiric, an unwanted desktop menubar may appear under the shell panel. This menubar is a function of Nautilus, but it is incompatible with shell themes, especially those with translucent panels. If you are using the default Adwaita theme, the menubar may appear as a white line under the shell panel. This menubar also results in the off-setting of the desktop background. The menubar cannot be turned off or modified with mouse or keyboard (i.e., "Alt+right click" does not work).

One easy workaround for this bug, often offered in the forums, is to disable Nautilus by opening "Advanced Settings" (GNOME Tweak Tool), clicking on "Desktop," and unchecking "Have the file manager handle the desktop." However, this workaround will also leave you unable to use the desktop for folders or documents, since it disables the link between the desktop and the user's "Home/Desktop" folder.

A better workaround is to remove any of the packages that may have included the menubar, with the following command: 

```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```

After removal of all appmenu packages, the menubar will be gone. You can re-check "Have the file manager handle the desktop" and place folders or documents there as normal.

---

### Post by viperdvman on 2012-02-23
> **kohoutek1 said:**
> 

A better workaround is to remove any of the packages that may have included the menubar, with the following command: 

```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```After removal of all appmenu packages, the menubar will be gone. You can re-check "Have the file manager handle the desktop" and place folders or documents there as normal.

I'm a bit skeptical of this. Does it end up killing the Unity appmenu too? Or if not, then not moving the app menus from the window to the menubar?

---

### Post by Dreamer Fithp Apprentice on 2012-02-25
Print Screen key quit working for me.

The work-around isn't rocket science. Install "shutter" and you'll have a clickable icon on your panel and an entry in the applications menu to do the same thing.

---

### Post by Helen McCall on 2012-03-18
> **drs305 said:**
> **Synaptic fails with 'out_of_range' or 'SIGBART' error**

If Synaptic (not installed by default) won't run and generates one of the above messages, disabling the Accessibility settings appears to fix it:
[LIST]
[*]Open Universal Access (Dash/Home > Universal Access; or System Settings (upper right) > Universal Access)
[*]Seeing tab > Screen Reader; Off
[/LIST]


You do not have to disable anything. Just toggle the settings on and off or vice versa. This did the trick for me.

---

### Post by Curious00 on 2012-03-18
I've experienced an odd problem where every time I check or uncheck the box next to a plugin in CCSM, Compiz and Unity will crash. Sometimes the desktop recovers, but most often it won't. It appears to be a glitch in the Unity Compiz plugin, itself.

This is such a critical problem - that because my naivety got me into a pickle while trying to address the problem, I found a need to actually wipe and reinstall Ubuntu.

Here is my advice (thus far) for those who are in my shoes and who want to make CCSM work for them:


____

If you have the screen flash and Compiz restart (or not) every time you load or unload a plugin (clear or unclear a checkbox on the main page), try this:
[LIST=1]

[*] First of all, before you get your feet wet, you'll want to be able to recover the default Compiz settings (or whichever ones you have in there currently) in an emergency. To prepare for this, go to the "Preferences" (orange text on the left), and export your profile somewhere you'll be able to find it again. When it asks whether you want to "skip default options while exporting your profile", answer no. Then, you can simply import the settings file back into Compiz whenever you need to.

[*] Secondly, you're going to need to be able to rescue your desktop quickly if it has a tendency to crash every time you load and unload a plugin. Go to the Ubuntu system settings (the gear icon in the Unity taskbar). Choose "Keyboard Layout", press the "Options..." button, find where it says "Key sequence to kill the X server", and check "Control + Alt + Backspace." This means that whenever your system hangs, all you have to do is press that key combination in order to automatically log off. Then you can log back in without having to reboot your computer. If worse comes to worse, you can also log into Ubuntu classic mode from that screen.

[*] Place a Compiz configuration icon on the desktop so you can quickly access it. Simply drag the icon out of the launcher after you search for "Compiz."

[*] Fourthly, know that the problem with CCSM crashing every time you load or unload a plugin seems to be specific to the Unity plugin. If you go down to the "Desktop" section and  uncheck "Ubuntu Unity Plugin" you will lose your taskbar, and your top bar - however you can then make any adjustments at all within Compiz, and you'll never crash it. Afterwards, you can simply replace that checkmark next to the "Unity" plugin, and you're good to go.
[/LIST]
____

Hopefully, it won't be long before I actually discover a real fix. When I do, I'll post it here.

---

### Post by jonashendrickx on 2012-03-19
Ubuntu 11.10 hangs sometimes on shutdown with a ATI card installed.
I think it is with fglrx drivers.
With radeon drivers I will be stuck at Checking Battery State [OK]

Any fix for this ?

I figured:
[http://ubuntuforums.org/showthread.php?t=808543](http://ubuntuforums.org/showthread.php?t=808543)

I noticed lightdm is not in that file he is talking about. Maybe thats our problem?

---

### Post by gleedadswell on 2012-03-20
Boot to black screen on fresh install of 11.10 on HP Compaq 8200 Elite all-in-one:

I've documented this in more detail here:

[http://ubuntuforums.org/showthread.php?t=1911886]("http://ubuntuforums.org/showthread.php?t=1911886")

and it is also posted as a bug report on launchpad, so I'll just give the quick summary.

The live CD boots to a black screen on this machine.  This can be solved by making a custom USB key with the live CD .iso booted by grub.  Put the "nosplash nomodeset" options into grub.

Then you'll need to modify grub on the new installation on the hard drive to have those same options.  This gives you a system which boots, but has no 3d graphics support, and a few graphics problems even in ubuntu 2d or gnome fallback.  This is easily fixed by upgrading to the linux 3.2 kernel.  At that point everything seems to work like a charm.

---


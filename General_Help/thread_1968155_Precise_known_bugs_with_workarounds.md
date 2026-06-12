---
title: "Precise known bugs with workarounds"
date: 2012-04-28
forum: General Help
---

### Post by CharlesA on 2012-04-28
Please post the bugs you have run into and how you worked around them here.

**Do not post your problems, please raise a support thread.**

Keep in mind, that Linux is infinitely customizable, you do not have to stick with Unity as a desktop environment if you do not want to.

---

### Post by haqking on 2012-04-28
I have posted a workaround thread to the default dnsmasq being hardcoded into networkmanager in 12.04 which leaves users potentially vulnerable to MITM attacks and DNS poisoning especially on open networks where rogue DNS servers could appear.

Thread/workaround here [http://ubuntuforums.org/showthread.php?t=1968061](http://ubuntuforums.org/showthread.php?t=1968061)

It is not needed as a default configuration, it should be provided as a feature if needed.

Though it appears no caching is happening by default, however instructions above are there if needed.

Peace

---

### Post by mendhak on 2012-04-29
Sometimes LightDM (the login screen) won't let you log in. This might happen if you have set a non-default wallpaper.  The login screen will simply say "logging in" and get stuck there.  To get around it,

[LIST=1]
[*]Ctrl Alt F1, login
[*]Run these commands:

```
    sudo apt-get install gdm
    sudo dpkg-reconfigure gdm
```

[*]That installs GDM, and you will need to set it as default in the second command.  
[*]Reboot
[*]Login, set a standard wallpaper (right click desktop)
[*]Run this command to set lightdm back
    ```
sudo dpkg-reconfigure lightdm
```
[*]Reboot
[/LIST]

If that doesn't work and you still get stuck, do a Ctrl+Alt+F1 at the login screen and have a look at the following log files to see what's happening.

```
sudo less /var/log/lightdm/x-0-greeter.log
sudo less /var/log/lightdm/lightdm.log
```

---

### Post by Zukaro on 2012-04-29
Default Ubuntu wallpapers will also become the login screen wallpaper (if used as your desktop wallpaper).  This is a feature, however, it doesn't work with custom wallpapers (which is a bug).  If you're using your own wallpaper it wont appear on the login screen; the way to fix this is to copy it into /usr/share/backgrounds and then set the permissions to read only (set "group" and "other" permissions to read only).

You wont be able to drag the file to the folder as the folder is owned by root, so type "sudo mv /home/username/Pictures/wallpaper.jpg /usr/share/backgrounds" (make sure there's a space between locations); then go to the directory, find the file, right click, go into permissions and change group and other to read only (you're still the owner of the file, which is why you don't need to change permissions through the terminal).

Then to use the wallpaper just select it as your desktop wallpaper and it will also become your login screen wallpaper.

If you want your login screen wallpaper different from your desktop wallpaper download Ubuntu Tweak Tool and follow all the same steps above with the image you want to use instead; then just choose that image in Ubuntu Tweak Tool.




I found out about this bug and the fact the permissions were the issue here:
[https://bugs.launchpad.net/ubuntu-tweak/+bug/888186](https://bugs.launchpad.net/ubuntu-tweak/+bug/888186)

---

### Post by Yathi on 2012-04-30
I believe adobe flashed has been renamed in Precise Pangolin. So you need to install:

```
sudo apt-get install adobe-flashplugin
```


instead of the usual 

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by philinux on 2012-04-30
If you have ambiance as your theme and you right click the desktop, for example, you'll see a light menu rather than dark like Oneiric.

The discussion surrounding this "design decision" is here.

[Bug Report 925895]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895")

The fix if you want it is here.

[Theme fix for Precise]("http://www.omgubuntu.co.uk/2012/04/how-to-revert-to-dark-menus-for-ambiance-theme-in-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29")

---

### Post by Lamukra on 2012-04-30
> **philinux said:**
> If you have ambiance as your theme and you right click the desktop, for example, you'll see a light menu rather than dark like Oneiric.

The discussion surrounding this "design decision" is here.

[Bug Report 925895]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895")

The fix if you want it is here.

[Theme fix for Precise]("http://www.omgubuntu.co.uk/2012/04/how-to-revert-to-dark-menus-for-ambiance-theme-in-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29")

Have you tried to run nautilus with root privileges and see what happens. With me nautilus was behaving very strangely - changing color of window with almost every click :)... or it is normal? Can you try it?

---

### Post by merlinus on 2012-04-30
Did not work for me.  Same light-colored menus and such as with plain old Ambiance theme.  I am using Gnome Classic.

Also, the theme only showed up in the Advanced Settings tool, not System Settings/Appearance.

> **philinux said:**
> If you have ambiance as your theme and you right click the desktop, for example, you'll see a light menu rather than dark like Oneiric.

The discussion surrounding this "design decision" is here.

[Bug Report 925895]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895")

The fix if you want it is here.

[Theme fix for Precise]("http://www.omgubuntu.co.uk/2012/04/how-to-revert-to-dark-menus-for-ambiance-theme-in-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29")

---

### Post by whatthefunk on 2012-04-30
Crap Nvidia driver included on .iso.  Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

Reboot and you should be good to go.

---

### Post by codingman on 2012-04-30
Can anybody back me up on how to fix the ALT-TAB bug in Gnome Classic? Or is this a bug that is in progress of being fixed? I'm not using Gnome Classic until this bug is fixed.

---

### Post by philinux on 2012-05-01
> **Lamukra said:**
> Have you tried to run nautilus with root privileges and see what happens. With me nautilus was behaving very strangely - changing color of window with almost every click :)... or it is normal? Can you try it?

Looks fine here although gksu nautilus does not have a global menu and the drop down menus are light grey with black text. So fine here.

---

### Post by philinux on 2012-05-01
> **merlinus said:**
> Did not work for me.  Same light-colored menus and such as with plain old Ambiance theme.  I am using Gnome Classic.

Also, the theme only showed up in the Advanced Settings tool, not System Settings/Appearance.

Could be gnome classic related.

Like it says use the tweak tool of your choice, they recommend myunity.

System settings appearance does not seem to recognise any custom themes.

---

### Post by bigoten on 2012-05-01
> **codingman said:**
> Can anybody back me up on how to fix the ALT-TAB bug in Gnome Classic? Or is this a bug that is in progress of being fixed? I'm not using Gnome Classic until this bug is fixed.

I agree. This feature is driving me crazy. How can we ALT-TAB among ALL opened applications in ALL workspaces, as we used to?

---

### Post by brad1138 on 2012-05-01
> **whatthefunk said:**
> Crap Nvidia driver included on .iso.  Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

Reboot and you should be good to go.

What does this fix?

---

### Post by codingman on 2012-05-01
> **bigoten said:**
> I agree. This feature is driving me crazy. How can we ALT-TAB among ALL opened applications in ALL workspaces, as we used to?

Hey! Go to CCSM and then enable application switcher,it works quite beautifully,ALT-TAB then shows the Compiz window switcher, but at least it works for now.

Hope this helps

Codingman

---

### Post by whatthefunk on 2012-05-01
> **brad1138 said:**
> What does this fix?

The nvidia drivers that came on the iso dont work with a lot of graphics cards.  This is a way to get the old driver.

---

### Post by jsavga on 2012-05-01
> **bigoten said:**
> I agree. This feature is driving me crazy. How can we ALT-TAB among ALL opened applications in ALL workspaces, as we used to?
Super+W is broke too, showing only applications from current workspace instead of all workspaces. Driving me nuts.

---

### Post by bigoten on 2012-05-02
> **codingman said:**
> Hey! Go to CCSM and then enable application switcher,it works quite beautifully,ALT-TAB then shows the Compiz window switcher, but at least it works for now.

Hope this helps

Codingman

I tried before, it does not work. Perhaps I am doing something wrong. I tried to set up one of the three following options: Application Switcher, Static Application Switcher, and Shift Switcher. I just fail to get the ALT TAB working as I think it should. Did anyone find a specific configuration to solve this issue?

---

### Post by raphifix on 2012-05-02
> **bigoten said:**
> I tried before, it does not work. Perhaps I am doing something wrong. I tried to set up one of the three following options: Application Switcher, Static Application Switcher, and Shift Switcher. I just fail to get the ALT TAB working as I think it should. Did anyone find a specific configuration to solve this issue?

Idk how the key binding is for you, but for me the default is Super+Tab, NOT Alt+Tab.

---

### Post by gunksta on 2012-05-02
There is an open bug regarding external monitors and users of intel graphics. I have a Sandy Bridge processor and I have to be very careful how I plug things in.

If I plug in my USB Hub, External Monitor, etc and then boot the computer, LightDM comes up as expected and then Unity / Gnome Shell goes into a hard freeze upon log-in.

I was intrigued that LightDM worked correctly. So, I tried various window managers and eventually discovered that xfwm from XFCE4 / Xubuntu works just fine and does not trigger this bug. Alternatively, I am able to avoid it by first connecting the external monitor, logging in to Unity and THEN inserting my USB hub with external keyboard, mouse, printer, etc. A small hassle, but everything seems stable.

This problem drove me nuts because I loves my external monitor. Hope it helps someone else. I'm using a Lenovo X220 laptop. I don't know if desktop users are affected by this. YMMV.

---

### Post by dangmc on 2012-05-02
> **whatthefunk said:**
> Crap Nvidia driver included on .iso.  Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

Reboot and you should be good to go.
@whatthefunk-doesn't work for me, tried watching flash movie on firefox, 1st time caused hard freeze, 2nd time caused logout. Back to nouveau.
  desktop:Asus P7P55D-e mobo
          I5-750 cpu
          160 gb hdd (ide)
          8 gb ram
          9800 GT gpu (Nvidia)
          Ubuntu 12.04_amd64
triple boot: Ubuntu 11.10_amd64,Windows 7 Professional, Ubuntu 12.04_amd64 LTS
btw-do you know if it's possible to install Nvidia driver 280.13? This is what I have on Oneiric & works great.

---

### Post by whatthefunk on 2012-05-02
> **dangmc said:**
> @whatthefunk-doesn't work for me, tried watching flash movie on firefox, 1st time caused hard freeze, 2nd time caused logout. Back to nouveau.
  desktop:Asus P7P55D-e mobo
          I5-750 cpu
          160 gb hdd (ide)
          8 gb ram
          9800 GT gpu (Nvidia)
          Ubuntu 12.04_amd64
triple boot: Ubuntu 11.10_amd64,Windows 7 Professional, Ubuntu 12.04_amd64 LTS
btw-do you know if it's possible to install Nvidia driver 280.13? This is what I have on Oneiric & works great.

Sounds like a different issue to me.  I had to install with the alternate iso and boot in recovery mode.  No desktop effect worked, no videos worked, screen resolution was broken etc....

---

### Post by dangmc on 2012-05-02
> **CharlesA said:**
> Please post the bugs you have run into and how you worked around them here.

**Do not post your problems, please raise a support thread.**

Keep in mind, that Linux is infinitely customizable, you do not have to stick with Unity as a desktop environment if you do not want to.
aren't we allowed to respond to suggested workarounds? why was my response to post #9 removed?

---

### Post by dangmc on 2012-05-02
> **whatthefunk said:**
> Sounds like a different issue to me.  I had to install with the alternate iso and boot in recovery mode.  No desktop effect worked, no videos worked, screen resolution was broken etc....
ok- sorry. i didnt look far enough.

---

### Post by CharlesA on 2012-05-02
> **dangmc said:**
> aren't we allowed to respond to suggested workarounds? why was my response to post #9 removed?
Nothing has been removed from what I can see.

As for your issue, have you created a thread about it? It sounds like a different problem entirely.

---

### Post by mihoo on 2012-05-04
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

I have info - version "295.33-0ubuntu1~precise~xup1" for "nvidia-current" does not exist :(

---

### Post by StApnea on 2012-05-04
On my computer, and judging by this bug [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/953089]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/953089") others as well, pressing the super key on an open workspace will not do anything. I think Unity may become flummoxed about which window is on top when switching windows.
Anyway, I've found that using one of the Dash Lens shortcuts (e.g. Super+a, Super+f, Super+m) works fine.

---

### Post by imbjr on 2012-05-04
Devede - no visible menu, generates silent DVD

If you experience these problems, switch over to using mencoder in the application's properties. You will get a proper preview when generated and a working ISO.

Note: this is with Xubuntu, amd64 kernel and the medibuntu repos.

---

### Post by alr1969 on 2012-05-05
Regarding all those .goutputstream-XXXXX showing up in the home folder as per this thread [http://ubuntuforums.org/showthread.php?t=1938825&highlight=goutputstream+files](http://ubuntuforums.org/showthread.php?t=1938825&highlight=goutputstream+files) 

In my case those files would appear after a re-start from a shutdown.  Seems that if I log out before shutting down,  the files do not appear.  I use the terminal to check on them.

Hope this helps.

---

### Post by mathiflip on 2012-05-05
> **bigoten said:**
> I agree. This feature is driving me crazy. How can we ALT-TAB among ALL opened applications in ALL workspaces, as we used to?

very annoying indeed! I fixed it by going to CCSM -> unity plugin and on the tab 'switcher' uncheck the second box before 'Bias alt-tab to prefer........'

Someone already had a solution for the super+w function?

---

### Post by JLF65 on 2012-05-05
Worker blows up if you try to use it with AVFS from the repo. The problem is with AVFS - it has a string operation that triggers Fortify... unfortunately, Foritify isn't very user friendly in that it deliberately crashes programs that trigger it. The idea is that the person runs the program in dbg which catches the crash deliberately caused by Fortify and then traces it back to the string operation that Fortify didn't like. But what it amounts to for the average user is programs which used to work now go BOOM for no apparent reason.

The workaround for this is to recompile avfs from source with Fortify turned off.

Grab the latest source for AVFS.

```
sudo apt-get install build-essential liblzma-dev libfuse-dev
./configure --enable-library
```

in its "Makefile" change:

```
CPPFLAGS =  -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -D_GNU_SOURCE
```

to:

```
CPPFLAGS =  -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_POSIX_PTHREAD_SEMANTICS -D_GNU_SOURCE -D_FORTIFY_SOURCE=0
```

then:

```
make
sudo make install
```

At that point, you can install Worker from the repo and it will work fine.

---

### Post by IanW on 2012-05-05
> **mihoo said:**
> ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

I have info - version "295.33-0ubuntu1~precise~xup1" for "nvidia-current" does not exist :(

Nvidia have just released a new stable driver "295.49" to address the problems with "295.40".

---

### Post by OzzyFrank on 2012-05-05
As odd as it sounds, this DeVeDe-Mencoder "fix" also worked for me. What I mean by that is since I don't usually use DeVeDe for encoding, just the DVD authoring, I wouldn't have thought switching back to Mencoder would have made a difference (since the authoring is handled by DVDAuthor). And nothing appears wrong with FFMPEG, as I actually use that to encode to DVD-compatible files, via tovidGUI.

---

### Post by Paddy Landau on 2012-05-06
> **mendhak said:**
> Sometimes LightDM (the login screen) won't let you log in.> **Zukaro said:**
> Default Ubuntu wallpapers will also become the login screen wallpaper (if used as your desktop wallpaper).  This is a feature, however, it doesn't work with custom wallpapers (which is a bug).
You cannot log in if your home folder is encrypted, because LightDM cannot get hold of the wallpaper. Zukaro's method is a solution to that.

---

### Post by bigoten on 2012-05-08
> **mathiflip said:**
> very annoying indeed! I fixed it by going to CCSM -> unity plugin and on the tab 'switcher' uncheck the second box before 'Bias alt-tab to prefer........'


I don't have Unity installed on my system (and I don't want to install the whole thing).
How can I install this unity plugin for compiz?

---

### Post by Paddy Landau on 2012-05-08
> **bigoten said:**
> I don't have Unity installed on my system (and I don't want to install the whole thing).
How can I install this unity plugin for compiz?
No, no, no... you don't want the Unity plugin if you don't have Unity! It would mess up your system.

Unity (and the Unity plugin) come with Ubuntu 11.04, 11.10 and 12.04.

---

### Post by drplix on 2012-05-08
> **mathiflip said:**
> very annoying indeed! I fixed it by going to CCSM -> unity plugin and on the tab 'switcher' uncheck the second box before 'Bias alt-tab to prefer........'

Someone already had a solution for the super+w function?

It seems this is one of a general set of problems.  Finding windows from other workspaces has been deliberately removed in 12.04.  I've started a thread to try to find a general solution, workaround, or community pressure to have this design decision reverted...

[http://ubuntuforums.org/showthread.php?t=1976347](http://ubuntuforums.org/showthread.php?t=1976347)

My particular bug-bear is that Scale/Spread of windows now cannot show windows from all workspaces/desktops.

---

### Post by Henne91 on 2012-05-08
> **whatthefunk said:**
> Crap Nvidia driver included on .iso.  Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```Reboot and you should be good to go.

This will get you the old proprietary nvidia driver. However, for some nvidia graphic cards even this fails because compiz crashes when trying to start Unity-3D. (However, Unity-2D should work, at least it did in my case.)

**[COLOR="Red"]WARNING! If you can start Unity-3D without problems DON'T run the following commands if you don't know what you're doing since it can break your 3D graphics acceleration![/COLOR]**

A workaround that did help me was to completly remove proprietary drivers and use nouveau instead:

```
sudo apt-get remove --purge nvidia-*
```

You also might have to remove a custom xorg.conf created by the driver or yourself:

```
sudo rm /etc/X11/xorg.conf
```

The xorg.conf will be automatically recreated after rebooting if required.

This way I could start Unity-3D without Compiz crashing and an alright 3D acceleration provided by the open-source nouveau driver.

---

### Post by searchfgold6789 on 2012-05-10
**Bug:**
The package nvidia-173 won't be installable until the Xorg team rewrites some ABI code.

**Workaround:**
Use nouveau.

---

### Post by CharlesA on 2012-05-10
> **haqking said:**
> 
Thread/workaround here [http://ubuntuforums.org/showthread.php?t=1968061](http://ubuntuforums.org/showthread.php?t=1968061)

Just so we have the workaround in this thread:

Run this from a terminal:
```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

Change the line that says:
```
dns=dnsmasq
```

To:
```
#dns=dnsmasq
```

Restart Network Manager:
```
sudo service network-manager restart
```

Verify /etc/resolv.conf does not say: nameserver 127.0.0.1

```
cat /etc/resolv.conf
```

---

### Post by tolubalogun on 2012-05-12
To solve the audio problem, install pavucontrol and go to config menu choosing audio duplex

---

### Post by shanemorris on 2012-05-12
This should help new installs of Ubuntu 12.04 with keyboard and trackpad problems. When I installed 12.04 on my Toshiba Satellite, the keyboard and trackpad would work through the USB install bootloader/blahblahblah process, but then would completely go non-functional at the login screen. Oh noes!

Of note, I'm running Windows 7 on one side, and Ubuntu 12.04 on the other side.

1. Restart your computer and hold "Shift" at the boot screen. (That's the one telling you to choose Windows or Ubuntu.) This will take you into GRUB2. If you're not familiar with what you're doing here, don't do anything stupid. Seriously. You will hurt yourself.

2. Type this...

> acpi=noirq

The "q" at the end assumes you have a QWERTY keyboard. Some other weirdos use this other type. I think it starts with an "a", or something. If that's the kind of keyboard you have, you probably know what it's called already. Replace the "q" with an "a" in that case.

3. Press "ESC". That's how you leave GRUB. You will now boot back up. If your keyboard and track pad work - ding, you have succeeded.

4. You need to KEEP this little code in place. So then you open up your handy dandy Terminal.

5. Type the following stuff. (Stuff is the techie word for it.)

> sudo gedit /etc/default/grub

6. That's going to take you to an open screen where you'll need to alter some text look for a line that says, "GRUB_CMDLINE_LINUX_DEFAULT" and in the spot where it says "quiet splash". Change that line to "acpi=noirq quiet splash"... BUT WAIT, THERE'S MORE.

7. Don't sweat it. Seriously, you're going to be fine. Basically, what we're doing is making that little edit we made stick. If not, you'll have to do it at every reboot. (That's what she never said.)

8. SAVE and CLOSE that window.

9. UPDATEUPDATEUPATE. Go into your Terminal again and type this...

> sudo update-grub

10. You're all done! Restart baby!

Any questions or help I can offer, let me know.

---

### Post by traditionalist on 2012-05-12
One very severe bug which affects a lot of things and caused me a lot of problems with a new installation of 12.04 was the software "tracker". After starting it filled up my root with stuff and crashed the system. There is apparently no way to redirect the index. It also prevented me from using some other software, notably "remastersys" because it was impossible to exclude the tracker stuff from a backup.

Alternative, if you need an indexer use "recoll" ( it is better anyway),  and don't put indices on /root

After removing tracker ( although a clean install is better), the system is once again fast and stable.

---

### Post by Paddy Landau on 2012-05-12
> **shanemorris said:**
> sudo gedit /etc/default/grub
Please use [FONT=Lucida Console]gksudo[/FONT] and not [FONT=Lucida Console]sudo[/FONT] for GUI programs.
```
gksudo gedit /etc/default/grub
```You can also enter that from Alt-F2 instead of the terminal, if you prefer.

---

### Post by loklaan on 2012-05-16
The poor laptop battery performance on Ubuntu isn't exactly a bug, but I consider it enough of a shortcoming to post a solution on this thread.

Installing **[Jupiter]("http://www.jupiterapplet.org/")**, the light-weight power and hardware control applet, will give you improved battery life.

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

Open Jupiter and it will appear in the top panel.
[IMG]http://dl.dropbox.com/u/17323455/images/jupiter.png[/IMG]

---

### Post by traditionalist on 2012-05-16
I finally found a workaround for all my graphic card problems with several new ATI Radeon cards. 

Install Gnome shell, remove Unity  and use the generic drivers in the release. Don't even bother trying the proprietary drivers or various other stuff, none of it works, I tried for two weeks without success, they just crash all the time if you try to use unity, and crash regularly with other desktop environments, especially with Ubuntu 2D  as well.  ( I didn't like Unity anyway, and was glad to be rid of it!).

"GNOME classic " runs best, but "Gnome"  and "GNOME Classic (no effects)" also run well and very stable.  Ubuntu 2D will still crash the system, it just loses the desktop all the time.  I have removed everything I could find regarding it, but it still appears in the greeter

Curiously, unity with an otherwise identical system  runs on an old celeron machine with integrated graphics without any problems. It just does not like my ATI cards.

Everything on my system which did not work before is now stable, including Compiz ( which is great now that it works!)

Maybe this will help someone else who is struggling.

I used this to remove it;

```
mike@mikepc:~$ sudo apt-get remove unity unity-2d-places unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications gir1.2-unity-4.0 unity-common indicator-sound indicator-power indicator-appmenu libindicator6 indicator-application evolution-indicator indicator-datetime indicator-messages libnux-1.0-0 nuxtools
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'gir1.2-unity-4.0' can't be removed
E: Unable to locate package libindicator6
E: Unable to locate package libnux-1.0-0
E: Couldn't find any package by regex 'libnux-1.0-0'
E: Unable to locate package nuxtools
mike@mikepc:~$ ^C
mike@mikepc:~$ 

```Make sure you install the Gnome stuff first before you delete Unity, ( For newbies like me who didn't, ! ) Or you will have to do it all from the command line. Or keep re-installing the system until you can get it to run.

---

### Post by marty331 on 2012-05-17
If you experience the 'gray flash' when you sign in, you are in 2D Unity.  If you have an Nvidia graphics card, install Bumblebee to enable 3D Unity.

---

### Post by hawthornso23 on 2012-05-17
I like to plug in a USB  mouse on my laptop. However when operating off the battery aggressive USB powersaving turns the mouse off unless it is constantly moved. 

The solution is to add the mouse device ID to the blacklist in 

```
/etc/laptop-mode/conf.d/usb-autosuspend.conf
```

mouse ID found by running lsusb

---

### Post by Leviawan on 2012-05-19
you are right

---

### Post by QwUo173Hy on 2012-05-19
Libre Office Writer does not have a working spell check on a fresh 12.04 install here (three seperate installations have the same problem).

Spell check doesn't detect any errors but says it has completed the spell check, which is not the case.

Bug Report & workaround: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/997934](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/997934) 

Thanks to Bra|10n for providing the solution on [this thread]("http://www.kubuntuforums.net/showthread.php?58629-Turn-On-LibreOffice-Spell-Check&p=299008&posted=1#post299008").

---

### Post by HanDez on 2012-05-22
This got me a perfectly working display!

 I have the AMD Quad-Core A6-3620 APU with Radeon HD 6530D graphics. And of course I got the black screen when trying to install Ubuntu 12.04.

Solution:

1. Boot the Ubuntu Live CD.
2. Hit any key during boot splash screen
3. Press F6 and select nomodeset, then Esc, and then select  Install Ubuntu, then Enter.
4. Install Ubuntu
5. Reboot into recovery mode, and select "resume normal boot" from the menu, hit enter.
6. Run the following command:

sudo apt-get update && sudo apt-get install fglrx && sudo apt-get install fglrx-updates

 7.  Follow the prompts to finish the fglrx driver installation.
 8.  Then run: sudo reboot
 9.  Boot in normal mode....ENJOY!!! 

And by the way I do have "AMD Catalyst Control Center" with this method.


:popcorn:

---

### Post by QwUo173Hy on 2012-05-23
> **tolubalogun said:**
> To solve the audio problem, install pavucontrol and go to config menu choosing audio duplex

Tolubalogun, can you describe the audio problem this solves? It would be unwise for anyone to go applying random solutions.

---

### Post by Morbius1 on 2012-05-23
> **jarlath said:**
> Tolubalogun, can you describe the audio problem this solves? It would be unwise for anyone to go applying random solutions.
I don't know what specific sound problem he was talking about but I can tell you that it resolved an issue for me using Xubuntu 12.04. This describes the cause and the proposed solution which did in fact work for me: [http://ubuntuforums.org/showpost.php?p=11401461&postcount=4](http://ubuntuforums.org/showpost.php?p=11401461&postcount=4)

I have 2 sound cards because I have one built into the monitor so this may not impact that many users.

---

### Post by J V on 2012-05-24
> **Paddy Landau said:**
> You cannot log in if your home folder is encrypted, because LightDM cannot get hold of the wallpaper. Zukaro's method is a solution to that.
If your wallpaper settings are stored in your home folder then surely it would have to be decrypted before lightdm would even know what to use?

For Xubuntu users:

Xu stores backgrounds in /usr/share/xfce4/backdrops/ not /usr/share/backgrounds/

It still won't help you - storing them there doesn't let you log in with lightdm

**Edit:** Found the workaround! Follow these instructions to be able to log in! _[http://ubuntuforums.org/showpost.php?p=11921373&postcount=20](http://ubuntuforums.org/showpost.php?p=11921373&postcount=20)_

---

### Post by Paddy Landau on 2012-05-24
> **J V said:**
> If your wallpaper settings are stored in your home folder then surely it would have to be decrypted before lightdm would even know what to use?
Yes, that is precisely the situation.

LightDM should not fail and prevent log-in in this situation -- it should instead revert to the default wallpaper or, if for whatever reason it is unavailable, to a default uniform colour.

---

### Post by J V on 2012-05-24
Then how come some people can get it working by moving the wallpaper outside of their home directory?

---

### Post by CharlesA on 2012-05-24
> **J V said:**
> Then how come some people can get it working by moving the wallpaper outside of their home directory?
Probably because the home directory is only decrypted after you login. If the wallpaper is outside of the home directory, it is not encrypted.

---

### Post by J V on 2012-05-25
My point being that to know which wallpaper the user uses you need to decrypt the home folder in the first place, so why can't it access the decrypted wallpaper?

In any case, moving the wallpaper outside the home folder doesn't do it for xubuntu

---

### Post by Paddy Landau on 2012-05-25
> **J V said:**
> My point being that to know which wallpaper the user uses you need to decrypt the home folder in the first place, so why can't it access the decrypted wallpaper?
LightDM cannot access files within your home folder, because you have not logged in and therefore the folder is still encrypted. When you move the wallpaper outside your home directory, e.g. to /usr/share/backgrounds, it is no longer encrypted. Next time you restart your machine, LightDM is able to access it.

> **J V said:**
> In any case, moving the wallpaper outside the home folder doesn't do it for xubuntu
Did you remember to set your wallpaper to the new location outside your home folder?

---

### Post by J V on 2012-05-25
Yes, and on top of that I deleted the one inside so it can't be using that one, but perhaps this is more suited to it's own thread?

---

### Post by Paddy Landau on 2012-05-25
> **J V said:**
> Yes, and on top of that I deleted the one inside so it can't be using that one, but perhaps this is more suited to it's own thread?
Yes, start your own thread to see if it can be solved.

---

### Post by Ashrael on 2012-05-25
> **codingman said:**
> Hey! Go to CCSM and then enable application switcher,it works quite beautifully,ALT-TAB then shows the Compiz window switcher, but at least it works for now.

Hope this helps

Codingman

I haven't read this thread past your post yet, but, if you install unsettings you can switch real easy from <alt-tab per desktop> to <alt-tab uses all desktops> and a whole lot more...

HTH

---

### Post by Ashrael on 2012-05-25
> **Morbius1 said:**
> I don't know what specific sound problem he was talking about but I can tell you that it resolved an issue for me using Xubuntu 12.04. This describes the cause and the proposed solution which did in fact work for me: [http://ubuntuforums.org/showpost.php?p=11401461&postcount=4](http://ubuntuforums.org/showpost.php?p=11401461&postcount=4)

I have 2 sound cards because I have one built into the monitor so this may not impact that many users.

I agree, pavucontrol is a vital app for me too, I have a Senheisser pc 36 headset which has it's own "soundcard" inbuilt (good stuff!) so I need to switch sound to and fro. For skype it was very handy in routing the incoming call sound to my loudspeakers and the rest to my headset...
As seen here: [http://ubuntuforums.org/showthread.php?t=1839994&highlight=skype+ringing](http://ubuntuforums.org/showthread.php?t=1839994&highlight=skype+ringing)

It can also be very helpful with 5.1 and higher hardware.....

---

### Post by LawM on 2012-05-26
Pidgin + sipe, to use communicator, to avoid the annoying "Read error":

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/950790](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/950790)

export NSS_SSL_CBC_RANDOM_IV=0 worked
 for it to take effect open a terminal window then
$ export NSS_SSL_CBC_RANDOM_IV=0
$ pidgin &

---

### Post by atomicblue on 2012-06-02
> **CharlesA said:**
> Just so we have the workaround in this thread:

Run this from a terminal:
```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

Change the line that says:
```
dns=dnsmasq
```

To:
```
#dns=dnsmasq
```

Restart Network Manager:
```
sudo service network-manager restart
```

Verify /etc/resolv.conf does not say: nameserver 127.0.0.1

```
cat /etc/resolv.conf
```


Canonical -- for all that is holy!  Pick a configuration and stick with it!  The rest of the Linux world has been using resolvconf for 20 years now.  At least give us some heads up before you start changing standard configurations!

---

### Post by CharlesA on 2012-06-02
> **atomicblue said:**
> Canonical -- for all that is holy!  Pick a configuration and stick with it!  The rest of the Linux world has been using resolvconf for 20 years now.  At least give us some heads up before you start changing standard configurations!
Read the details why they made the change here:
[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

I do not think it is a good idea, but this isn't the thread for such discussion.

---

### Post by eode on 2012-06-03
Mouse gets laggy during disk usage.

Symptoms:
Mouse becomes difficult to control, lags, or 'skips' when the hard disk is under heavy usage (may happen during other IO operations, like heavy network or ramdisk usage as well).
Mouse may miss clicks.
Double-clicks may be interpreted as single-clicks.

..this makes a gamer just want to die.

In my case, this was caused by DRM/kernel mouse polling, and is easily fixed.  There are no reported side-effects to this fix, other than (if you're a gamer) prolonged life.

If you are running into the problem now, and just want to test real quick if this fix works, you can do:
```

sudo sh -c 'echo N > /sys/module/drm_kms_helper/parameters/poll'
```

To make that 'permanent', type:
```

sudo sh -c 'echo "options drm_kms_helper poll=0" >> /etc/modprobe.d/local.conf'
sudo update-initramfs -u
```

..and then you will be blissfully, blissfully happy, for ever and ever.

---

### Post by hottarod on 2012-06-08
Problems I have with 12.04(so far);

speakers die, no sound at all
toggle to head phones and back to speakers and they come back
it is definitely set on the external speakers but they aren't working
I have no clue when this starts or what is causing it

suspend display power option
after some unknown period of time the system hangs and won't come back
have to power off and back on which got tedious so I turned off suspending the display  and the system for now

software center has been schizophrenic starting back in late 11.10
click it and nothing happened and no automatic updates
the past couple of fix packages seem to have fixed it 
saw a replacement for software center come down recently so I guess that was it

system soft crashes while just sitting idle - dbus daemon
one message I caught says that cpu 1 has not been communicating for at least 22 seconds(I'm running amd64) 
I sent in a few crash reports on it
most of the time it will continue to run after this

my variable rpm fan no longer works
I let my bios manage the rpms on it and it cycled fine up until 12.04
no fix for this so far that I have found

Firefox has been crashing and having to quit
recent fixes may have fixed this as I haven't seen it in a couple or 3 days now
I noticed a new Firefox was distributed in that

In summary, install the latest fixes should help I guess.  Don't know about the other stuff.

---

### Post by Cavsfan on 2012-06-08
I installed xscreensavers and inserted a startup command of ```
xscreensaver -nosplash
```
It would never work and when I clicked on screensaver, I got this error:
```
The XScreenSaver daemon doesn't seem to be running on display ":0".  Launch it now?
```
So, I would have to click yes and then the screensaver would work.
I finally noticed that it wasn't actually running so I added another startup command just like the above and that fixed it.

Here is what it took:
[http://ubuntuforums.org/showpost.php?p=12009172&postcount=5](http://ubuntuforums.org/showpost.php?p=12009172&postcount=5)

I've rebooted a few times, logged out a few times and this finally fixed it.

---

### Post by Cavsfan on 2012-06-09
The same goes for Emerald windows manager. It does not work at startup even though I have ```
emerald --replace
```in Startup Applications.
I just added a 2nd startup command and logged out and back in and viola, it works like it should.
This is standard Ubuntu 12.04 with Unity.

This works but, only about 90% of the time. But, without it Emerald will not start at all. 
If it does not work at login, I logout and back in and it works then.

---

### Post by imbjr on 2012-06-10
To be able to design GUI applications in Netbeans, use this at the command line:

netbeans -cp:a /usr/share/java/xercesImpl.jar

This will prevent the GUI designer displaying just a rectangle with the message "Loading ..." at its centre.

---

### Post by K-Ghidorah on 2012-06-21
I'd been having problems with continual random hard freezes.  It was bad enough that I put up a rather nasty rant here not too long ago announcing that, until things got fixed, I was going to stop using anything based off the current Ubuntu.

BUT!!!

I stumbled onto the cure due to the fact that I really... REALLY.... wanted to use KXStudio again, and their low-latency kernel is only available on 12.04.  Turns out the kernel is slightly older than the original (3.2.0-23, as opposed to 3.2.0-24 or -25).  Again, I'm using the low-latency kernel, so I don't know if this makes any difference (I know more about popcorn kernels than Linux kernels).

If anyone else is having the problems I was facing, I recommend getting the 3.2.0-23 generic kernel (or the low latency kernel if you're also a musician).  I've not had one freeze so far.  Also, as far as I know, very few people have had these problems in the Live environment, so the 3.2.0-24 might also be a good one.

I WOULD'VE put this at the end of my rant thread, but the mods closed the thread before I could post that I could very well have solved the problem (I'll give it a week).  But anyhoo, if you stumble upon this and you've had these problems, give this a shot and maybe confirm or deny this.

Hope I've helped someone out there.

~K

---

### Post by tkoco on 2012-06-22
The only problem with this tip is that the version changes over time.
Change ```
sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```
To ```
sudo apt-get install nvidia-current
```

and apt-get will fetch the latest automatically.

> **whatthefunk said:**
> Crap Nvidia driver included on .iso.  Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

Reboot and you should be good to go.

---

### Post by exploder on 2012-06-27
If you are getting an error saying a system problem has been detected and there is no problem or other errors for no apparent reason, remove apport and you will no longer get these messages.

I have had this problem with every install of Ubuntu 12.04 and that is how I put a stop to it. Hope this helps someone.

---

### Post by ka55o5 on 2012-07-02
Don't forget to run nvidia-settings and Save to X Configuration File ***before*** updating.

PS.
Adding the PPA and checking for updates is all that is needed (no extra CMDs).

> **tkoco said:**
> The only problem with this tip is that the version changes over time.
Change ```
sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```
To ```
sudo apt-get install nvidia-current
```

and apt-get will fetch the latest automatically.[QUOTE=whatthefunk;11892911]Crap Nvidia driver included on .iso.  Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

Reboot and you should be good to go.[/QUOTE]

---

### Post by guipy on 2012-07-02
Hello everyone...

i'm experiencing a "bug", but i have no workaround...if someone knows a workaround, i'll thanks very much.

The problem is: many times, with 2 or 3 windows, e.g., if you minimize them, once you restore one, it comes without focus ! It's annoying because if you restore terminal without focus and start typing...:mad::mad: you all know...you type for nothing :lol:

you can see a most explained version of this bug: [http://ubuntuforums.org/showthread.php?t=1963643](http://ubuntuforums.org/showthread.php?t=1963643)

Thanks in advance...

---

### Post by Cavsfan on 2012-07-02
> **tolubalogun said:**
> To solve the audio problem, install pavucontrol and go to config menu choosing audio duplex

Thanks! Just by installing pavucontrol, I now have the normal sound that plays just after logging in.
I even had it setup in startup applications, but it did not work until I installed that file. :guitar:

---

### Post by Cavsfan on 2012-07-02
Anyone have a clue as to why an additional gedit file is opened when you enter gksu gedit filename? 
Everytime I edit a file that way a 2nd text file is opened for edit although it is blank.
If you immediately close it, it just closes but, if you save the file you were working with, it asks you to save the blank file.
It's just a pain in the neck.

---

### Post by Paddy Landau on 2012-07-02
> **Cavsfan said:**
> Anyone have a clue as to why an additional gedit file is opened when you enter gksu gedit filename?
Indeed, this has been happening since the beginning of 12.04, I believe.

It is a pain. I think a bug report should be raised for this; I hadn't thought to do it until now.

---

### Post by drs305 on 2012-07-02
> **Paddy Landau said:**
> Indeed, this has been happening since the beginning of 12.04, I believe.

It is a pain. I think a bug report should be raised for this; I hadn't thought to do it until now.

The gedit root 'Untitled document' bug has been around for a long time. They aren't too interested in fixing it. I switched to Geany when editing files as root for this reason.

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076")

---

### Post by Paddy Landau on 2012-07-02
> **drs305 said:**
> [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076")
Thanks for the bug reference. I've added my vote to it.

---

### Post by Paddy Landau on 2012-07-03
> **Cavsfan said:**
> Anyone have a clue as to why an additional gedit file is opened when you enter gksu gedit filename?
I have made a workaround for this problem. It's a tad fiddly setting it up, but once done, it works well.

Here's how to set it up.

[LIST=1]
[*]Download the attachment [attach]220573[/attach] and extract the two files as follows.
[LIST]
[*][FONT=Lucida Console]askpass[/FONT] — into any folder you like, somewhere out of your way.
[*][FONT=Lucida Console]ggedit[/FONT] — into any folder within your path; I use [FONT=Lucida Console]~/bin[/FONT] (which is put onto your path by default if you create that folder and log out and in again).
[/LIST]
 
[*]Edit the file [FONT=Lucida Console].profile[/FONT] in your home folder. Append the following line, substituting my path with wherever you saved the [FONT=Lucida Console]askpass[/FONT] file (this is necessary even if [FONT=Lucida Console]askpass[/FONT] is within your path). You cannot use "[FONT=Lucida Console]~[/FONT]"; you must use the fully-qualified path.```
export SUDO_ASKPASS='/home/paddy/bin/askpass'
```
[*]Either reboot or log out and in again.
[/LIST]
To use:

[LIST]
[*]Instead of [FONT=Lucida Console]gksudo gedit[/FONT], use [FONT=Lucida Console]ggedit[/FONT], which you can use from Alt-F2, the terminal or a script. For example, press Alt-F2 and enter:
[FONT=Lucida Console]ggedit /etc/fstab[/FONT]
[*]If you prefer to use a different name, simply rename [FONT=Lucida Console]ggedit[/FONT] to something else and use that new name.
[/LIST]
Known problems:

[LIST]
[*]If, after starting [FONT=Lucida Console]ggedit[/FONT] but before entering your password, you change your mind and press *Cancel*, it will nevertheless ask you three times for your password with a short pause between each attempt. I don't know how to prevent that from happening.
[/LIST]

---

### Post by Morbius1 on 2012-07-03
Wouldn't it be a lot easier to install leafpad and simply do a:
```
gksu leafpad
```Internally it may very well have the same issue as a "gksu gedit" but since there are no tabs in leafpad you'll never know. ;)

Just a suggestion.

---

### Post by Cavsfan on 2012-07-03
> **drs305 said:**
> The gedit root 'Untitled document' bug has been around for a long time. They aren't too interested in fixing it. I switched to Geany when editing files as root for this reason.

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

Thanks for the info. I too have added my vote to the bug.

---

### Post by Cavsfan on 2012-07-03
> **Morbius1 said:**
> Wouldn't it be a lot easier to install leafpad and simply do a:
```
gksu leafpad
```Internally it may very well have the same issue as a "gksu gedit" but since there are no tabs in leafpad you'll never know. ;)

Just a suggestion.

+1 on Leafpad! I just tried it and is great! :D I'm using that from now on.

---

### Post by Cavsfan on 2012-07-03
> **Cavsfan said:**
> I installed xscreensavers and inserted a startup command of ```
xscreensaver -nosplash
```It would never work and when I clicked on screensaver, I got this error:
```
The XScreenSaver daemon doesn't seem to be running on display ":0".  Launch it now?
```So, I would have to click yes and then the screensaver would work.
I finally noticed that it wasn't actually running so I added another startup command just like the above and that fixed it.

Here is what it took:
[http://ubuntuforums.org/showpost.php?p=12009172&postcount=5](http://ubuntuforums.org/showpost.php?p=12009172&postcount=5)

I've rebooted a few times, logged out a few times and this finally fixed it.

This post was not correct. It did not require 2 separate entries in Startup Applications.
Just had to edit **gksu gedit /etc/xdg/autostart/screensaver.desktop** file and fix the misspelled word Application (It had Applicaton without the i at the end).

---

### Post by Paddy Landau on 2012-07-04
> **teeyounee said:**
> I'm experiencing a bug that I cannot find a workaround. I installed Ubuntu via Usb and everything went fine but when I boot I get a black screen with a blinking underscore. Please help
Please start a new thread in the [Absolute Beginner Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=326"). This is a thread for known bugs with workarounds.

---

### Post by Cavsfan on 2012-07-05
I could never get Emerald [FONT=Verdana]window decorator to work in Precise until I stumbled upon this.

I had **emerald --replace** in startup programs but, that did not work. What did work was making it into a script.
[/FONT]```
#! /bin/bash
sleep 5
emerald --replace
```I just saved that with gedit in my Home directory, saved it as emerald-script and made it executable.
I put that command in the startup application as **/home/cavsfan/emerald-script** and voila it finally worked!

I got that from this site although I did not install it with their method.

[[COLOR=blue]_http://paulscomputernotes.blogspot.com/2012/04/emerald-themer-in-ubuntu-1204.html_[/COLOR]]("http://paulscomputernotes.blogspot.com/2012/04/emerald-themer-in-ubuntu-1204.html")

EDIT: While logging on in Gnome Classic mode without Emerald there was no way to get to the top of windows to move them. 
They were stuck where ever they opened up. But, with Emerald I could click near the top and move the window down and wherever I wanted.

---

### Post by Paddy Landau on 2012-07-09
> **Cavsfan said:**
> While logging on in Gnome Classic mode without Emerald there was no way to get to the top of windows to move them.
If that should happen to you again, hold down Alt and click anywhere within the window; that will allow you to drag the entire window.

---

### Post by Cavsfan on 2012-07-10
> **Paddy Landau said:**
> If that should happen to you again, hold down Alt and click anywhere within the window; that will allow you to drag the entire window.

Thanks for the info!

---

### Post by Cavsfan on 2012-07-13
Anyone know anything about logging into 12.04 in Classic Gnome opening anything and the top goes behind the top panel?
It acts like Unity where there is no top panel. I always have to bring the windows down a 1/4 inch to access the File, Edit, etc.
I can open Firefox, have to pull it down 1/4 inch, close it and when I open it back up it does the exact same thing.
Just wondering if there is a work around or is it a bug?
That is why I had to have Emerald running so I could access the top before I knew Paddy's way of clicking any where on the window while holding ALT and moving the window down.

---

### Post by CharlesA on 2012-07-13
I didn't run into that when I was messing around with Gnome Classic.

---

### Post by Cavsfan on 2012-07-13
> **CharlesA said:**
> I didn't run into that when I was messing around with Gnome Classic.
That is always the way my system works. Everytime I open a terminal,  folder, firefox, etc. it always does this and I have to pull it down 1/4  inch.
Over and over again without logging out or anything. Every window does this.

---

### Post by Cavsfan on 2012-07-13
This is when I first open Firefox:

[[IMG]http://ompldr.org/tZXFmYQ[/IMG]]("http://ompldr.org/vZXFmYQ")

This is after I pull it down 1/4 inch.

[[IMG]http://ompldr.org/tZXFmZA[/IMG]]("http://ompldr.org/vZXFmZA")

If I close it and re-open it: exact same thing.

---

### Post by CharlesA on 2012-07-13
I wonder if that has something to do with the global menu. Do you have it installed?

---

### Post by Cavsfan on 2012-07-13
> **CharlesA said:**
> I wonder if that has something to do with the global menu. Do you have it installed?
I am not sure. What is it called. I checked SPM for global-menu and nothing came up.

---

### Post by CharlesA on 2012-07-13
I think it is a part of unity.

firefox-globalmenu - Unity appmenu integration for Firefox

---

### Post by Cavsfan on 2012-07-13
> **CharlesA said:**
> I think it is a part of unity.

firefox-globalmenu - Unity appmenu integration for Firefox

I have that installed. It happens with terminal, folders and every possible window I could open not just Firefox.

---

### Post by CharlesA on 2012-07-13
Try this then:
[http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/)

---

### Post by Cavsfan on 2012-07-13
> **CharlesA said:**
> Try this then:
[http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/)

Thanks for that link! That did not fix the Gnome classic problem where it does not realize there is a top panel there.
I cannot even right click on the top panel but, I switched (logged off and back on) to Unity and I love getting away from having to go to the top of 
the screen for the File, Edit, etc. buttons. Except Firefox but, I know how to make the File, Edit, etc. appear if I want it to.
At least that is what I think I am seeing.

So, that cured a problem I disliked about Unity but, it didn't fix the classic gnome issue where the windows open under the top panel.
I wonder what is causing that? BTW when you switch from classic to Unity or vice versa it takes a while for it to load.
Thanks!

---

### Post by CharlesA on 2012-07-13
Glad it fixed Unity for you. I wonder what the deal with Classic Gnome is. =/

---

### Post by Cavsfan on 2012-07-13
> **CharlesA said:**
> Glad it fixed Unity for you. I wonder what the deal with Classic Gnome is. =/
Thanks! That Unity thing was annoying like when I had a terminal open at the bottom of the screen  and had to go to the top of the screen to do anything! 
I give up trying to fix the Classic Gnome problem. I can deal with it OK.
It will hopefully be fixed when I install 12.04.1 when it comes out in August. :)

---

### Post by Paddy Landau on 2012-07-13
> **Cavsfan said:**
> Anyone know anything about logging into 12.04 in Classic Gnome opening anything and the top goes behind the top panel?
I did have this problem intermittently back in the beta phase, but not for a couple of months now. Is your system fully up-to-date?

---

### Post by QIII on 2012-07-14
deleted

---

### Post by Cavsfan on 2012-07-14
> **Paddy Landau said:**
> I did have this problem intermittently back in the beta phase, but not for a couple of months now. Is your system fully up-to-date?

Yes, I downloaded the iso on the RC date (April 26th)  and everything is up to date that I know of.  I check regularly for updates.
When I have 2 tabs open in Firefox and close it it saves the 2 open pages (I have tab control installed as an addon).
When I restart or logoff and back on and open Firefox, it is not behind the top panel for some reason.
But, if there are not more than one tab saved it opens behind the top panel just like everything else.

---

### Post by Cavsfan on 2012-07-14
For now I will just hide the top panel. Found you have to press ALT+SUPER plus right click in Gnome Classic to get to the menu for autohide.
That's why I love Ubuntu: you learn something pretty often. :)

---

### Post by Paddy Landau on 2012-07-14
> **Cavsfan said:**
> Found you have to press ALT+SUPER plus right click in Gnome Classic to get to the menu...
You should not need the Super key; just Alt+right-click. There was a specific reason why Canonical introduced that requirement, but I've forgotten that reason.

---

### Post by hawthornso23 on 2012-07-15
[COLOR=Silver]Alt + Super + rightclick  is needed if you are running compiz with desktop effects. 

Alt + rightclick does absolutely nothing to a panel in that situation.[/COLOR] [COLOR=Silver]

The changed behavior is undocumented, inconsistent, undiscoverable and annoying ... until you find out about it and get used to it. Then it is merely one more quirk.[/COLOR] 

UPDATE: OK - just tried it and  both  alt + rightclick  and  al t+ super+ rightclick  now work.  Looks like there was an undocumented change back.

---

### Post by Cavsfan on 2012-07-15
Just to verify, I logged into Unity and nothing works on the top panel, I tried ALT+Right Click, ALT+SUPER+Right Click and nothing.
I also tried just right click and nothing. 
Nothing works at all on my top panel in Unity and in Gnome Classic, the only thing that works for me on the top panel is ALT+Super+Right Click.

---

### Post by Paddy Landau on 2012-07-15
> **Cavsfan said:**
> I logged into Unity and nothing works on the top panel...
It is set only for Gnome Classic, not for Unity.

> **Cavsfan said:**
> ... the only thing that works for me on the top panel is ALT+Super+Right Click.
Curious. Have you changed your keyboard short-cuts at all?

---

### Post by Cavsfan on 2012-07-15
> **Paddy Landau said:**
> Curious. Have you changed your keyboard short-cuts at all?

The short answer would be no I have not. Although:

When I go to System Tools > Preferences > Keyboard Input Methods a box pops up that says
"Keyboard Input Methods (IBus Daemon) has not been started. Do you want to start it now?"
I clicked Yes and in the box it says this:

"IBus has been started! If you can not use IBus, please open System Menu -> System Settings ->
Language Support and set the "Keyboard Input Method" to "ibus", then log out and back in again."

Then Ibus Preferences opened up. 

If I logout and back in the IBus Daemon is not started and it asks the same thing.

But, under System tools > System Settings > Keyboard Layout I have not changed anything.

---

### Post by Paddy Landau on 2012-07-15
> **Cavsfan said:**
> ... "Keyboard Input Methods (IBus Daemon) has not been started. Do you want to start it now?"
I suggest you start a new thread for this. Obviously, there is something wrong with your set-up, and it should be fixed.

---

### Post by Cavsfan on 2012-07-16
> **Paddy Landau said:**
> I suggest you start a new thread for this. Obviously, there is something wrong with your set-up, and it should be fixed.

Thank you. I opened a new thread.

---

### Post by Cavsfan on 2012-07-16
Could an admin. please change the title of this thread from "Precise Keyboard Input Methods error" to "Precise Gnome classic top panel problem"?

[http://ubuntuforums.org/showthread.php?p=12107416#post12107416](http://ubuntuforums.org/showthread.php?p=12107416#post12107416)

I went into System Menu -> System Settings -> Language Support and set the "Keyboard Input Method" to "ibus", then logged out and back in again.

Then when I click on System Tools > Preferences > Keyboard Input Methods, 
The Ibus Preferences opens up. So, I believe that part is fixed.
Thanks!

---

### Post by Cavsfan on 2012-07-19
If any one has the problem of windows opening under the top panel in Gnome Classic, which I had after 2 clean installs.
Open up **CCSM** and enable **Window Rules** and then beside **Below** enter **top_panel**.
That should fix it.

FYI: When doing a fresh clean install of 12.04 64 bit I initially had only 2 options when logging in: Ubuntu and Ubuntu (2D).
After installing Gnome Classic with these instructions:
[[COLOR=blue]_How to install classic gnome desktop in ubuntu 12.04 (Precise)_[/COLOR]]("http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html")

Then Gnome Classic and Gnome Classic (No Effects) appeared in the menu as options when logging in.
Also after installing Cairo Dock, 3 more options appeared at the top of the list: Cairo Dock (Gnome +Effects), Cairo-Dock (Gnome no effects) and Cairo-Dock (with Unity Panel)
So, after Gnome Classic and Cairo Dock were installed there are 7 options listed when logging in.

---

### Post by Paddy Landau on 2012-07-19
> **Cavsfan said:**
> FYI: When doing a fresh clean install of 12.04 64 bit I initially had only 2 options when logging in: Ubuntu and Ubuntu (2D).
Was that even after installing all updates? I did not install Gnome Classic, and yet they (Gnome Classic and Gnome Classic No Effects) are available to me.

---

### Post by Cavsfan on 2012-07-19
> **Paddy Landau said:**
> Was that even after installing all updates? I did not install Gnome Classic, and yet they (Gnome Classic and Gnome Classic No Effects) are available to me.

Yes, I am sure because I installed Cairo Dock and Compiz, Emerald, got a whole slew of updates,
rebooted several times and when Gnome Classic did not appear I installed it via that website's directions.

If you were involved with the testing process maybe that could explain it. That is about all I can think of.

---

### Post by Paddy Landau on 2012-07-19
> **Cavsfan said:**
> If you were involved with the testing process maybe that could explain it.
Nope. I tested in VIrtual Box, but did a fresh installation on my machine only after the official release date. How curious.

---

### Post by Cavsfan on 2012-07-19
> **Paddy Landau said:**
> Nope. I tested in VIrtual Box, but did a fresh installation on my machine only after the official release date. How curious.

Definitely curious! I did an initial install on April 26 the final release date.
Yesterday I formatted the DVD-RW and downloaded a fresh ISO and installed it. To the best of my knowledge Gnome did not show up until I installed it.

Also, I counted wrong on the above post: there are 8 total options when logging in - 3 Gnome login options.
I believe Gnome, Gnome Classic and Gnome Classic (No effects).

---

### Post by MoebusNet on 2012-07-20
I hope Nicolas doesn't mind me quoting him here. This workaround enables nvidia96 driver users to use the restricted nvidia drivers with 12.04. This works for me with Lubuntu 12.04.

From: [http://ubuntuforums.org/showthread.php?t=1966336&page=3](http://ubuntuforums.org/showthread.php?t=1966336&page=3)
See post #24

> Hi guys,

In order to use nvidia-173 or nvidia-96, please see my post here:
[https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268](https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268)

I found a workaround: keep the 11.10 version of the Xorg server
No conflict at all with any package from 12.04 !!!

nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact "composite" is mandatory to use Unity correctly (very laggy) I had to force composite to switch it "off" to avoid laggy windows by modifying /etc/X11/xorg.conf:

Section "Extensions"
Option "Composite" "Disable"
EndSection

Enjoy.

Nicolas

---

### Post by MoebusNet on 2012-07-20
> **exploder said:**
> If you are getting an error saying a system problem has been detected and there is no problem or other errors for no apparent reason, remove apport and you will no longer get these messages.

I have had this problem with every install of Ubuntu 12.04 and that is how I put a stop to it. Hope this helps someone.

Again, I'm quoting someone else's work that solves an issue:

[http://ubuntuforums.org/showthread.php?t=1981696&page=3](http://ubuntuforums.org/showthread.php?t=1981696&page=3)
See post #30 by Carborundum

```
sudo sed -i s/enabled=1/enabled=0/ /etc/default/apport
```

This way you won't have to uninstall apport.

---

### Post by SpaceMaster on 2012-07-20
I've been seeing a lot of Nvidia drivers problems here.  There are several similar known bugs reported for this.  In my case, I found helpful instructions here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485"), and there's a short chronicle of my journey to a fully functional desktop here: [http://ubuntuforums.org/showthread.php?t=2029882]("http://ubuntuforums.org/showthread.php?t=2029882") I really suggest this solution, as it provides you with drivers tailored by Nvidia specifically for the graphics car you have installed.

---

### Post by HunterDX77M on 2012-07-21
> **philinux said:**
> If you have ambiance as your theme and you right click the desktop, for example, you'll see a light menu rather than dark like Oneiric.

The discussion surrounding this "design decision" is here.

[Bug Report 925895]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895")

The fix if you want it is here.

[Theme fix for Precise]("http://www.omgubuntu.co.uk/2012/04/how-to-revert-to-dark-menus-for-ambiance-theme-in-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29")

Thanks for that! I couldn't find something that worked until I saw this.

---

### Post by uradhalat on 2012-07-24
I m using ubuntu on RV509 Samsung Laptop but it was unable to install drivers of nvidia graphic card

---

### Post by Cavsfan on 2012-07-24
Suspend was not working. It would go into suspend mode really quick and nice but, it would not resume to anything but, a black screen.
I had to press the reset button on my PC and reboot every time. I searched for answers and there are none out there.

I had added the xswat ppa and upgraded nvidea-current, etc. to version 302.17.
Turns out that was what caused my problem.  I have a Nvidea Geforce 9800.

I followed the paragraph at the top of this page and did a ppa-purge which reverted my driver back to 295.40 and suspend works fantastic now!

[[color=blue]_https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/_[/COLOR]](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

This is my 2nd install of Precise and the first time I stayed with the default driver and was amazed at how fast suspend went into effect.
I never had any problem with it going into suspend mode or waking from it.
I can say that it goes into suspend mode much, much faster than windows 7 goes into sleep mode.
The fans and the CPU are off before my monitor turns off!

---

### Post by blortuga on 2012-07-27
> I don't know enough to know if this is a "bug" or just one of those "works-as-designed" things.  I've been using 12.04 for a few weeks now, and on a couple of occasions over the last week, I've had episodes of extreme network slowness.  

This *seemed* to begin after I added a bunch of "block" addresses to my /etc/hosts file.  (which was funny, because I was used to this method causing problems on Windows, not Linux).

I isolated the slowness to traffic between my laptop, and my home router (DND 3300, using AT&T DSL as my ISP).  As near as I can figure, my ubuntu 12.04 machine thinks that the DNS server is my router.  (192.168.1.1)  - When every other machine on my network (varieties of Windows, Mac OS X, iOS, Android), all get the DNS server ip addresses forwarded from the router via DHCP.

I have found some articles stating that 12.04 changes the way  Ubuntu does dns resolution, instead of using /etc/resolv.conf, this file is dynamic and represents output from resolvconf, and this obtains dns information from dnsmasq.  A lot of these articles suggest ways of disabling dnsmasq, (though I'm not sure this is a good idea, for forwards-compatability).  dnsmasq uses /etc/hosts for resolution, by default, first.

I'm not sure why that would be a problem, because it should just block those addresses, and blast through, and then resolve any others off the dns server it has. But it didn't seem right to me that the DNS server is listed as 192.168.1.1.  DHCP should give my client the DNS server addresses, like every other machine.  

What I ended up doing was modifying my /etc/dhcp/dhclient.conf file, and entering:
prepend domain-name-servers (with a comma-separated list of my ISP's name servers, followed by some free dns servers, in case my problem was caused by my ISP's servers being flaky).

This seemed to fix the problem, but since it was really intermittent, I'm not sure if it's going to happen again, say two days from now.

But if this behavior is related to the configuration- change of using this local dnsmasq service, then I'd say it could be called a "Precise bug".  A system configured with a static IP probably wouldn't see a problem, because dns servers would be explicitly specified.  I think you're not supposed to need to explicitly specify dns servers for dchp - but the fact that I was getting SOME resolutions, and others were timing out like crazy, means that there was probably some content dependency on the contents of /etc/hosts.  I don't think it should do that.

Long story short: turned out that the problem was my DSL profile with my ISP. Not a "precise" bug.
It seemed like it was my ubuntu system only, because it was intermittent; but the problem was that the DSL signal was so poor, that it would bog down the responsiveness of the router.
Resetting the profile (ISP support rep does this remotely) seemed to fix it.

---

### Post by alaskafun on 2012-07-27
Does anyone know what those it mean this text below ?

---

### Post by heyup on 2012-08-08
This bug hasn't been fixed yet:-

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1010461](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1010461)

'Installation failed. The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again'.

Workaround here:

[http://ubuntuforums.org/showthread.php?t=1966588](http://ubuntuforums.org/showthread.php?t=1966588)

Edit. Error doesn't occur using alternate installer.

---

### Post by bogan on 2012-08-26
Hi!, **All**,   **Re: Most Unity Launcher Icons Invisible**.

I formatted the root partition of my 12.04 updated to 12.04.1; it had a separate /Home partiton I left unaltered. I then installed 12.04.1 from a newly downloaded LiveCD.

The installation was completed OK, except for - for some reason, I had not chosen the option to install propriatory drivers - installing the nvidia 173 drivers which messed up my graphics. Using 'Remove' in Additional Drivers put that right.

However, the Icons in the Unity Launch bar were mostly invisible, though the title showed when the Mouse Pointer was over one; even the ones that did show did not work when selected.```
unity reset # and
unity replace # and rebooting
``` produced only screens full of error messages; though at least they did not hang unfinished, as previous installations always did.

However, running: ```
sudo apt-get install --reinstall ubuntu-desktop 
```displayed all the Icons I expected, and none of the Unity default Icons I did not want.

Only the 'GConf Cleaner' and 'Update Manager' did not have their correct Icons.

They were even at the smaller 32 pixel size.

Chao!**, bogan**.

---

### Post by Cavsfan on 2012-08-26
Did a fresh install of 12.04.1 today and Paddy, I only had Unity and Unity 2D as the only 2 selections after the initial install.
I had to install Gnome Classic in order for it to be selectable and Compiz and Cairo Dock for other selections to appear.

Unity works fine, but in Gnome Classic there are no window switchers that work. Every time I tried to select one from CCSM, it froze and I had to press the reset  button.
There is no default window switcher like the one in Unity.

Does any one know a work around for that? Or is there a bug filed? It sure is annoying!
If you press Alt+Tab it froze also.

---

### Post by Paddy Landau on 2012-08-27
> **Cavsfan said:**
> Did a fresh install of 12.04.1 today and Paddy, I only had Unity and Unity 2D as the only 2 selections after the initial install.
I discovered how I had got the Gnome Classic options. I installed [alacarte]("apt:alacarte") (Main Menu) in order that I could add, remove and modify menu items (the Dash uses the Main Menu). Installing alacarte installs Gnome Classic.

Incidentally, 12.10 does away with Ubuntu 2D. It has some clever mechanism by which people without suitable graphics cards automatically get the same basic functionality as Ubuntu 3D, such as being able to change the Launcher size. I haven't tried installing alacarte on 12.10, though.

---

### Post by vasa1 on 2012-08-27
> **Paddy Landau said:**
> I discovered how I had got the Gnome Classic options. I installed [alacarte]("apt:alacarte") (Main Menu) in order that I could add, remove and modify menu items (the Dash uses the Main Menu). Installing alacarte installs Gnome Classic.

Incidentally, 12.10 does away with Ubuntu 2D. It has some clever mechanism by which people without suitable graphics cards automatically get the same basic functionality as Ubuntu 3D, such as being able to change the Launcher size. I haven't tried installing alacarte on 12.10, though.

Have you also installed Gnome Tweak Tools (Advanced Settings)? That one also pulls in a bunch of Gnome stuff.

---

### Post by Paddy Landau on 2012-08-27
> **vasa1 said:**
> Have you also installed Gnome Tweak Tools (Advanced Settings)? That one also pulls in a bunch of Gnome stuff.
No, I haven't.

---

### Post by Cavsfan on 2012-08-27
> **Paddy Landau said:**
> I discovered how I had got the Gnome Classic options. I installed [alacarte]("apt:alacarte") (Main Menu) in order that I could add, remove and modify menu items (the Dash uses the Main Menu). Installing alacarte installs Gnome Classic.

Incidentally, 12.10 does away with Ubuntu 2D. It has some clever mechanism by which people without suitable graphics cards automatically get the same basic functionality as Ubuntu 3D, such as being able to change the Launcher size. I haven't tried installing alacarte on 12.10, though.

Forgot to mention that 12.04 crawled along like it had a 3-5 second pause when I did anything! Even when I installed the Nvidia driver. Although come to find out it was the 173 version.
Installing the Nvidia Current Updates driver 295.49 through Additional Drivers is what  fixed it though. Now, it is normal.

I have 12.10 installed and I like it better than 12.04. Installing the Nvidia driver destroys the installation. I thought I could pull that off a 2nd time and botched it again.
I had to re-install that 2 days ago and it works great with the nouveau driver. I have Compiz, CCSM, Cairo Dock Open GL. the cube, Emerald window decorator, etc. It works pretty well!
Although if the grub is not installed on that partition, I have no mouse movement.

So, there is no work around for switching windows in Gnome Classic in 12.04? Every time I try to set something in CCSM, it freezes completely.
There doesn't seem to be any default window switcher.

---

### Post by Paddy Landau on 2012-08-27
> **Cavsfan said:**
> So, there is no work around for switching windows in Gnome Classic in 12.04? Every time I try to set something in CCSM, it freezes completely.
Sorry, I don't know. I have been using *Gnome Classic (No Effects)* when Unity did not correctly work; but Compiz has stabilised after some bugs were fixed, so I have been using only Unity recently.

---

### Post by bogan on 2012-08-27
Hi!,** Cavsfan,**

Like you I did a clean install of 12.04.1 yesterday, and the system installed the 173 nvidia-current driver.

But unlike you, I did not have any of the problems you report here and in other threads.

'Alt+Tab' works the Window Switcher correctly, though I did have to run ```
sudo apt-get install --reinstall ubuntu-desktop
```to get the Launcher Icons correctly, as reported above.

Chao!, **bogan**.

---

### Post by Cavsfan on 2012-08-27
> **bogan said:**
> Hi!,** Cavsfan,**

Like you I did a clean install of 12.04.1 yesterday, and the system installed the 173 nvidia-current driver.

But unlike you, I did not have any of the problems you report here and in other threads.

'Alt+Tab' works the Window Switcher correctly, though I did have to run ```
sudo apt-get install --reinstall ubuntu-desktop
```to get the Launcher Icons correctly, as reported above.

Chao!, **bogan**.

This was in Gnome Classic with effects?
Thanks!

---

### Post by bogan on 2012-08-27
Hi!, **Cavsfan**,

No, this was in ubuntu/unity3d.

Using 'Alt+Tab', the Mouse cursor did not work - ie was not visible - so you navigate with the Cursor keys, & release 'Alt' or press 'Enter' to select the highlighted choice.

In Gnome Classic (no effects) you have the open window files listed in the bottom panel, so I had not tried it until now. At first I thought it was not working, but...:

Pressing 'Alt+Tab' displayed [[COLOR=Blue]Deleted[/COLOR][COLOR=Yellow]Thumbnails[COLOR=Black]][/COLOR][/COLOR][COLOR=Black] [/COLOR]Icons for all the four open windows, repeatedly pressing 'Tab' altered the highlight, and releasing 'Alt'  selected it. [Two File manager windows were represented by  Icons - not thumbnails - labeled 'Home' & 'Switch'.

The Mouse cursor was visible & moveable but clicking on a Thumbnail just closed the Window Selector, as did using mother means of selection, except 'Tab'.

So, it did  work, but rather differently to the 3d version, and neither crashed..

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-08-27
> **bogan said:**
> Hi!, **Cavsfan**,

No, this was in ubuntu/unity3d.

Using 'Alt+Tab', the Mouse cursor did not work - ie was not visible - so you navigate with the Cursor keys, & release 'Alt' or press 'Enter' to select the highlighted choice.

In Gnome Classic (no effects) you have the open window files listed in the bottom panel, so I had not tried it until now. At first I thought it was not working, but...:

Pressing 'Alt+Tab' displayed Thumbnails for all the four open windows, repeatedly pressing 'Tab' altered the highlight, and releasing 'Alt'  selected it. [Two File manager windows were represented by  Icons - not thumbnails - labeled 'Home' & 'Switch'.

The Mouse cursor was visible & moveable but clicking on a Thumbnail just closed the Window Selector, as did using mother means of selection, except 'Tab'.

So, it did  work, but rather differently to the 3d version, and neither crashed..

Chao!, **bogan.**

Hi **bogan**!

I have only tried Unity which works well and Gnome Classic with effects.
That is where I cannot get alt+tab to work.
I'll have to try out Gnome Classic no effects to see what I get.

Thanks!

---

### Post by bogan on 2012-08-28
Hi!, **Cavsfan**,

Correct, in Gnome Classic ( with effects) 'Alt+Tab' does nothing at all. But you do have the bottom Panel listing.

Neither, there, does pressing the 'Super' Key [ Win/MS Keys] show the list of Hot Keys settings.

Chao!,** bogan**.

---

### Post by Cavsfan on 2012-08-28
> **bogan said:**
> Hi!, **Cavsfan**,

Correct, in Gnome Classic ( with effects) 'Alt+Tab' does nothing at all. But you do have the bottom Panel listing.

Neither, there, does pressing the 'Super' Key [ Win/MS Keys] show the list of Hot Keys settings.

Chao!,** bogan**.

Pressing the super key does not do anything in Gnome Classic with effects. I pressed alt+tab and a bunch of garbage displayed.
So, I opened CCSM and unchecked the windows switcher and it froze for about 5 minutes.
I was able to logout and after a long time, the login screen appeared. I think I will just stick with Unity.
Thanks!

Note: I tried Gnome Classic (no effects) Cairo Dock had a black box around it probably because it is in Startup programs as cairo-dock -o.
So I opened a terminal and entered killall cairo-dock then cairo-dock & without the -o for open gl and got the same black box.
I'm just going to stick with Unity, the other options are not worth messing with IMO.

---

### Post by Paddy Landau on 2012-08-28
> **Cavsfan said:**
> Gnome Classic (no effects) Cairo Dock…
I wouldn't try to use features such as Cairo Dock with Ubuntu. Rather try Cairo Dock with alternatives such as Kubuntu, Xubuntu, or some other distro. Ubuntu is geared specifically towards Unity, and Gnome Classic was included as (I believe) a just-in-case fall-back.

---

### Post by Cavsfan on 2012-08-28
> **Paddy Landau said:**
> I wouldn't try to use features such as Cairo Dock with Ubuntu. Rather try Cairo Dock with alternatives such as Kubuntu, Xubuntu, or some other distro. Ubuntu is geared specifically towards Unity, and Gnome Classic was included as (I believe) a just-in-case fall-back.

With regular Ubuntu Unity Cairo Dock, Compiz, the cube and the whole nine yards work flawlessly.
But, not on the other login options. I am done messing with them any way. I will just use Unity and deal with that.
I don't understand why they had to get so far away from how Lucid Lynx works. That IMO is the best version I have dealt with.
But, that is off topic.

Unity + Cairo Dock = works great!

---

### Post by Paddy Landau on 2012-08-28
> **Cavsfan said:**
> With regular Ubuntu Unity Cairo Dock, Compiz, the cube and the whole nine yards work flawlessly.
You got the Cube to work flawlessly with 12.04? I'm amazed, because there are a couple of known bugs that cause problems with Unity; I myself have problems with them. I am not using the Cube until the bugs are fixed.

---

### Post by Cavsfan on 2012-08-29
> **Paddy Landau said:**
> You got the Cube to work flawlessly with 12.04? I'm amazed, because there are a couple of known bugs that cause problems with Unity; I myself have problems with them. I am not using the Cube until the bugs are fixed.

Yes CCSM, Compiz, Cairo Dock and even Emerald windows decorator work pretty well and I got everything except Emerald from the regular repositories using Synaptic.
I installed Emerald from this site: [[COLOR=blue]_http://ubuntuportal.com/2012/06/http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html_[/COLOR]](http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html)

Occasionally I have to reload the windows manager because the min, max, close button disappear from the top right of windows but, they are still there a mouse over shows I just cannot see them.
But, that solves the problem when I reload it. 
The only time I have had any problem is with anything other than Unity. It crashes all the time in Classic Gnome No effect and with Effects. 
Which is why I am sticking with Unity.
They all even work great on 12.10 Unity as well.

---

### Post by MoebusNet on 2012-09-03
Restore Missing Volume Button to System Tray After Upgrade to Ubuntu 12.04 (Gnome 3 Classic/Fallback)

May 10, 2012 by Ubuntu Genius

Please note: this is an updated version of the guide for restoring the volume button in Ubuntu 10.04/Gnome 2, and is specifically for those using the Gnome 3 “Classic” (Fallback) desktop (though may be applicable for Gnome-Shell and Unity).

&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;&#920;

If you’ve just upgraded to 12.04 “Precise Pangolin” and found that the volume icon/button is missing from the system tray (at the far-right of the top Gnome panel), you can choose between adding the newer indicator applet, or running the old stand-alone volume button like back in Gnome 2. With the indicator applet, it will load automatically with each boot, but it doesn’t take much to get the legacy volume button to do the same.

Volume Button:

Note: Those who’ve had to do this before in Ubuntu 10.04 through to 11.10 will have noted the package gnome-volume-control-applet no longer exists, but since it has just been renamed, all you need to do is change the command to gnome-sound-applet.

To run it for the current session, hit Alt+F2 to open the Run Application app, paste gnome-sound-applet into the text field, and click the Run button (you can also enter the command into a terminal, but the button will disappear if you close the terminal).

To get it to start automatically from the next reboot, click the cog in the top-right (in Unity) and open Startup Applications and add it as a new entry with a name like “Volume Button”. If you’re using Gnome Classic, your user menu in the top-right won’t include Startup Applications, so just run gnome-session-properties via Alt+F2 or in a terminal.

If for some reason the volume app is missing on your system, run sudo apt-get install gnome-sound-applet in the terminal.

Indicator Applet:

Alt+Right-click an empty area of the panel (if you have Compiz effects enabled, then you will need to hold Alt+Super/Windows while right-clicking), choose Add to Panel, then drag Indicator Applet Complete to next to the clock in the system tray, or wherever you want to put it instead. The volume button will be restored, but as part of the Indicator Applet which also has a mail/message notifier for Evolution and messaging apps, as well as showing when other apps like Rhythmbox music player are open.

I found this here: [http://ubuntugenius.wordpress.com/2012/05/10/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-12-04-gnome-3-classicfallback/](http://ubuntugenius.wordpress.com/2012/05/10/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-12-04-gnome-3-classicfallback/)

This worked for me.

---

### Post by Jamie_Edwards on 2012-09-05
> **Zukaro said:**
> Default Ubuntu wallpapers will also become the login screen wallpaper (if used as your desktop wallpaper).  This is a feature, however, it doesn't work with custom wallpapers (which is a bug).  If you're using your own wallpaper it wont appear on the login screen; the way to fix this is to copy it into /usr/share/backgrounds and then set the permissions to read only (set "group" and "other" permissions to read only).

You wont be able to drag the file to the folder as the folder is owned by root, so type "sudo mv /home/username/Pictures/wallpaper.jpg /usr/share/backgrounds" (make sure there's a space between locations); then go to the directory, find the file, right click, go into permissions and change group and other to read only (you're still the owner of the file, which is why you don't need to change permissions through the terminal).

Then to use the wallpaper just select it as your desktop wallpaper and it will also become your login screen wallpaper.

If you want your login screen wallpaper different from your desktop wallpaper download Ubuntu Tweak Tool and follow all the same steps above with the image you want to use instead; then just choose that image in Ubuntu Tweak Tool.




I found out about this bug and the fact the permissions were the issue here:
[https://bugs.launchpad.net/ubuntu-tweak/+bug/888186](https://bugs.launchpad.net/ubuntu-tweak/+bug/888186)

I don't know if this has already been mentioned but for those who don't like working in the terminal and would rather have a gui, I found another way to copy and paste non-default wallpapers into "usr/share/backgrounds"

NOTE: The following done using Nautilus, it might work with other File Managers but I don't know.

I pressed **ALT** + **F2**

This then opens a "Enter command" prompt.
Enter the following:
```
gksu nautilus
```

Another prompt will open asking for your password so enter it.

A new window will appear saying "Home" this is nautilus but with root privileges.

Here I like to middle click "File System" so that two tabs open in the window.

In the first tab navigate to your "Home" folder by clicking
```
File System/usr/[usr_name]/then_location_where_wallpapers_are_saved_to
```

Obviously clicking on the relevant folders to you.

right click on intended wallpaper and click "copy".

in the second tab navigate to
```
File System/usr/share/backgrounds
```

then right click and press "paste".

The wallpaper will then show up on the login screen.

---

### Post by Cavsfan on 2012-09-06
> **Jamie_Edwards said:**
> 
```
gksu nautilus
```

One thing: I was told **gksu nautilus** is no longer supported.
The alternative way is to enter **sudo -s**, enter your password and then enter **nautilus**.
You get the same results.
See the 2nd comment [[color=blue]_here_[/COLOR]](https://bugzilla.gnome.org/show_bug.cgi?id=654184) and the last comment [[color=blue]_here_[/COLOR]](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805682).

---

### Post by Cavsfan on 2012-09-06
Just wondering if there is a work around for this:
When I want to restart, I have to click on the Shutdown option in the dropdown list from the gear at the top right.
Then I have to select Restart on the left side of the box. I sometimes mistakenly click on the Shutdown box by mistake.

Is there a way to put "Restart" as an option there.
Quantal Quetzel 12.10 has "Restart" as an option in that same place.

---

### Post by bogan on 2012-09-06
Hi!, **Cavsfan**,

You Posted: > One thing: I was told **gksu nautilus** is no longer supported.I do not understand this as even if no longer supported it certainly still works with 12.04.1.

Further more the 'delay' is only there if you do not give nautilus a Path &/or a file.

When the resulting window is closed, I get a window full of error messages, repeating the first line of the following: ```
(nautilus:2608): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1628:19: Not using units is deprecated. Assuming 'px'.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```If I use your suggestion { 'sudo-s'  and 'nautilus'} then I indeed get a noticeable delay, starting with a message: ```
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension
```Followed by EIGHT full screens of those messages , ending with the same 'usershare' message as above.

So I shall continue use gksu for both gedit and nautilus.

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-09-06
Bogan,
I am just the messenger. I was told by someone else not to use **gksu nautilus** as it is no longer supported.
Those 2 links I mentioned have quotes from a developer not to use it.
"You shouldn't run nautilus as root." is what the 1st link says.

I cannot explain why as I do not know but, I know that in earlier versions of Ubuntu **nautilus-gksu** was available via Synaptic as a program to install.
As you know, this installed an option in Nautilus to "open as administrator".
It is no longer available for Ubuntu.

I used to run **sudo bleachbit** to delete cache etc. and was informed that sudo is not for GUI apps. 
There is a bleachbit as root program that is also installed which would most probably be identical to **gksu bleachbit**.
I see people still using sudo bleachbit and tried to mention that they should be using gksu but, was told sudo works.
I even posted a link that explained sudo vs gksu but, never seen any response.

So, my point would be I guess that just because something works, if it is not supposed to be used that way, there may be unintended results.

Like using sudo instead of gksu. It works great but, I have read that eventually it can cause harm.

I still use **gksu gedit** regularly as it is the correct way to edit a GUI like gedit. I am trying to get used to **gksu leafpad** but, the change is hard to make stick.

All those error messages you see when you use **gksu nautilus** in terminal may be a sign.
One more knowledgeable than I would have to explain why it not supposed to be used and no longer supported.

---

### Post by Paddy Landau on 2012-09-07
Don't use [FONT=Lucida Console]sudo[/FONT] for GUI programs.

Use [FONT=Lucida Console]gksudo[/FONT] (rather than [FONT=Lucida Console]gksu[/FONT]).

It's perfectly fine to use [FONT=Lucida Console]gksudo[/FONT] [FONT=Lucida Console]nautilus[/FONT]. Don't worry about the messages in the terminal; they are not important. If you use [FONT=Lucida Console]Alt+F2[/FONT], you won't see them anyway.

I personally have no delay when using [FONT=Lucida Console]gksudo[/FONT] [FONT=Lucida Console]nautilus[/FONT].

---

### Post by bogan on 2012-09-07
Hi!, **Paddy Landau,**

Thanks for the tip, I had never tried 'gksudo', all the advice I had seen said use 'gksu'.

You are right, 'gksudo nautilus' gives only a slight delay, but 7 screens of Gtk-WARNING messages when the window is closed.

But 'gksudo nautilus /boot/grub' [for instance] gives no delay and no warning messages, only:```
:~$ gksudo nautilus /boot/grub
Initializing nautilus-gdu extension # Window opens: When closed:
Shutting down nautilus-gdu extension
:~$ 
```Chao!, **bogan**.

---

### Post by Paddy Landau on 2012-09-07
> **bogan said:**
> I had never tried 'gksudo', all the advice I had seen said use 'gksu'.
[FONT=Lucida Console][COLOR=Navy]gksu[/COLOR][/FONT] and [FONT=Lucida Console][COLOR=Navy]gksudo[/COLOR][/FONT] are in fact the very same program, but the two commands respond differently. [FONT=Lucida Console][COLOR=Navy]gksudo[/COLOR][/FONT] is [FONT=Lucida Console][COLOR=Navy]gksu[/COLOR][/FONT] but in sudo mode. [FONT=Lucida Console][COLOR=Navy]gksudo[/COLOR][/FONT] is equivalent to [FONT=Lucida Console][COLOR=Navy]gksu[/COLOR][/FONT][COLOR=Navy] [FONT=Lucida Console]--sudo-mode[/FONT][/COLOR].

The technical differences below are highlighted by the different values of three environment variables, as follows.
```
sudo:
    ${USER}       (target)    root
    ${HOME}       (unchanged)    /home/paddy
    ${PATH}       (target)    target user's path

sudo -H
    ${USER}       (target)    root
    ${HOME}       (target)    /root
    ${PATH}       (target)    target user's path

sudo su:
    ${USER}       (target)    root
    ${HOME}       (target)    /root
    ${PATH}       (unchanged)    your path

gksudo (or gksu --sudo-mode):
    ${USER}       (target)    root
    ${HOME}       (target)    /root
    ${PATH}       (target)    target user's path

gksu:
    [FONT=Tahoma]Supposedly the same as [/FONT][FONT=Lucida Console]gksudo[/FONT][FONT=Tahoma], but there are unexpected
[/FONT]    [FONT=Tahoma]results from some commands, e.g. [[FONT=Lucida Console]find[/FONT] when using regex]("http://ubuntuforums.org/showthread.php?t=1819589").[/FONT]
```

---

### Post by Cavsfan on 2012-09-07
> **Paddy Landau said:**
> Don't use [FONT=Lucida Console]sudo[/FONT] for GUI programs.

Use [FONT=Lucida Console]gksudo[/FONT] (rather than [FONT=Lucida Console]gksu[/FONT]).

It's perfectly fine to use [FONT=Lucida Console]gksudo[/FONT] [FONT=Lucida Console]nautilus[/FONT]. Don't worry about the messages in the terminal; they are not important. If you use [FONT=Lucida Console]Alt+F2[/FONT], you won't see them anyway.

I personally have no delay when using [FONT=Lucida Console]gksudo[/FONT] [FONT=Lucida Console]nautilus[/FONT].

Gksudo is is just symlinked to gksu.

Enter this in terminal:
```
ls -l /usr/bin/gksudo
```

I had wondered what the difference was between gksudo and gksu myself.

[http://askubuntu.com/questions/21033/what-is-the-difference-between-gksudo-and-gksu](http://askubuntu.com/questions/21033/what-is-the-difference-between-gksudo-and-gksu)

---

### Post by Paddy Landau on 2012-09-07
> **Cavsfan said:**
> Gksudo is is just symlinked to gksu.
Yes, I am aware of that. However, the program obviously looks at how it was called, because the two do give different results.

See [FONT=Lucida Console]man[/FONT] [FONT=Lucida Console]gksu[/FONT] to read about the differences. [FONT=Lucida Console]gksu[/FONT] uses [FONT=Lucida Console]su[/FONT] as its back-end, while [FONT=Lucida Console]gksudo[/FONT] uses [FONT=Lucida Console]sudo[/FONT] (unless you force it otherwise with [FONT=Lucida Console]--su-mode[/FONT] or [FONT=Lucida Console]--sudo-mode[/FONT]).

---

### Post by Cavsfan on 2012-09-07
man gksu says this:

Notice that all the magic is done by the underlying library, **libgksu**. Also notice that [B]the library will decide if it should use su or sudo as 
backend[/B] using the /apps/gksu/sudo-mode gconf  key, if you call the gksu command. You can force the backend by using the gksudo command, 
or by using the --sudo-mode and --su-mode options.

This appears to me to indicate that when using gksu the underlying library libgksu determines if it should use su or sudo as backend.
Unless you force the backend by using gksudo.

Not meaning to argue here just wanting a clear explanation and the above conflicts with what you are saying at least I think it does.

---

### Post by Paddy Landau on 2012-09-07
Thanks for the extra info, Cavsfan.

The important thing is to use [FONT=Lucida Console]gksudo[/FONT] with Ubuntu unless you have a specific reason for using [FONT=Lucida Console]gksu[/FONT].

---

### Post by Cavsfan on 2012-09-07
> **Paddy Landau said:**
> Thanks for the extra info, Cavsfan.

The important thing is to use [FONT=Lucida Console]gksudo[/FONT] with Ubuntu unless you have a specific reason for using [FONT=Lucida Console]gksu[/FONT].

You are welcome Paddy. Every once in a while I stumble across something useful.
Doesn't the above say that when you use gksu, the library decides if su or sudo is used?

I looked in gconfig editor in /apps/gksu and see that sudo-mode is checked.

According to that link I provided both commands are exactly the same.
The big thing that is mentioned over and over is not to use sudo on GUI, but to use gksu.

Here is a post from 2006 that says they are exactly the same and nothing appears to have changed since then.

[http://ubuntuforums.org/showpost.php?p=1761503&postcount=14](http://ubuntuforums.org/showpost.php?p=1761503&postcount=14)

I cannot find anything that supports there is a difference between **gksu** and **gksudo**.

---

### Post by Paddy Landau on 2012-09-08
> **Cavsfan said:**
> According to that link I provided both commands are exactly the same.
…
I cannot find anything that supports there is a difference between **gksu** and **gksudo**.
From the manual:
> gksu is a frontend to su and gksudo is a frontend to sudo.This is unless you explicitly use [FONT=Lucida Console]--su-mode[/FONT] or [FONT=Lucida Console]--sudo-mode[/FONT].

So, they are different to the extent that [FONT=Lucida Console]su[/FONT] and [FONT=Lucida Console]sudo[/FONT] differ. I have shown some differences in [post=12223323]post #152[/post], but I would like to know what other differences there are.

*In theory*, [FONT=Lucida Console]gksu[/FONT] and [FONT=Lucida Console]gksudo[/FONT] on Ubuntu should be identical. In practice, they are different. The difference that I have found is subtle but can lead to disastrous results; specifically, *regex* commands can give unexpected results. I found out the hard way when I used [FONT=Lucida Console]gksu find … -regex … -delete[/FONT], and ended up deleting some system files. [See a discussion]("http://ubuntuforums.org/showthread.php?t=1819589") that I raised on this (at the time of writing, I had not yet realised that I had deleted system files).

---

### Post by Cavsfan on 2012-09-09
Paddy, I am not trying to argue with you but, I still do not find any proof that there is a difference between a file and a symbolic link to that very same file.

```
cavsfan@cavsfan-MS-7529:~$ ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 Sep  4 10:11 [COLOR="#00CED1"]/usr/bin/gksudo[/COLOR] -> [COLOR="Green"]gksu[/COLOR]
cavsfan@cavsfan-MS-7529:~$
```
They act as the same file. The only difference I can find is "Symbolic links may refer to directories and may cross file system boundaries."

[[color=blue]_http://manpages.ubuntu.com/manpages/precise/man7/symlink.7.html_[/COLOR]](http://manpages.ubuntu.com/manpages/precise/man7/symlink.7.html)

BTW, is there any workaround to get a restart option in the drop down list when you click on the gear in the top right corner as I mentioned in post [[color=blue]_#147_[/COLOR]](http://ubuntuforums.org/showpost.php?p=12221666&postcount=147)?

I will also mention that I did a clean install of 12.04.1 and it did not come with Gnome Classic and with the way that was working for me,
I am not even going to install it. I'll just stick with Unity and like it. :)

---

### Post by Paddy Landau on 2012-09-09
> **Cavsfan said:**
> Paddy, I am not trying to argue with you but, I still do not find any proof that there is a difference between a file and a symbolic link to that very same file.
Cavsfan, I've already given you [the proof]("http://ubuntuforums.org/showthread.php?t=1819589") more than once. You can choose to disbelieve it, or you can do it yourself and see the results with your own eyes.

You are right that [FONT=Lucida Console]gksudo[/FONT] is just a symbolic link to [FONT=Lucida Console]gksu[/FONT]. But you are wrong that [FONT=Lucida Console]gksu[/FONT] is unable to tell the difference.

A program is able to tell how it was called. Therefore, if you call [FONT=Lucida Console]gksu[/FONT] using [FONT=Lucida Console]gksudo[/FONT], it is able to tell that it was called as [FONT=Lucida Console]gksudo[/FONT] and not [FONT=Lucida Console]gksu[/FONT]. It's a trivial thing to do and I myself have scripted this sort of behaviour before. The program [FONT=Lucida Console]gksu[/FONT] simply checks how it was called, and adjusts its behaviour accordingly unless overridden with [FONT=Lucida Console]--su-mode[/FONT] or [FONT=Lucida Console]--sudo-mode[/FONT].

---

### Post by Cavsfan on 2012-09-26
I am not sure if this has been mentioned before but, when in gnome classic I looked up at the date/time all I seen was the time.
No date was displayed.

I found a way to fix that [[COLOR=blue]_here._[/COLOR]]("http://askubuntu.com/questions/129985/how-to-make-the-date-appear-next-to-the-time-indicator-in-gnome-classic")

BTW, Precise whether in Unity or Gnome Classic is really working well as you would expect from an LTS.

---

### Post by Freecore on 2012-11-11
I've recopiled the temporary solutions to the Bug 796076.

When you run "gksudo gedit /path/of/file" gedit tries to open an untitled document and keeps loading it.

The recopilation can be found on comment #25.

[http://bugs.launchpad.net/gedit/+bug/796076](http://bugs.launchpad.net/gedit/+bug/796076)

---

### Post by Linuxisfast on 2012-11-11
> **Freecore said:**
> I've recopiled the temporary solutions to the Bug 796076.

When you run "gksudo gedit /path/of/file" gedit tries to open an untitled document and keeps loading it.

The recopilation can be found on comment #25.

[http://bugs.launchpad.net/gedit/+bug/796076](http://bugs.launchpad.net/gedit/+bug/796076)

Yep confirmed this bug as well on launchpad, I get the same with Ubuntu Quantal x64.

---

### Post by fballem on 2012-11-11
> **whatthefunk said:**
> Crap Nvidia driver included on .iso.  Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

Reboot and you should be good to go.

This actually can be a larger problem, since on some nVidia cards, the driver simply won't work and ubuntu 12.04 will not boot. If this applies to you, then you will need to do a special installation process, which is described here: [https://wiki.ubuntu.com/fballem/Software%2012.04#Installation](https://wiki.ubuntu.com/fballem/Software%2012.04#Installation)

---

### Post by Paddy Landau on 2012-11-12
> **Freecore said:**
> When you run "gksudo gedit /path/of/file" gedit tries to open an untitled document and keeps loading it.
Thanks to Freecore, my [post=12071894]original post giving a workaround[/post] is now redundant. Freecore found out that there is a much simpler way; just use gksudo twice, as follows.
```
gksudo gksudo gedit *<file>*
```It works perfectly!

---

### Post by Cavsfan on 2013-01-20
A couple of days ago I installed gdm (gnome display manager) via SPM in Precise. I chose lightdm to be the default display manager but, 
still thought I would never be able to get back in to Precise. Since Precise's recovery mode is "read only" on all file systems I found very little I could do.

Then I stumbled upon a thread about recovery being read only and **Paddy Landau** had filed a bug. I cannot find that bug right now but I did note that Paddy had entered this in the comments of the bug as a workaround:
Login to recovery and drop to root shell and enter these:
```
mount --options remount,rw /
mount --all
```I was then able to enter **sudo dpkg-reconfigure lightdm** without getting an error. I also purged gdm.
But, still when it booted up normally in gnome classic mode it would not get past the black screen with 4 dots changing to yellow and never going anywhere.
However, I found I could press ALT+F2 and get a login prompt. Once logged in I could start lightdm with **sudo service start lightdm** and it would then login normally.

By, now I know that lightdm is just not starting at bootup. I found this thread with the fix:
[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=2049203_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2049203")

It told how **sudo dpkg-reconfigure lightdm** only put "lightdm" in **/etc/X11/default-display-manager**.
But, if you edited that file and put **usr/sbin/lightdm** in place of **lightdm** it would fix the whole problem.

---

### Post by Paddy Landau on 2013-01-20
> **Cavsfan said:**
> I cannot find that bug right now…
[ Bug #996454]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454"). Vote for it if it affects you.

---

### Post by Cavsfan on 2013-01-20
> **Paddy Landau said:**
> [ Bug #996454]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454"). Vote for it if it affects you.

Done! I cannot believe there are only 11 (after me) people that claim to be affected by this. This was a nightmare!
Thanks for the workaround Paddy! That saved doing a clean install and at least a couple of days getting things back like they were.
I will have those notes available at all times. I am pretty sure everything after Precise opens as read only in recovery.

I think I'll try to install the latest Nvidia driver from Nvidia's website.

---

### Post by bogan on 2013-01-21
Hi!, **Cavsfan**.

"Done! I cannot believe there are only 11 (after me) people that claim to be affected by this".

Nor can I !

I just subscribed to it, and it now says:> **     Recovery Mode starts in read-only, does not mount home folder, and hangs when trying to do something    [Edit]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454/+edit") **


                       
[LIST=1]
[*]     [Ubuntu]("https://launchpad.net/ubuntu")
[*]     [“friendly-recovery” package]("https://launchpad.net/ubuntu/+source/friendly-recovery")
[*]     [Bugs]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery")
[*]     Bug #996454
[/LIST]
                                        Reported by       [Paddy Landau]("https://launchpad.net/%7Epaddy-landau")       on 2012-05-08                    
             
                                                                  You have subscribed to this bug report.
                             
                                                               
                        [52]("https://bugs.launchpad.net/+help-bugs/bug-heat.html")       
                                                                        [This bug affects you and 10 other people]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454/+affectsmetoo")           [             [IMG]https://bugs.launchpad.net/@@/edit[/IMG]           ]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454/+affectsmetoo")                
A BUG in a bug, maybe??

Chao!, **bogan.**

---

### Post by Paddy Landau on 2013-01-21
> **bogan said:**
> I just subscribed to it … A BUG in a bug, maybe??
Subscribing is not a vote (you may subscribe but not consider it a problem). You need to click on the green wording, and it will ask you whether or not it affects you. Click "Yes" and it will add your vote.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230425&stc=1&d=1358772780[/IMG]

---

### Post by bogan on 2013-01-21
Hi!, **Paddy**,

Yes, I did that, and I have just done it again.

All it does is to change the "Yes, it affects me" into  black text on a Red background, on a larger grey ground, and stays there. The number does not change.

If I click on the other line it changes to "This bug affects 10 people, but not you".

I am logged in and the righthand text shows: " You are s: subscribed to all notifications for this bug". [ The 's:' is a Pen Icon.]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230425&stc=1&d=1358772780[/IMG]" Yes,it affects me " on a[COLOR=Red] Red blackground block.[/COLOR] after clicking.


I wonder If I was already a 'voter', and the bug report system took that into account.

Chao!, **bogan.**

---

### Post by hawthornso23 on 2013-02-21
Can we have this thread made sticky again. Some of us are still using the LTS and plan to do so for some time.

---

### Post by CharlesA on 2013-02-21
> **hawthornso23 said:**
> Can we have this thread made sticky again. Some of us are still using the LTS and plan to do so for some time.
We usually only sticky the bugs and known workarounds threads for the latest release. If you need to find this thread in the future, you can either bookmark it or subscribe to it from the thread tools menu.

---

### Post by thatsmyboy on 2013-02-27
Upon closing Rhythmbox, Unity panel and menu bar become invisible as described in this link: [https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/894493]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/894493") 

Workaround :

Can recover visibility by pressing Super+S to reveal Spread (you see nothing however), and then hitting Escape. Then things return to normal.

---

### Post by Previous1 on 2014-01-09
**Catfish defaults to "catfish" folder ([bug #283953]("https://launchpad.net/bugs/283953"))**
Workaround: patch catfish.py
```
cd /usr/share/catfish
sudo sed -i 's/os.path.abspath(self.options.path)/os.path.abspath(os.path.expanduser(self.options.path))/' catfish.py
sudo sed -i 's/set_filename(os.path.expanduser(self.options.path))/set_current_folder(self.options.path)/' catfish.py
sudo rm catfish.pyc
sudo python -m compileall catfish.py
```


**Apparmor: evince/google-chrome ([bug #964510]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/964510"))**
Workaround: edit abstractions
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/964510/comments/12](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/964510/comments/12)


**Apparmor: no support for block_suspend ([bug #1199933]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1199933"))**
Workaround: patch apparmor
[http://ubuntuforums.org/showthread.php?t=2198529](http://ubuntuforums.org/showthread.php?t=2198529)
[https://launchpadlibrarian.net/156145963/foo.diff](https://launchpadlibrarian.net/156145963/foo.diff)


[B]Terminal doesn't scroll - Xubuntu
[/B]Workaround: replace with gnome-terminal
```
sudo apt-get remove xfce4-terminal
sudo apt-get install gnome-terminal
```


**Weather plugin shows "No Data" ([bug #1244629]("https://launchpad.net/bugs/1244629")) - Xubuntu**
Workaround: install Debian package
```
wget http://ftp.de.debian.org/debian/pool/main/x/xfce4-weather-plugin/xfce4-weather-plugin_0.7.4-4_i386.debsha256sum -c <<< "e45ae1610777e6913be36f206bb36a8f6b145de8f0bff0fe0581435b48f3cf7e  xfce4-weather-plugin_0.7.4-4_i386.deb" && sudo dpkg -i xfce4-weather-plugin_0.7.4-4_i386.deb
```


**Abiword doesn't scroll ([bug #960089]("https://bugs.launchpad.net/bugs/960089")) - Xubuntu**
Workaround: revert to 2.8.6
[http://xubuntugeek.blogspot.be/2013/02/how-to-downgrade-abiword-version-to-286.html](http://xubuntugeek.blogspot.be/2013/02/how-to-downgrade-abiword-version-to-286.html)


**Thunar delayed start ([bug #775117]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117")) - Xubuntu**
Workaround: disable automatic network mounts
```
sudo sed -i 's/AutoMount=true/AutoMount=false/' /usr/share/gvfs/mounts/network.mount
```

---


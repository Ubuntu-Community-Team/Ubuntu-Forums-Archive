---
title: "Unity Segmentation Fault on Ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by Hornet.ch on 2011-10-14
Hi

I upgraded to Oneiric Ocelot today and it worked fine first. Unity 3D also worked with the proprietary nvidia drivers. Now, Unity 3D doesn't work anymore. I tried the following:

```

unity --reset
unity --replace

```

But I always get a segmentation fault. With unity --replace I get countless warnings like "glib.glib-object <unknown>:0 invalid cast from 'BamfWindow' to 'BamfApplication'" followed by a "compiz (unity) - Warn : unsupported internal format" and a segmentation fault. unity --replace also segfaults after the message "unsupported internal format" message.

The nvidia driver doesn't seem to be the problem as I can start a Gnome Shell session with 3D support. And I didn't do much with the system. The only thing that might have been the trigger is that I tried to change Unity Launcher's icon size with ccsm.

Anyone an idea what to do?

Hornet

---

### Post by HulaBula on 2011-10-15
Try resetting all compiz settings first:
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm -r ~/.config/compiz-1/compizconfig/*
unity --reset --replace

Restart your system afterwards and unity should be running again.
Note that all your compiz-settings will be reset.

---

### Post by hwttdz on 2011-10-15
unity-greeter, lightdm and nvidia are not getting along in the current version in ubuntu 

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/833619](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/833619)

I avoided lightdm entirely for the time being and I'm using gdm to and xfce.

---

### Post by WorLord on 2011-10-15
> **hwttdz said:**
> unity-greeter, lightdm and nvidia are not getting along in the current version in ubuntu 

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/833619](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/833619)

I avoided lightdm entirely for the time being and I'm using gdm to and xfce.

Two computers here, using all three of those... not seeing this crash.

*shrug*

---

### Post by doubleeagle on 2011-10-18
Exact same issue here. Above solutions aren't working for me.

I've also tried uninstalling lightdm, unity & compiz with purge specified. Still the same issue.

Any other thoughts on what the issue might be?

---

### Post by Matyy on 2011-10-24
I get the same messages & a segmentation fault &#8211; but only since yesterday. I don't remember I changed anything, I restarted lightdm and since that I cannot launch to unity. Unity 2D & Gnome Shell work flawlessly.

But when I run "unity --replace" within Unity 2D &#8211; Unity 3D starts and works!

---

### Post by Matyy on 2011-10-24
After doing that – launching »unity --replace« from unity2d the normal unity launches again. Perhaps this helps someone…

---

### Post by EpoxyRepair on 2011-10-25
I've just upgraded to 11.10 on a Dell Inspiron 6400 laptop - roughly 6 years old, with an Intel chipset graphics card. I get a plain brown screen when I try to log in and find this in dmesg:

compiz[5413]: segfault at 0 ip 012fd746 sp bfbf2020 error 4 in libunityshell.so[1156000+20b000]
[ 3633.533213] compiz[5571]: segfault at 0 ip 01385746 sp bfa810e0 error 4 in libunityshell.so[11de000+20b000]

I'm able to log in to Unity 2D. But things appear to be working erratically and painfully slow

---

### Post by EpoxyRepair on 2011-10-26
As an update, i tried logging ctrl Al F2 and running unity --reset --replace and it ran reasonably well. I'm not sure if Unity is meant to leave you with an icon free desktop, but thats what I have.

Also I get these errors in my error log:

compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3a0057d!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3a00f5b!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3a01721!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.

And the following warnings...

WARN  2011-10-26 19:29:50 unity.iconloader IconLoader.cpp:401 Unable to load icon applications-microblogging-panel at size 24
WARN  2011-10-26 19:29:53 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-26 19:29:53 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-26 19:29:53 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-26 19:29:53 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-26 19:29:53 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-10-26 19:29:53 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2011-10-26 19:29:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/gwibber does not exist
WARN  2011-10-26 19:29:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/gwibber does not exist
WARN  2011-10-26 19:29:55 unity.iconloader IconLoader.cpp:401 Unable to load icon tray-message at size 24
WARN  2011-10-26 19:37:10 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2011-10-26 20:08:37 glib <unknown>:0 Failed to fetch type: Method "WindowType" with signature "" on interface "org.ayatana.bamf.window" doesn't exist

WARN  2011-10-26 20:08:37 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


Anyone got any ideas on where to go from here...system is usable, but this is not a pleasant experience

---

### Post by dpiddyTx on 2011-10-29
bump

---

### Post by Matyy on 2011-11-02
Well all I can do is login in unity-2d, unity --replace and kill the unity-2d processes. I am using unity2d right now...

---

### Post by Matyy on 2011-11-07
bump again…

please if someone knows where I could look. I don’t want to log into unity2d everyday just to start unity and kill unity2d.

---

### Post by EpoxyRepair on 2011-11-08
Hi Matty,

I was wondering what graphics card you have. Maybe by comparing notes we can get somewhere?

I've also tried installing gnome , but can only use gnome classic

---

### Post by Matyy on 2011-11-14
Hey, sry for the late reply. My graphics card is a nVidia Geforce 8600m.

---

### Post by meghakumar on 2012-04-23
Not sure if you still have this problem. I tried different commands I found on forums but nothing worked, so did this simple (but crude) solution --

1) Created a new user
2) rm -rf /home/problemuser/.config/compiz-1
3) rm -rf /home/problemuser/.compiz-1

(basically delete all your compiz settings)
(and now copy over settings from the new user)

4) sudo cp -r /home/newuser/.config/compiz-1 /home/problemuser/.config
5) sudo cp -r /home/newuser/.compiz-1 /home/problemuser/
6) sudo chown -R problemuser /home/problemuser/.config/compiz-1 /home/problemuser/.compiz-1
7) sudo reboot

This would reset all your compiz settings, but does bring back your workspace to how it used to be!

---


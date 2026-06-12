---
title: "Stopping the update notifier running"
date: 2010-02-05
forum: General Help
---

### Post by 9i8uy7trd on 2010-02-05
I am getting to the end of my tether with this..... What is actually triggering the update-notifier to be run at log on to a desktop environment?

I am using ubuntu something or other (damn code names... only the fan boys can easily remember which is which, and otherwise finding the version of ubuntu is a right farce.... OK, the apt sources are using hardy. What is that? 9.04? I dunno. Every other distro I've used has an /etc/*distroname*-version file, but not Ubuntu!).

The admin account (the first account created) on my Ubuntu machine is using XFCE rather than Gnome, and I have turned off the following to try and stop the nagging, and the phoning home:

* In software sources/updates, check for updates is off.
* In software sources/updates, show new distribution release is never.
* XFCE settings manager/autostarted apps/update notifier is unchecked. And now removed.
* XFCE settings manager/Sessions and startup/advanced/launch [gnome|KDE] services are both unticked.
*The update-notifier.desktop file has been removed from /etc/xdg/autostart

In the gconf-editor, there is supposedly a check box to turn off the notifier - it is not there.

And I daren't uninstall the update-notifier as the distro wants to remove ubuntu-desktop!

```
ps faux
[snip]
9i8uy7trd  10321  2.0  0.4  36244  6584 pts/0    S    20:59   0:00      \_ /usr/bin/xfce4-session
[snip]
9i8uy7trd  10333  0.8  0.4  20748  7468 pts/0    S    20:59   0:00          \_ update-notifier --sm-config-prefix /update-notifier-dp7ydV/ --sm-client-id 1158601782000125539555500000229180004 --screen 0

```So it is xfce4-session launching the update-nagifier. I cannot find anything in my XFCE config that might be launching the notifier (eg ~/.config/autostart dir contains no reference to the notifier).

I can't believe Windows makes things like this so much easier!

---

### Post by serpentracer on 2010-02-05
I wonder if you need to do it as root user to really get it to completely stop.

---

### Post by 9i8uy7trd on 2010-02-05
> **serpentracer said:**
> I wonder if you need to do it as root user to really get it to completely stop.

The GUI elements that need root ask for it, and otherwise settings are user settings (update-notifier runs as a user, launched from a user's process), so changing things as root would make no difference.

I obviously used the root account to move stuff out of /etc/xdg/autostart

---

### Post by 9i8uy7trd on 2010-02-08
Anyone got any ideas then?  I've not looked into this much more, but I can confirm that if the update-notifier process is killed, and then synaptic is run, the update-notifier doesn't get restarted. This says to me that the update-notifier isn't very closely tied to apt, and as it runs when the desktop environment is started, it's more to do with that.

---

### Post by gmargo on 2010-02-08
> **9i8uy7trd said:**
> Every other distro I've used has an /etc/*distroname*-version file, but not Ubuntu!).

The *Linux Standards Base* specification calls for this information to be provided by the **lsb_release** command: [http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/lsbrelease.html](http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/lsbrelease.html)

In Ubuntu, you can use the **lsb_release** command or view the file **/etc/lsb-release**. 
```

$ **lsb_release** -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.4 LTS
Release:        8.04
Codename:       hardy

$ cat **/etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

```

---

### Post by 9i8uy7trd on 2010-02-08
> **gmargo said:**
> The *Linux Standards Base* specification calls for this information to be provided by the **lsb_release** command: [http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/lsbrelease.html](http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/lsbrelease.html)


Ahh, cheers, didn't know about that! I assumed that /etc/distroname-version was the standard, but it's obviously not that straightforward, seeing as my Ubuntu 8.04.4 LTS machine has a file /etc/debian-version (containing the codename version of Debian that Ubuntu is based on).

---

### Post by ajventi on 2010-02-17
Well having recently migrated to Xfce myself in order to cut all the fat that gnome consumes, I came across the same problem, and seeing that there was no solution in this thread, I figured I'd try and figure it out.

In short I traced through a bunch of conf files and shell scripts starting at /etc/gdm/gdm.conf

I ended up in /etc/xdg/xfce4/xinitrc 

If you use xfce4-session (the session manager) it controls what's autostarted, since I use the session manager, this is how I fixed it. I read the man page:

> xfce4-session uses the contents of the ~/.cache/sessions/

So First I tried manually killing update-notifier saving my session and logging out, no luck. So I logged out again, logged in on a text tty and edited the most recent file I found in ~/.cache/sessions/. Searching for update-notifier I found the following lines:


> Client2_ClientId=11c0a80102000126634175400000055460004
Client2_Hostname=local/alpha
Client2_CloneCommand=update-notifier,--sm-config-prefix,/update-notifier-EUDRba/
Client2_CurrentDirectory=/home/anthony
Client2_Program=update-notifier
Client2_RestartCommand=**update-notifier**,--sm-config-prefix,/update-notifier-EUDRba/,--sm-client-id,11c0a80102000126634175400000055460004,--screen,0
Client2_RestartStyleHint=1
Client2_UserId=anthony

So I assumed anything with a Client2_ prefix was controllong update-notifier, deleted those lines, logged back in to xfce and the problem is solved.

Now if you don't use xfce-session I'm assuming you should edit /etc/xdg/autostart/update-notifier.desktop:

> [Desktop Entry]
Encoding=UTF-8
Name=Update Notifier
Comment=Update notification daemon
Icon=update-notifier
Exec=update-notifier
Terminal=false
Type=Application
Categories=
**OnlyShowIn=GNOME;XFCE;**
X-Ubuntu-Gettext-Domain=update-notifier

Delete "XFCE;" from the line that says "OnlyShowIn" and it should work. Again, I can't guarantee this will work, but from what I read in the startup scripts (namely /etc/xdg/xfce4/xinitrc) this should remedy the problem.

---

### Post by OrangeCrate on 2010-02-17
> **9i8uy7trd said:**
> I am getting to the end of my tether with this..... **What is actually triggering the update-notifier to be run at log on to a desktop environment?**

Unless I'm grossly misunderstanding what your attempting to do, why don't you just go to System > Preferences > Startup Applications > and uncheck "Update Notifier"? Then it won't run at startup.


> **I am using ubuntu something or other (damn code names... only the fan boys can easily remember which is which,** and otherwise finding the version of ubuntu is a right farce.... OK, the apt sources are using hardy. What is that? 9.04? I dunno. Every other distro I've used has an /etc/*distroname*-version file, but not Ubuntu!).

<snip>



LOL, the first number of a version is the year, the second number is the month of release. 9.04 was released in April of 2009. 9.10 was release in October of 2009. 10.04 will be released in April of 2010.

---


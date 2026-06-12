---
title: "Lost launch bar and Top Menu!!!!"
date: 2012-09-10
forum: General Help
---

### Post by Ace..... on 2012-09-10
12.04 LTS

I definitely need help.
I'm typing this in Win.

I ran update & install.

I then installed Ubuntu Tweek.

I ran the janitor in all innocence assuming it was well sorted (I'd read reviews that it was mature and very good).

It deleted everything it found was deletable.

I looked at all the options, but only tried one, which was launch bar display in m/s.

It has been a bit quick to appear, so I tried sliding the delay bar and checking for change.

left it very low, figuring maybe a reboot is needed.

I rebooted and ran memtest, but stopped at 25% thinking I'll run it tonight.

let it boot into ubuntu, but neither launch bar or top menu appeared.

rebooted to recovery mode and ran the file system test.

rebooted normal (no change).
rebooted normal again (no change).

The only desktop icons are wine related, but the progs do run.

Right clicking provides access to All Settings, including Ubuntu Tweek - which runs fine.

So it _seems_ like ubuntu is functioning, only that I have no access to any menus or launch bar.

Created a 2nd account, but that displays a blank desktop.

Ctrl alt delete allows log out, and at the log in screen it DOES display the Top Menu

I read another post suggesting sudo reboot would work, but it just rebooted.
However I learned that Ctrl Alt T brings up the terminal.

Typed Firefox, and it launches, as does google-chrome.


Can anyone help me please?

---

### Post by cortman on 2012-09-10
You may have accidentally removed Unity. Run

```
sudo apt-get install ubuntu-desktop
```

To make sure it's still installed, and if not to install it.

---

### Post by Ace..... on 2012-09-10
Thanks for the response.... here's the outcome:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

seems no point in rebooting cos nothing has happened.

hmmmmm what to do now?

Install a different desktop perhaps?

I'm reporting a bug at tweak, cos it surely must be their fault.

I'm not panicking.... we can surely fix this cos all progs seem to be working ok.

gonna post to tweak now.

---

### Post by cortman on 2012-09-10
Ok- should have just included this one in my original post- but oh well:

```
sudo apt-get install unity --reinstall
```

---

### Post by Ace..... on 2012-09-10
Action occured:)


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,285 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise-updates/main unity amd64 5.14.0-0ubuntu1 [1,285 kB]
Fetched 1,285 kB in 3s (428 kB/s)  
(Reading database ... 209204 files and directories currently installed.)
Preparing to replace unity 5.14.0-0ubuntu1 (using .../unity_5.14.0-0ubuntu1_amd64.deb) ...
Unpacking replacement unity ...
Processing triggers for man-db ...
Setting up unity (5.14.0-0ubuntu1) ...


Okay... time for a reboot methinks.

---

### Post by Ace..... on 2012-09-10
Sorry to say, but no joy.

Ran the full reboot and no change.

Wow - it must be something different.

cos terminal stated '1 reinstalled'

Note: I've tried changing display settings, in case they were 'off screen'.

okay.... it wants us to try harder. :rolleyes:

---

### Post by jerome1232 on 2012-09-10
I would try reseting unity

```

unity --reset
```Log out then log back in.

If that doesn't work I would try reseting unity and compiz from a tty (that means print this out or something, press ctrl+alt+f1, login and start typing) reboot after all of that is done.

```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
unity --reset
```

---

### Post by Ace..... on 2012-09-10
did ctrl alt f1

ended with a blank screen ie no log in

did ctrl alt del and it went to full reboot.

maybe that tells us something.

gonna eat now.

check you later.

thanks for the help:)

---

### Post by jerome1232 on 2012-09-10
Your tty's aren't working? You should've had a black screen with a very small text login prompt at the top left and btw ctrl+alt+f7 should've gotten you back to a gui, I guess I should've mention that.

Try from a gnome-terminal then, you did say that worked right?

---

### Post by Ace..... on 2012-09-10
Okay.
I copied and pasted the text in one go, into terminal.
Note there was alot of screen activity, but I remained with a functioning browser.


Here's the result in terminal:

(note: "titlebar' is set to an invalid value" --- interesting maybe)
```

name:~$ gconftool-2 --recursive-unset /apps/compiz-1
name:~$ gconftool-2 --recursive-unset /apps/compizconfig-1
name:~$ rm ~/.compiz-1/session/*
name:~$ rm ~/.config/compiz-1/compizconfig/config
name:~$ unity --reset
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Window manager warning: GConf key '/apps/metacity/general/action_double_click_titlebar' is set to an invalid value

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:2527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/mark/.compiz/session to /home/mark/.compiz-1/session
[LOG]: Copied file /home/mark/.compiz/session/10b1c004487528854b134730664117978000000018880042 to /home/mark/.compiz-1/session/10b1c004487528854b134730664117978000000018880042
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1a00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x280002f

Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
compiz (core) - Warn: unhandled ConfigureNotify on 0xe00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing animation options...done
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing cube options...done
Initializing decor options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing grid options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x240025f

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x240026d

```
I'll reboot.

---

### Post by Ace..... on 2012-09-10
(note: previous page/post is the data output listing)

I've logged a bug on the tweak website, and raised a question here:

[https://answers.launchpad.net/ubuntu-tweak-website/+question/208213](https://answers.launchpad.net/ubuntu-tweak-website/+question/208213)

I am presuming that Tweak Janitor failed to identify the files that should not have been flagged for deletion.

I've posted this thread link to allow their team to view the data we are producing.

Hopefully we will be able to establish what was deleted, to enable them to make the necessary mods.

I've only positive thoughts.

We'll fix this, and in so doing we'll all advance. ;)

---

### Post by cortman on 2012-09-10
Good job filing the bug and staying positive. :)

This looks like a case for reinstallation to me.

---

### Post by PaulInBHC on 2012-09-11
I had two installs on partitions and broke both of them with ubuntu tweaks.

I ended up formatting and combining the partitions and reinstalling 12.04 from the CD. 

I'm not installing tweaks again.

BTW I tried every terminal command I could find and nothing worked to get unity back.

---

### Post by Ace..... on 2012-09-11
By re-install, do you mean run install from a burned cd ie. install over 12.04?

or

load win 7 and remove all the partitions other than win, and start afresh?

What about grub - my multi boot will still be there?

OTHER OPTION

Do you believe I can simply install a different desktop?

---

### Post by Ace..... on 2012-09-11
I just found this advice/command:

Ubuntu-desktop is a meta-package in ubuntu that connects all the packages that are installed by default in a fresh ubuntu install. For that reason you can remove it without any damage to other packages or your system. It can be automatically removed if you remove ekiga or gnome-games.

But what if at some point you want to revert all the changes so you have the default packages reinstalled again?

Running :

**sudo apt-get install --reinstall ubuntu-desktop**

does not reinstall its dependencies. So the solution is :

[B]sudo apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | \
sed '/^$/d' | xargs sudo apt-get \
install --reinstall --install-recommends --yes[/B]

(yes this is one line :))

This is where i found it:

[http://gourgi.wordpress.com/2009/09/27/re-install-ubuntu-desktop-metapackage-and-reinstall-its-dependencies/](http://gourgi.wordpress.com/2009/09/27/re-install-ubuntu-desktop-metapackage-and-reinstall-its-dependencies/)

Can anybody verify this command?

---

### Post by jerome1232 on 2012-09-11
I'm not an awk or sed expert, but it looks like it just searches the cache for the dependencies of ubuntu-desktop then uses xargs to pass each one as an argument to apt-get and install them.

You can run apt-get as a dry run just to test and see what it will do, modify the command like this and it will do a dry run (simulation run) You don't need super user permissions to run apt-cache so I removed sudo from that line, best to run things as root only when necessary.

```
apt-cache depends ubuntu-desktop | awk -F ":" '{print $2}' | sed '/^$/d' | xargs sudo apt-get -s install --reinstall --install-recommends --yes 
```

---

### Post by Ace..... on 2012-09-11
I think that terminal has lost some output text, but here is what was displayed:

Is this what we are looking for?

```
Inst bluez-gstreamer [4.98-2ubuntu7] (4.98-2ubuntu7 Ubuntu:12.04/precise [amd64])
Inst branding-ubuntu [0.7] (0.7 Ubuntu:12.04/precise [all])
Inst brasero [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst checkbox-qt [0.13.7] (0.13.7 Ubuntu:12.04/precise [amd64])
Inst cmap-adobe-japan2 [0+20090930-2] (0+20090930-2 Ubuntu:12.04/precise [all])
Inst cups-client [1.5.3-0ubuntu4] (1.5.3-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Inst deja-dup [22.0-0ubuntu2] (22.0-0ubuntu2 Ubuntu:12.04/precise [amd64])
Inst dmz-cursor-theme [0.4.3] (0.4.3 Ubuntu:12.04/precise [all])
Inst doc-base [0.10.3] (0.10.3 Ubuntu:12.04/precise [all])
Inst empathy [3.4.2.3-0ubuntu1] (3.4.2.3-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Inst eog [3.4.2-0ubuntu1] (3.4.2-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Inst evince [3.4.0-0ubuntu1.3] (3.4.0-0ubuntu1.3 Ubuntu:12.04/precise-updates [amd64])
Inst example-content [46] (46 Ubuntu:12.04/precise [all])
Inst file-roller [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst firefox [15.0+build1-0ubuntu0.12.04.1] (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Inst firefox-gnome-support [15.0+build1-0ubuntu0.12.04.1] (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Inst fonts-kacst-one [5.0+svn11846-2] (5.0+svn11846-2 Ubuntu:12.04/precise [all])
Inst fonts-khmeros-core [5.0-5ubuntu1] (5.0-5ubuntu1 Ubuntu:12.04/precise [all])
Inst fonts-lao [0.0.20060226-8] (0.0.20060226-8 Ubuntu:12.04/precise [all])
Inst fonts-liberation [1.07.0-2ubuntu0.1] (1.07.0-2ubuntu0.1 Ubuntu:12.04/precise-updates [all])
Inst fonts-nanum [3.010-2] (3.010-2 Ubuntu:12.04/precise [all])
Inst fonts-takao-pgothic [003.02.01-5ubuntu1] (003.02.01-5ubuntu1 Ubuntu:12.04/precise [all])
Inst fonts-thai-tlwg [1:0.4.17-1ubuntu1] (1:0.4.17-1ubuntu1 Ubuntu:12.04/precise [all])
Inst gcalctool [6.4.1.1-0ubuntu3] (6.4.1.1-0ubuntu3 Ubuntu:12.04/precise-updates [amd64])
Inst gcc [4:4.6.3-1ubuntu5] (4:4.6.3-1ubuntu5 Ubuntu:12.04/precise [amd64])
Inst gedit [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst genisoimage [9:1.1.11-2ubuntu2] (9:1.1.11-2ubuntu2 Ubuntu:12.04/precise [amd64])
Inst ghostscript-x [9.05~dfsg-0ubuntu4.1] (9.05~dfsg-0ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Inst totem-mozilla [3.0.1-0ubuntu21] (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst libtotem0 [3.0.1-0ubuntu21] (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst totem-plugins [3.0.1-0ubuntu21] (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst totem [3.0.1-0ubuntu21] (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst totem-common [3.0.1-0ubuntu21] (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [all]) []
Inst gir1.2-totem-1.0 [3.0.1-0ubuntu21] (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64])
Inst gnome-accessibility-themes [3.4.1-0ubuntu1.1] (3.4.1-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Inst nautilus [1:3.4.2-0ubuntu4] (1:3.4.2-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Inst gnome-bluetooth [3.2.2-0ubuntu5] (3.2.2-0ubuntu5 Ubuntu:12.04/precise [amd64])
Inst nautilus-sendto [3.0.1-2ubuntu2] (3.0.1-2ubuntu2 Ubuntu:12.04/precise [amd64])
Inst gnome-font-viewer [3.4.0-1] (3.4.0-1 Ubuntu:12.04/precise [amd64])
Inst gnome-control-center [1:3.4.2-0ubuntu0.4] (1:3.4.2-0ubuntu0.4 Ubuntu:12.04/precise-updates [amd64])
Inst gnome-disk-utility [3.0.2-2ubuntu7] (3.0.2-2ubuntu7 Ubuntu:12.04/precise [amd64])
Inst gnome-nettool [3.2.0-0ubuntu1] (3.2.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gnome-orca [3.4.2-0ubuntu0.1] (3.4.2-0ubuntu0.1 Ubuntu:12.04/precise-updates [all])
Inst gnome-power-manager [3.4.0-0ubuntu1] (3.4.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gnome-session [3.2.1-0ubuntu8] (3.2.1-0ubuntu8 Ubuntu:12.04/precise [all])
Inst gnome-screenshot [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gnome-session-canberra [0.28-3ubuntu3] (0.28-3ubuntu3 Ubuntu:12.04/precise [amd64])
Inst gnome-sudoku [1:3.4.1-0ubuntu2.1] (1:3.4.1-0ubuntu2.1 Ubuntu:12.04/precise-updates [all])
Inst gnome-system-log [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gnome-system-monitor [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gnome-terminal [3.4.1.1-0ubuntu1] (3.4.1.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gnomine [1:3.4.1-0ubuntu2.1] (1:3.4.1-0ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Inst gstreamer0.10-alsa [0.10.36-1ubuntu0.1] (0.10.36-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst gstreamer0.10-plugins-base-apps [0.10.36-1ubuntu0.1] (0.10.36-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst gstreamer0.10-pulseaudio [0.10.31-1ubuntu1] (0.10.31-1ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gucharmap [1:3.4.1.1-0ubuntu1] (1:3.4.1.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gvfs-bin [1.12.1-0ubuntu1] (1.12.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gvfs-fuse [1.12.1-0ubuntu1] (1.12.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gwibber [3.4.2-0ubuntu2] (3.4.2-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Inst hplip [3.12.2-1ubuntu3.1] (3.12.2-1ubuntu3.1 Ubuntu:12.04/precise-updates [amd64])
Inst ibus [1.4.1-3ubuntu1] (1.4.1-3ubuntu1 Ubuntu:12.04/precise [amd64])
Inst ibus-gtk3 [1.4.1-3ubuntu1] (1.4.1-3ubuntu1 Ubuntu:12.04/precise [amd64])
Inst ibus-pinyin [1.4.0-1] (1.4.0-1 Ubuntu:12.04/precise [amd64])
Inst ibus-pinyin-db-android [1.4.0-1] (1.4.0-1 Ubuntu:12.04/precise [all])
Inst ibus-table [1.3.9.20110827-1ubuntu1] (1.3.9.20110827-1ubuntu1 Ubuntu:12.04/precise [all])
Inst im-switch [1.20ubuntu5] (1.20ubuntu5 Ubuntu:12.04/precise [all])
Inst jockey-gtk [0.9.7-0ubuntu7.1] (0.9.7-0ubuntu7.1 Ubuntu:12.04/precise-updates [all])
Inst kerneloops-daemon [0.12+git20090217-1ubuntu19] (0.12+git20090217-1ubuntu19 Ubuntu:12.04/precise [amd64])
Inst landscape-client-ui-install [12.05-0ubuntu0.12.04] (12.05-0ubuntu0.12.04 Ubuntu:12.04/precise-updates [amd64])
Inst language-selector-gnome [0.79] (0.79 Ubuntu:12.04/precise [all])
Inst laptop-detect [0.13.7ubuntu2] (0.13.7ubuntu2 Ubuntu:12.04/precise [amd64])
Inst launchpad-integration [0.1.56.1] (0.1.56.1 Ubuntu:12.04/precise-updates [all])
Inst libatk-adaptor [2.4.0-1ubuntu2] (2.4.0-1ubuntu2 Ubuntu:12.04/precise [amd64])
Inst libatk-adaptor-schemas [2.4.0-1ubuntu2] (2.4.0-1ubuntu2 Ubuntu:12.04/precise [amd64])
Inst libgail-common [2.24.10-0ubuntu6] (2.24.10-0ubuntu6 Ubuntu:12.04/precise [amd64])
Inst libnotify-bin [0.7.5-1] (0.7.5-1 Ubuntu:12.04/precise [amd64])
Inst libnss-mdns [0.10-3.2] (0.10-3.2 Ubuntu:12.04/precise [amd64])
Inst libpam-ck-connector [0.4.5-2] (0.4.5-2 Ubuntu:12.04/precise [amd64])
Inst libpam-gnome-keyring [3.2.2-2ubuntu4] (3.2.2-2ubuntu4 Ubuntu:12.04/precise [amd64])
Inst libproxy1-plugin-gsettings [0.4.7-0ubuntu4] (0.4.7-0ubuntu4 Ubuntu:12.04/precise [amd64])
Inst libproxy1-plugin-networkmanager [0.4.7-0ubuntu4] (0.4.7-0ubuntu4 Ubuntu:12.04/precise [amd64])
Inst libreoffice-calc [1:3.5.4-0ubuntu1.1] (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst libreoffice-gnome [1:3.5.4-0ubuntu1.1] (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst libreoffice-help-en-us [1:3.5.4-0ubuntu1.1] (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Inst libreoffice-impress [1:3.5.4-0ubuntu1.1] (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst libreoffice-math [1:3.5.4-0ubuntu1.1] (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst libreoffice-style-human [1:3.5.4-0ubuntu1.1] (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Inst libreoffice-writer [1:3.5.4-0ubuntu1.1] (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst libwmf0.2-7-gtk [0.2.8.4-10ubuntu1] (0.2.8.4-10ubuntu1 Ubuntu:12.04/precise [amd64])
Inst linux-headers-generic [3.2.0.30.32] (3.2.0.30.32 Ubuntu:12.04/precise-updates [amd64])
Inst mahjongg [1:3.4.1-0ubuntu2.1] (1:3.4.1-0ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Inst make [3.81-8.1ubuntu1] (3.81-8.1ubuntu1 Ubuntu:12.04/precise [amd64])
Inst mousetweaks [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst nautilus-share [0.7.3-1ubuntu2] (0.7.3-1ubuntu2 Ubuntu:12.04/precise [amd64])
Inst network-manager-gnome [0.9.4.1-0ubuntu2] (0.9.4.1-0ubuntu2 Ubuntu:12.04/precise [amd64])
Inst network-manager-pptp [0.9.4.0-0ubuntu1] (0.9.4.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst network-manager-pptp-gnome [0.9.4.0-0ubuntu1] (0.9.4.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst notify-osd [0.9.34-0ubuntu2] (0.9.34-0ubuntu2 Ubuntu:12.04/precise [amd64])
Inst onboard [0.97.0-0ubuntu3] (0.97.0-0ubuntu3 Ubuntu:12.04/precise [amd64])
Inst overlay-scrollbar [0.2.16-0ubuntu1] (0.2.16-0ubuntu1 Ubuntu:12.04/precise [all])
Inst plymouth-theme-ubuntu-logo [0.8.2-2ubuntu30] (0.8.2-2ubuntu30 Ubuntu:12.04/precise [amd64])
Inst policykit-desktop-privileges [0.10] (0.10 Ubuntu:12.04/precise [all])
Inst printer-driver-min12xxw [0.0.9-6ubuntu1] (0.0.9-6ubuntu1 Ubuntu:12.04/precise [amd64])
Inst printer-driver-pnm2ppa [1.13+nondbs-0ubuntu1] (1.13+nondbs-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst printer-driver-ptouch [1.3-3ubuntu0.1] (1.3-3ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst printer-driver-pxljr [1.3+repack0-2] (1.3+repack0-2 Ubuntu:12.04/precise [amd64])
Inst printer-driver-splix [2.0.0+svn300-1.1ubuntu2] (2.0.0+svn300-1.1ubuntu2 Ubuntu:12.04/precise [amd64])
Inst pulseaudio [1:1.1-0ubuntu15.1] (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Inst pulseaudio-module-gconf [1:1.1-0ubuntu15.1] (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Inst pulseaudio-module-x11 [1:1.1-0ubuntu15.1] (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Inst remmina [1.0.0-1ubuntu6.1] (1.0.0-1ubuntu6.1 Ubuntu:12.04/precise-updates [amd64])
Inst rfkill [0.4-1ubuntu2] (0.4-1ubuntu2 Ubuntu:12.04/precise [amd64])
Inst rhythmbox [2.96-0ubuntu4.1] (2.96-0ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Inst rhythmbox-plugin-magnatune [2.96-0ubuntu4.1] (2.96-0ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Inst seahorse [3.2.2-0ubuntu2] (3.2.2-0ubuntu2 Ubuntu:12.04/precise [amd64])
Inst simple-scan [3.4.1-0ubuntu1.1] (3.4.1-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst sni-qt [0.2.5-0ubuntu3] (0.2.5-0ubuntu3 Ubuntu:12.04/precise [amd64])
Inst software-center [5.2.5] (5.2.5 Ubuntu:12.04/precise-updates [all])
Inst software-properties-gtk [0.82.7.2] (0.82.7.2 Ubuntu:12.04/precise-updates [all])
Inst ssh-askpass-gnome [1:5.9p1-5ubuntu1] (1:5.9p1-5ubuntu1 Ubuntu:12.04/precise [amd64])
Inst system-config-printer-gnome [1.3.8+20120201-0ubuntu8.1] (1.3.8+20120201-0ubuntu8.1 Ubuntu:12.04/precise-updates [all])
Inst telepathy-idle [0.1.11-2] (0.1.11-2 Ubuntu:12.04/precise [amd64])
Inst thunderbird [15.0+build1-0ubuntu0.12.04.1] (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Inst thunderbird-gnome-support [15.0+build1-0ubuntu0.12.04.1] (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Inst transmission-gtk [2.51-0ubuntu1] (2.51-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst ttf-dejavu-core [2.33-2ubuntu1] (2.33-2ubuntu1 Ubuntu:12.04/precise [all])
Inst ttf-freefont [20100919-1] (20100919-1 Ubuntu:12.04/precise [all])
Inst ttf-indic-fonts-core [1:0.5.11ubuntu1] (1:0.5.11ubuntu1 Ubuntu:12.04/precise [all])
Inst ttf-punjabi-fonts [1:0.5.11ubuntu1] (1:0.5.11ubuntu1 Ubuntu:12.04/precise [all])
Inst ttf-ubuntu-font-family [0.80-0ubuntu2] (0.80-0ubuntu2 Ubuntu:12.04/precise [all])
Inst ttf-wqy-microhei [0.2.0-beta-1ubuntu1] (0.2.0-beta-1ubuntu1 Ubuntu:12.04/precise [all])
Inst type-handling:i386 (0.2.23build1 Ubuntu:12.04/precise [i386])
Inst ubuntu-artwork [57] (57 Ubuntu:12.04/precise [all])
Inst ubuntu-desktop [1.267] (1.267 Ubuntu:12.04/precise [amd64])
Inst ubuntu-extras-keyring [2010.09.27] (2010.09.27 Ubuntu:12.04/precise [all])
Inst ubuntu-sounds [0.13] (0.13 Ubuntu:12.04/precise [all])
Inst ubuntuone-client-gnome [3.0.1-0ubuntu1] (3.0.1-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Inst unity [5.14.0-0ubuntu1] (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Inst unity-2d [5.12.0-0ubuntu1.1] (5.12.0-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Inst unity-greeter [0.2.8-0ubuntu1.2] (0.2.8-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Inst unzip [6.0-4ubuntu1] (6.0-4ubuntu1 Ubuntu:12.04/precise [amd64])
Inst update-manager [1:0.156.14.9] (1:0.156.14.9 Ubuntu:12.04/precise-updates [all])
Inst update-notifier [0.119ubuntu8.5] (0.119ubuntu8.5 Ubuntu:12.04/precise-updates [amd64])
Inst usb-creator-gtk [0.2.38] (0.2.38 Ubuntu:12.04/precise [amd64])
Inst vino [3.4.2-0ubuntu1.1] (3.4.2-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst wireless-tools [30~pre9-5ubuntu2] (30~pre9-5ubuntu2 Ubuntu:12.04/precise [amd64])
Inst wpasupplicant [0.7.3-6ubuntu2] (0.7.3-6ubuntu2 Ubuntu:12.04/precise [amd64])
Inst xcursor-themes [1.0.3-1] (1.0.3-1 Ubuntu:12.04/precise [all])
Inst xdg-user-dirs [0.14-0ubuntu2] (0.14-0ubuntu2 Ubuntu:12.04/precise [amd64])
Inst xdg-user-dirs-gtk [0.9-0ubuntu1] (0.9-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst xdg-utils [1.1.0~rc1-2ubuntu6] (1.1.0~rc1-2ubuntu6 Ubuntu:12.04/precise [all])
Inst xdiagnose [2.5.2] (2.5.2 Ubuntu:12.04/precise-updates [all])
Inst xorg [1:7.6+12ubuntu1] (1:7.6+12ubuntu1 Ubuntu:12.04/precise [amd64])
Inst xterm [271-1ubuntu2] (271-1ubuntu2 Ubuntu:12.04/precise [amd64])
Inst xul-ext-ubufox [2.1.1-0ubuntu0.12.04.1] (2.1.1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [all])
Inst yelp [3.4.1-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst zenity [3.4.0-0ubuntu4] (3.4.0-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Inst zip [3.0-4] (3.0-4 Ubuntu:12.04/precise [amd64])
Inst cups-bsd [1.5.3-0ubuntu4] (1.5.3-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Inst ginn [0.2.4-0ubuntu1] (0.2.4-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst inputattach [1:1.4.2-1] (1:1.4.2-1 Ubuntu:12.04/precise [amd64])
Inst pulseaudio-module-bluetooth [1:1.1-0ubuntu15.1] (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Inst python-aptdaemon.pkcompat [0.43+bzr805-0ubuntu4] (0.43+bzr805-0ubuntu4 Ubuntu:12.04/precise-updates [all])
Inst rhythmbox-ubuntuone [3.0.0-0ubuntu1] (3.0.0-0ubuntu1 Ubuntu:12.04/precise [all])
Inst shotwell [0.12.3-0ubuntu0.1] (0.12.3-0ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst speech-dispatcher [0.7.1-6ubuntu3] (0.7.1-6ubuntu3 Ubuntu:12.04/precise [amd64])
Inst ubuntuone-installer [3.0.2-0ubuntu1.1] (3.0.2-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Conf alsa-utils (1.0.25-1ubuntu5 Ubuntu:12.04/precise [amd64])
Conf bluez (4.98-2ubuntu7 Ubuntu:12.04/precise [amd64])
Conf printer-driver-sag-gdi (0.1-3 Ubuntu:12.04/precise [all])
Conf foomatic-filters (4.0.16-0ubuntu0.2 Ubuntu:12.04/precise-updates [amd64])
Conf printer-driver-foo2zjs (20111202dfsg0-1ubuntu1 Ubuntu:12.04/precise [amd64])
Conf printer-driver-c2esp (23-1 Ubuntu:12.04/precise [amd64])
Conf openprinting-ppds (20120322-0ubuntu1 Ubuntu:12.04/precise [all])
Conf foomatic-db-compressed-ppds (20120322-0ubuntu1 Ubuntu:12.04/precise [all])
Conf cups-client (1.5.3-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Conf bc (1.06.95-2 Ubuntu:12.04/precise [amd64])
Conf cups (1.5.3-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-media (3.4.0-0ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-menus (3.4.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gnome-screensaver (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf libgd2-xpm (2.0.36~rc1~dfsg-6ubuntu2 Ubuntu:12.04/precise [amd64])
Conf libgd2-xpm:i386 (2.0.36~rc1~dfsg-6ubuntu2 Ubuntu:12.04/precise [i386])
Conf libqt4-sql-sqlite (4:4.8.1-0ubuntu4.2 Ubuntu:12.04/precise-updates [amd64])
Conf libsdl1.2debian (1.2.14-6.4ubuntu3 Ubuntu:12.04/precise [amd64])
Conf libxp6 (1:1.0.1-2 Ubuntu:12.04/precise [amd64])
Conf lightdm (1.2.1-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf nvidia-common (1:0.2.44 Ubuntu:12.04/precise [amd64])
Conf pcmciautils (018-6 Ubuntu:12.04/precise [amd64])
Conf qt-at-spi (0.2.0+git20120411-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf yelp (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf ubuntu-docs (12.04.6 Ubuntu:12.04/precise-updates [all])
Conf activity-log-manager-control-center (0.9.4-0ubuntu3 Ubuntu:12.04/precise [amd64])
Conf whoopsie (0.1.32 Ubuntu:12.04/precise [amd64])
Conf brltty (4.3-1ubuntu5 Ubuntu:12.04/precise [amd64])
Conf xkb-data (2.5-1ubuntu1.3 Ubuntu:12.04/precise-updates [all])
Conf ca-certificates (20111211 Ubuntu:12.04/precise [all])
Conf libsasl2-modules (2.1.25.dfsg1-3ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf libsasl2-modules:i386 (2.1.25.dfsg1-3ubuntu0.1 Ubuntu:12.04/precise-updates [i386])
Conf laptop-detect (0.13.7ubuntu2 Ubuntu:12.04/precise [amd64])
Conf acpi-support (0.140 Ubuntu:12.04/precise [amd64])
Conf aisleriot (1:3.2.3.2-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf alsa-base (1.0.25+dfsg-0ubuntu1 Ubuntu:12.04/precise [all])
Conf anacron (2.3-14ubuntu1 Ubuntu:12.04/precise [amd64])
Conf app-install-data-partner (12.12.04.1 Ubuntu:12.04/precise [all])
Conf python-apport (2.0.1-0ubuntu13 Ubuntu:12.04/precise-updates [all])
Conf apport-gtk (2.0.1-0ubuntu13 Ubuntu:12.04/precise-updates [all])
Conf at-spi2-core (2.4.2-0ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf avahi-autoipd (0.6.30-5ubuntu2 Ubuntu:12.04/precise [amd64])
Conf avahi-daemon (0.6.30-5ubuntu2 Ubuntu:12.04/precise [amd64])
Conf baobab (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf bluez-alsa (4.98-2ubuntu7 Ubuntu:12.04/precise [amd64])
Conf bluez-cups (4.98-2ubuntu7 Ubuntu:12.04/precise [amd64])
Conf bluez-gstreamer (4.98-2ubuntu7 Ubuntu:12.04/precise [amd64])
Conf branding-ubuntu (0.7 Ubuntu:12.04/precise [all])
Conf brasero (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf checkbox-qt (0.13.7 Ubuntu:12.04/precise [amd64])
Conf cmap-adobe-japan2 (0+20090930-2 Ubuntu:12.04/precise [all])
Conf deja-dup (22.0-0ubuntu2 Ubuntu:12.04/precise [amd64])
Conf dmz-cursor-theme (0.4.3 Ubuntu:12.04/precise [all])
Conf doc-base (0.10.3 Ubuntu:12.04/precise [all])
Conf empathy (3.4.2.3-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf eog (3.4.2-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf evince (3.4.0-0ubuntu1.3 Ubuntu:12.04/precise-updates [amd64])
Conf example-content (46 Ubuntu:12.04/precise [all])
Conf zip (3.0-4 Ubuntu:12.04/precise [amd64])
Conf unzip (6.0-4ubuntu1 Ubuntu:12.04/precise [amd64])
Conf genisoimage (9:1.1.11-2ubuntu2 Ubuntu:12.04/precise [amd64])
Conf file-roller (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf firefox (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf firefox-gnome-support (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf fonts-kacst-one (5.0+svn11846-2 Ubuntu:12.04/precise [all])
Conf fonts-khmeros-core (5.0-5ubuntu1 Ubuntu:12.04/precise [all])
Conf fonts-lao (0.0.20060226-8 Ubuntu:12.04/precise [all])
Conf fonts-liberation (1.07.0-2ubuntu0.1 Ubuntu:12.04/precise-updates [all])
Conf fonts-nanum (3.010-2 Ubuntu:12.04/precise [all])
Conf fonts-takao-pgothic (003.02.01-5ubuntu1 Ubuntu:12.04/precise [all])
Conf fonts-thai-tlwg (1:0.4.17-1ubuntu1 Ubuntu:12.04/precise [all])
Conf gcalctool (6.4.1.1-0ubuntu3 Ubuntu:12.04/precise-updates [amd64])
Conf gcc (4:4.6.3-1ubuntu5 Ubuntu:12.04/precise [amd64])
Conf gedit (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf ghostscript-x (9.05~dfsg-0ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Conf libtotem0 (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64])
Conf totem-common (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [all])
Conf gstreamer0.10-alsa (0.10.36-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf totem (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64])
Conf totem-mozilla (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64])
Conf gir1.2-totem-1.0 (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64])
Conf totem-plugins (3.0.1-0ubuntu21.1 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-accessibility-themes (3.4.1-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Conf nautilus (1:3.4.2-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-bluetooth (3.2.2-0ubuntu5 Ubuntu:12.04/precise [amd64])
Conf nautilus-sendto (3.0.1-2ubuntu2 Ubuntu:12.04/precise [amd64])
Conf gnome-font-viewer (3.4.0-1 Ubuntu:12.04/precise [amd64])
Conf gnome-control-center (1:3.4.2-0ubuntu0.4 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-disk-utility (3.0.2-2ubuntu7 Ubuntu:12.04/precise [amd64])
Conf gnome-nettool (3.2.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gnome-orca (3.4.2-0ubuntu0.1 Ubuntu:12.04/precise-updates [all])
Conf notify-osd (0.9.34-0ubuntu2 Ubuntu:12.04/precise [amd64])
Conf gnome-power-manager (3.4.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gnome-session (3.2.1-0ubuntu8 Ubuntu:12.04/precise [all])
Conf gnome-screenshot (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gnome-session-canberra (0.28-3ubuntu3 Ubuntu:12.04/precise [amd64])
Conf gnome-sudoku (1:3.4.1-0ubuntu2.1 Ubuntu:12.04/precise-updates [all])
Conf gnome-system-log (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gnome-system-monitor (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gnome-terminal (3.4.1.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gnomine (1:3.4.1-0ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Conf gstreamer0.10-plugins-base-apps (0.10.36-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf gstreamer0.10-pulseaudio (0.10.31-1ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gucharmap (1:3.4.1.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gvfs-bin (1.12.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gvfs-fuse (1.12.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gwibber (3.4.2-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf hplip (3.12.2-1ubuntu3.1 Ubuntu:12.04/precise-updates [amd64])
Conf ibus (1.4.1-3ubuntu1 Ubuntu:12.04/precise [amd64])
Conf ibus-gtk3 (1.4.1-3ubuntu1 Ubuntu:12.04/precise [amd64])
Conf ibus-pinyin-db-android (1.4.0-1 Ubuntu:12.04/precise [all])
Conf ibus-pinyin (1.4.0-1 Ubuntu:12.04/precise [amd64])
Conf ibus-table (1.3.9.20110827-1ubuntu1 Ubuntu:12.04/precise [all])
Conf im-switch (1.20ubuntu5 Ubuntu:12.04/precise [all])
Conf jockey-gtk (0.9.7-0ubuntu7.1 Ubuntu:12.04/precise-updates [all])
Conf kerneloops-daemon (0.12+git20090217-1ubuntu19 Ubuntu:12.04/precise [amd64])
Conf landscape-client-ui-install (12.05-0ubuntu0.12.04 Ubuntu:12.04/precise-updates [amd64])
Conf language-selector-gnome (0.79 Ubuntu:12.04/precise [all])
Conf launchpad-integration (0.1.56.1 Ubuntu:12.04/precise-updates [all])
Conf libatk-adaptor (2.4.0-1ubuntu2 Ubuntu:12.04/precise [amd64])
Conf libatk-adaptor-schemas (2.4.0-1ubuntu2 Ubuntu:12.04/precise [amd64])
Conf libgail-common (2.24.10-0ubuntu6 Ubuntu:12.04/precise [amd64])
Conf libnotify-bin (0.7.5-1 Ubuntu:12.04/precise [amd64])
Conf libnss-mdns (0.10-3.2 Ubuntu:12.04/precise [amd64])
Conf libpam-ck-connector (0.4.5-2 Ubuntu:12.04/precise [amd64])
Conf libpam-gnome-keyring (3.2.2-2ubuntu4 Ubuntu:12.04/precise [amd64])
Conf libproxy1-plugin-gsettings (0.4.7-0ubuntu4 Ubuntu:12.04/precise [amd64])
Conf libproxy1-plugin-networkmanager (0.4.7-0ubuntu4 Ubuntu:12.04/precise [amd64])
Conf libreoffice-calc (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf libreoffice-gnome (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf libreoffice-writer (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf libreoffice-help-en-us (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Conf libreoffice-impress (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf libreoffice-math (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf libreoffice-style-human (1:3.5.4-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Conf libwmf0.2-7-gtk (0.2.8.4-10ubuntu1 Ubuntu:12.04/precise [amd64])
Conf linux-headers-generic (3.2.0.30.32 Ubuntu:12.04/precise-updates [amd64])
Conf mahjongg (1:3.4.1-0ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Conf make (3.81-8.1ubuntu1 Ubuntu:12.04/precise [amd64])
Conf mousetweaks (3.4.1-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf nautilus-share (0.7.3-1ubuntu2 Ubuntu:12.04/precise [amd64])
Conf network-manager-gnome (0.9.4.1-0ubuntu2 Ubuntu:12.04/precise [amd64])
Conf network-manager-pptp (0.9.4.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf network-manager-pptp-gnome (0.9.4.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf onboard (0.97.0-0ubuntu3 Ubuntu:12.04/precise [amd64])
Conf overlay-scrollbar (0.2.16-0ubuntu1 Ubuntu:12.04/precise [all])
Conf plymouth-theme-ubuntu-logo (0.8.2-2ubuntu30 Ubuntu:12.04/precise [amd64])
Conf policykit-desktop-privileges (0.10 Ubuntu:12.04/precise [all])
Conf printer-driver-min12xxw (0.0.9-6ubuntu1 Ubuntu:12.04/precise [amd64])
Conf printer-driver-pnm2ppa (1.13+nondbs-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf printer-driver-ptouch (1.3-3ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf printer-driver-pxljr (1.3+repack0-2 Ubuntu:12.04/precise [amd64])
Conf printer-driver-splix (2.0.0+svn300-1.1ubuntu2 Ubuntu:12.04/precise [amd64])
Conf pulseaudio (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Conf pulseaudio-module-gconf (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Conf pulseaudio-module-x11 (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Conf remmina (1.0.0-1ubuntu6.1 Ubuntu:12.04/precise-updates [amd64])
Conf rfkill (0.4-1ubuntu2 Ubuntu:12.04/precise [amd64])
Conf rhythmbox (2.96-0ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Conf rhythmbox-plugin-magnatune (2.96-0ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Conf seahorse (3.2.2-0ubuntu2 Ubuntu:12.04/precise [amd64])
Conf xdg-utils (1.1.0~rc1-2ubuntu6 Ubuntu:12.04/precise [all])
Conf simple-scan (3.4.1-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf sni-qt (0.2.5-0ubuntu3 Ubuntu:12.04/precise [amd64])
Conf ubuntu-extras-keyring (2010.09.27 Ubuntu:12.04/precise [all])
Conf software-center (5.2.5 Ubuntu:12.04/precise-updates [all])
Conf software-properties-gtk (0.82.7.2 Ubuntu:12.04/precise-updates [all])
Conf ssh-askpass-gnome (1:5.9p1-5ubuntu1 Ubuntu:12.04/precise [amd64])
Conf system-config-printer-gnome (1.3.8+20120201-0ubuntu8.1 Ubuntu:12.04/precise-updates [all])
Conf telepathy-idle (0.1.11-2 Ubuntu:12.04/precise [amd64])
Conf thunderbird (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf thunderbird-gnome-support (15.0+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf transmission-gtk (2.51-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf ttf-dejavu-core (2.33-2ubuntu1 Ubuntu:12.04/precise [all])
Conf ttf-freefont (20100919-1 Ubuntu:12.04/precise [all])
Conf ttf-indic-fonts-core (1:0.5.11ubuntu1 Ubuntu:12.04/precise [all])
Conf ttf-punjabi-fonts (1:0.5.11ubuntu1 Ubuntu:12.04/precise [all])
Conf ttf-ubuntu-font-family (0.80-0ubuntu2 Ubuntu:12.04/precise [all])
Conf ttf-wqy-microhei (0.2.0-beta-1ubuntu1 Ubuntu:12.04/precise [all])
Conf type-handling:i386 (0.2.23build1 Ubuntu:12.04/precise [i386])
Conf ubuntu-artwork (57 Ubuntu:12.04/precise [all])
Conf inputattach (1:1.4.2-1 Ubuntu:12.04/precise [amd64])
Conf ubuntu-sounds (0.13 Ubuntu:12.04/precise [all])
Conf unity (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf unity-2d (5.12.0-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Conf unity-greeter (0.2.8-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Conf update-manager (1:0.156.14.9 Ubuntu:12.04/precise-updates [all])
Conf update-notifier (0.119ubuntu8.5 Ubuntu:12.04/precise-updates [amd64])
Conf wireless-tools (30~pre9-5ubuntu2 Ubuntu:12.04/precise [amd64])
Conf wpasupplicant (0.7.3-6ubuntu2 Ubuntu:12.04/precise [amd64])
Conf xdg-user-dirs (0.14-0ubuntu2 Ubuntu:12.04/precise [amd64])
Conf xdg-user-dirs-gtk (0.9-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf xdiagnose (2.5.2 Ubuntu:12.04/precise-updates [all])
Conf xterm (271-1ubuntu2 Ubuntu:12.04/precise [amd64])
Conf xorg (1:7.6+12ubuntu1 Ubuntu:12.04/precise [amd64])
Conf zenity (3.4.0-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Conf ubuntu-desktop (1.267 Ubuntu:12.04/precise [amd64])
Conf ubuntuone-client-gnome (3.0.1-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf usb-creator-gtk (0.2.38 Ubuntu:12.04/precise [amd64])
Conf vino (3.4.2-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf xcursor-themes (1.0.3-1 Ubuntu:12.04/precise [all])
Conf xul-ext-ubufox (2.1.1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [all])
Conf cups-bsd (1.5.3-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Conf ginn (0.2.4-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf pulseaudio-module-bluetooth (1:1.1-0ubuntu15.1 Ubuntu:12.04/precise-updates [amd64])
Conf python-aptdaemon.pkcompat (0.43+bzr805-0ubuntu4 Ubuntu:12.04/precise-updates [all])
Conf rhythmbox-ubuntuone (3.0.0-0ubuntu1 Ubuntu:12.04/precise [all])
Conf shotwell (0.12.3-0ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf speech-dispatcher (0.7.1-6ubuntu3 Ubuntu:12.04/precise [amd64])
Conf ubuntuone-installer (3.0.2-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
```

---

### Post by PaulInBHC on 2012-09-11
I have XP and 12.04

I used the live CD to delete the sda's with 12.04 on them and install a fresh copy of 12.04 in the unused space.

XP was not touched.

---

### Post by Ace..... on 2012-09-11
Yes, I think you're right.

I have started another thread on prepping for delete & install:

[http://ubuntuforums.org/showthread.php?p=12232148#post12232148](http://ubuntuforums.org/showthread.php?p=12232148#post12232148)

Primarily I want to get it right this time to allow future reinstalls without grief. ;)

Unless somebody comes up with the solution shortly, I will go for delete and install.

---

### Post by cortman on 2012-09-11
> **Ace..... said:**
> I think that terminal has lost some output text, but here is what was displayed:

Is this what we are looking for?


Looks correct AFAICT, but I'd still recommend a reinstallation unless you really would prefer to reinstall Unity.

---

### Post by jerome1232 on 2012-09-11
I would at least try it. If it fixes your issue you just saved yourself a reinstall. If it doesn't then you still reinstall.

---

### Post by Ace..... on 2012-09-11
Oh wow..... yes.

Strange how one mentally moves to a different path.

I suppose the question is:

can it screw everything up?

I think I will continue with prepping for a reinstall.

I'm nearly there now, having cleared 15Gb from my usb hard drive.

I'll copy home to it and clarify a couple of details on the prepping for delete & install thread.

Then I will run the command.
We've come so far, I think "for the community" this command should be tested.

If it works we can change the tag to solved and it will become easily searchable.

---

### Post by PaulInBHC on 2012-09-11
I posted on 4 or 5 threads that had the same problem and didn't get any answers that worked for me. Doesn't mean that there isn't an answer.

Check my profile and click posts by me. They are in the Desktop forum. Or try a search.

---

### Post by Ace..... on 2012-09-12
> **PaulInBHC said:**
> I posted on 4 or 5 threads that had the same problem and didn't get any answers that worked for me. Doesn't mean that there isn't an answer.

Check my profile and click posts by me. They are in the Desktop forum. Or try a search.

Yes, but you never know.
This could be the answer.

If not, then it's an install.

I'm just gonna test my 12.04 cd then I'll run the command.

---

### Post by Ace..... on 2012-09-12
Ok I ran the command and......

30 minutes later, and a reboot.....

nothing had changed. :(

After all the re-installing that occurred I had high hopes, but no.

We definitely tried hard to fix this, and thanks to everybody who contributed.

so we re-install. ;)

---

### Post by Ace..... on 2012-09-12
It worked perfectly.... or as near as damn it.

chrome had to be downloaded again from their site (not software centre - don't know why) but when it installed it had all my bookmarks in place..... nice.

clearly there may be other packages that need downloading, but thats fine if user data is present.

eg. just tried gparted and its not installed.

**THE KEY POINT IS THIS:**

Ubuntu can now be reinstalled yet it does not overwrite home dir data.

In effect..... the reinstallation process IS the solution.

It takes about an hour, and requires a minor bit of prepping in advance, but it is very good, and my system is FAST again as a bonus!

What I'll do is tidy the prepping info and post it here as the solution.

:D:D:D:D

---

### Post by TiloBunt on 2012-09-24
same issue here after using Janitor (Ubuntu Tweak)
looks like I'm back. 
first tried to unity reset and reinstall
[http://ubuntuforums.org/showthread.php?t=1944002]("http://ubuntuforums.org/showthread.php?t=1944002")
but didn't help

After running:
[http://forum.parallels.com/printthread.php?t=259137]("http://forum.parallels.com/printthread.php?t=259137")
> sudo apt-get install fglrx-updates

and rebooted.

I'm back, will update the other post/questions I found. 
Cheers
note I use a ASUS notebook with ATI 58xx mobile.

---

### Post by TiloBunt on 2012-09-24
well I got 2D back for now. keep you posted.

---

### Post by TiloBunt on 2012-09-24
after try to reinstall Unity 
[http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity)

still didn't work but a new user I created was working.
check 2d vs 3d via 
```
echo $DESKTOP_SESSION
```

so after login back to my account it also worked again.
check this thread for more ideas.
[http://ubuntuforums.org/showthread.php?t=1856053]("http://ubuntuforums.org/showthread.php?t=1856053")

cheers

---

### Post by Ace..... on 2012-10-03
Tilo

sorry I didn't step in to the thread.
After all the pain I got stuck into other jobs.

check out the guide I wrote that should help you if you still have problems:

[http://ubuntuforums.org/showthread.php?t=2057342](http://ubuntuforums.org/showthread.php?t=2057342)

:P

---


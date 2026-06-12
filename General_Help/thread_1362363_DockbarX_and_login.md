---
title: "DockbarX and login"
date: 2009-12-23
forum: General Help
---

### Post by TheNessus on 2009-12-23
everytime I login to ubuntu:

The panel encountered a problem while loading "OAFIID:GNOME_DockBarXApplet".

any ideas?

---

### Post by M7S on 2009-12-23
I really would like to find out the reason for this one. I've heard quite a few people that have run into this problem. Unfortunately, I have no idea of how to debug this one.

Unless you run global menu. Then the solution is to not use global-menu ;) (it's a bug on their end, if I understood it correctly.


M7S,
Dockbarx developer

---

### Post by TheNessus on 2009-12-23
have you considered making DBX start on the gnome-panel a few seconds into the login? it may have something to do with some processes that have not loaded yet.

---

### Post by M7S on 2009-12-23
Perhaps I should try what gnomenu does: every import of modules in the beggining of the script should be tried and if a error loading a module comes up, a five to ten second wait should occur and then dockbarx tries to import the module again. It's more of a hack than a real solution to the problem, though.

---

### Post by Leftblank on 2010-01-04
Hopefully that would work indeed; I'm one of the happy few who have this error. It's not on every restart, but does happen frequently for me, it'd be great to find a solution for this problem.

---

### Post by neeraj2608 on 2010-01-19
Apparently, reinstalling gnome-applets and gnome-applets-data solves the problem. Give it a try.

---

### Post by Leftblank on 2010-01-19
> **neeraj2608 said:**
> Apparently, reinstalling gnome-applets and gnome-applets-data solves the problem. Give it a try.

Forgot to update my post; ever since I removed the folder /home/username/.gconf/apps/panel and logged in again, it hasn't crashed at all. Pretty odd, but I'm more than glad it's solved for now.

---

### Post by neeraj2608 on 2010-01-19
> **neeraj2608 said:**
> Apparently, reinstalling gnome-applets and gnome-applets-data solves the problem. Give it a try.

Sorry, scratch that. I rebooted my machine and the problem's still there. :(

---

### Post by Leftblank on 2010-01-19
> **neeraj2608 said:**
> Sorry, scratch that. I rebooted my machine and the problem's still there. :(

Give deleting those folders I mentioned above your post a shot; it will reset your gnome panel settings, but solved it completely for me.

---

### Post by neeraj2608 on 2010-01-19
> **Leftblank said:**
> Forgot to update my post; ever since I removed the folder /home/username/.gconf/apps/panel and logged in again, it hasn't crashed at all. Pretty odd, but I'm more than glad it's solved for now.

Nopes, doesn't work for me. :( I deleted apps/panel, logged out, logged in and added Dockbarx to the panel, then logged out again. But when I log in, I still get the error message reported in the OP.

---

### Post by M7S on 2010-01-20
I've committed the fix I talked about in a previous post. It's not yet released but you can try it out from dockbarx's bzr branch. See [https://code.launchpad.net/~dockbar-main/dockbar/experimental](https://code.launchpad.net/~dockbar-main/dockbar/experimental)

---

### Post by neeraj2608 on 2010-01-20
> **M7S said:**
> I've committed the fix I talked about in a previous post. It's not yet released but you can try it out from dockbarx's bzr branch. See [https://code.launchpad.net/~dockbar-main/dockbar/experimental](https://code.launchpad.net/~dockbar-main/dockbar/experimental)

Excellent! It works. Many thanks. :)

---

### Post by neeraj2608 on 2010-01-20
> **neeraj2608 said:**
> Excellent! It works. Many thanks. :)

By the way, in case anyone's interested, Talika is another applet that provides similar functionality.

---

### Post by neeraj2608 on 2010-01-21
> **neeraj2608 said:**
> Excellent! It works. Many thanks. :)

Sorry, I spoke too soon. I got the error message again when I booted my machine this morning. It seems that a previous install of Dockbarx had not been properly removed and possibly messed things up. Sorry.

This might seem like a noob suggestion, but I was having a look at your server file GNOME_DockBarXApplet.server. The name of the applet 'factory' specified on line 13 is *[FONT=Verdana]"GNOME_DockBarXApplet_Factory"[/FONT]*. This is the file that should be placed in the /usr/lib/bonobo/server directory (as explained [here]("http://here")). So, shouldn't the file [FONT=Courier New]GNOME_DockBarXApplet.server[/FONT] be renamed to [FONT=Courier New]GNOME_DockBarXApplet_Factory.server[/FONT]?

I just tried out this change on Dockbarx ver. 0.24.0.1 installed from the dockbar PPA, taking care to first delete all of my gconf settings in [FONT=Courier New]~/.gconf/apps/panel[/FONT] just to ensure that no previous installations of dockbarx could cause any problems. After changing the file name to [FONT=Courier New]GNOME_DockBarXApplet_Factory.server[/FONT],  and carrying out a couple of cold boots and hibernate/resumes, I have still had no crashes.

---

### Post by neeraj2608 on 2010-01-21
> **neeraj2608 said:**
> 
... I have still had no crashes.

Everytime I say that, I jinx it, LOL.

Needless to say, my blundering around hasn't solved the problem. On the other hand, I now have a better understanding of server files (this page is quite helpful: [Gnome applets with Python]("http://www.pygtk.org/articles/applets_arturogf/")).

---

### Post by snoxu on 2010-01-23
I'm running DockbarX on Arch. I'm having the same problem mentioned here. I think I've tried every thing including the bzr branch. Nothing seems to work.

Anyhow patiently awating some kind of fix. Also DockbarX for the Xfce panel would be great (so I could stop using gnome panel)

---

### Post by M7S on 2010-01-24
I will look into the possibility to send all error messages to a log-file so that you could see what goes wrong. If someone knows how you do this in python, please inform me.

Regarding your other request, can't you run dockbarx in xfapplet in xfce?

---

### Post by snoxu on 2010-01-24
Yeah I can run it in xfapplet, which is funny because it made me realize that I prefer Gnome panels customization better.

Anyhow, DockbarX also crashes in Xfapplet at login.

---

### Post by snoxu on 2010-03-20
So any news on a solution to the problem?

---

### Post by M7S on 2010-03-24
Sorry, no sollution yet. :(

---

### Post by snoxu on 2010-05-09
I've started using Talika, Dockbarx just crashes constantly and it can be a bit anoying. Talika is really basic though, I prefer Dockbarx.

I wish I could help. Anyhow hope you figure out the problem.

---

### Post by M7S on 2010-05-09
Well, there should be a fix now.

Go to /home/username/.config/gnome-session and remove the folder "saved-session". Reboot. Tell me if it works.

---

### Post by snoxu on 2010-05-09
Is the fix in the bzr branch?

Anyhow, I tried x.0.30 and it still crashes when I reboot. So I have to add it to the panel often.

The bzr branch I can't even run, it crashes when I try to add it to the panel.

p.s. I removed the "saved-session" folder, which was empty. I don't think it had any effect.

---

### Post by M7S on 2010-05-10
Do you have a slow computer? We think it has something to do with the startup time of dockbarx. I hoped removing saved-session should work always but perhaps not. There is a change in the bzr branch that might work for you. The code has been spilt up in modules and that could perhaps help (some testing points to that, but it's far from certain). To install it it run "./setup.py install" when you pulled the branch.

---

### Post by snoxu on 2010-05-10
BTW I'm running Arch Linux on two laptops. An Asus G1 (2,0Ghz C2D, 2GB ram and 64bit Arch, I wouldn't call it slow) and a Asus netboot (Atom cpu and 32bit Arch, it's somewhat slow).

For some reason I can only run the bzr on my Asus G1 the standard version crashes emediatly. My netbook will only run the standard dockbarx the bzr crashes emediatly when I try to add it to gnome panel.

They will both crash at login regardless. Can't really explain it

p.s. My netbook setup does not have a gnome-session folder.

---

### Post by NetBeholder on 2010-05-11
> **M7S said:**
> Well, there should be a fix now.

Go to /home/username/.config/gnome-session and remove the folder "saved-session". Reboot. Tell me if it works.

It works! Thank you! After reboot and few login-logout no error occur :)

---

### Post by M7S on 2010-05-11
> **snoxu said:**
> BTW I'm running Arch Linux on two laptops. An Asus G1 (2,0Ghz C2D, 2GB ram and 64bit Arch, I wouldn't call it slow) and a Asus netboot (Atom cpu and 32bit Arch, it's somewhat slow).

For some reason I can only run the bzr on my Asus G1 the standard version crashes emediatly. My netbook will only run the standard dockbarx the bzr crashes emediatly when I try to add it to gnome panel.

They will both crash at login regardless. Can't really explain it

p.s. My netbook setup does not have a gnome-session folder.
I'm beginning to suspect that you perhaps are suffering from a completely different bug than the rest. Do you get any errors when you run dockbarx in window, "dockbarx.py run-in-window" or "dockbarx_factory.py run-in-window"? Do you have any errors connected to dockbarx in ~/.xsession-errors?

Oh, if you have dockbarx.py in /usr/bin you should delete it if you are using bzr branch.

---

### Post by snoxu on 2010-05-11
> **M7S said:**
> I'm beginning to suspect that you perhaps are suffering from a completely different bug than the rest. Do you get any errors when you run dockbarx in window, "dockbarx.py run-in-window" or "dockbarx_factory.py run-in-window"?
This is what I got when I ran it on a window and then closed the window (this on my netbook BTW, these comands don't work, not found, for the bzr branch):

dockbarx.py run-in-window

** (dockbarx.py:13727): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'
How would I check for those?
** (dockbarx.py:13727): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:13727): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload

Am I supposed to leave it running and log out log in to test it?


> **M7S said:**
> Do you have any errors connected to dockbarx in ~/.xsession-errors?
I have no clue. I don't have that file in my home directory.

> **M7S said:**
> Oh, if you have dockbarx.py in /usr/bin you should delete it if you are using bzr branch.
I running the standard version on my netbook. It'll be a while before I can check on my other laptop where I'm running the bzr branch.

---

### Post by ScdGigi on 2010-05-12
> **M7S said:**
> Well, there should be a fix now.

Go to /home/username/.config/gnome-session and remove the folder "saved-session". Reboot. Tell me if it works.

Seems to works..

Thank you!!

---

### Post by bra|10n on 2010-05-14
> **snoxu said:**
> This is what I got when I ran it on a window and then closed the window (this on my netbook BTW, these comands don't work, not found, for the bzr branch):

dockbarx.py run-in-window

** (dockbarx.py:13727): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'
How would I check for those?
** (dockbarx.py:13727): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:13727): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload

Am I supposed to leave it running and log out log in to test it?



I have no clue. I don't have that file in my home directory.


I running the standard version on my netbook. It'll be a while before I can check on my other laptop where I'm running the bzr branch.


:confused: I have the same errors so it seems;

dockbarx.py run-in-window
** (dockbarx.py:1870): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:1870): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:1870): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload
Opened window matched with gio app on id: nautilus
Opened window matched with gio app on id: gnome-terminal
/usr/bin/dockbarx.py:735: DeprecationWarning: PyArray_FromDimsAndDataAndDescr: use PyArray_NewFromDescr.
  for row in pb.get_pixels_array():
Opened window matched with gio app on executable: firefox
Opened window matched with gio app on id: gedit
Opened window matched with gio app on id: gedit

It seemed to install ok and is running. Only I can't access "Properties" via right click so am stuck at default option. ???

And xsessions-errors shows nothing related

---

### Post by M7S on 2010-05-14
Sorry, I should have mentioned. Nothing of that is really errors, just the things that always shows. 

About preference dialog, 
1) If you installed manually, did you copy dbx_preference.py to /usr/bin
2) There is a bug in dbx_preference.py that might affect you, it's fixed and will be in the next release.

---

### Post by bra|10n on 2010-05-14
> **M7S said:**
> Sorry, I should have mentioned. Nothing of that is really errors, just the things that always shows. 

About preference dialog, 
1) If you installed manually, did you copy dbx_preference.py to /usr/bin
2) There is a bug in dbx_preference.py that might affect you, it's fixed and will be in the next release.

Cheers :KS
dbx_preference.py not in /usr/bin was what was wrong.
You might like to include it in the Read Me file
Thanks again

---

### Post by rospo84 on 2010-05-17
Same problem for me...

```
raffeee@raffeee:~$ dockbarx.py 
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: impossibile aprire il file oggetto condiviso: Nessun file o directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: impossibile aprire il file oggetto condiviso: Nessun file o directory

** (dockbarx.py:10828): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:10828): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:10828): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/dockbarx.py", line 126, in <module>
    import Image
ImportError: No module named Image

```

---

### Post by na12 on 2010-05-17
> **rospo84 said:**
> Same problem for me...

```
raffeee@raffeee:~$ dockbarx.py 
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: impossibile aprire il file oggetto condiviso: Nessun file o directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: impossibile aprire il file oggetto condiviso: Nessun file o directory

** (dockbarx.py:10828): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:10828): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:10828): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/dockbarx.py", line 126, in <module>
    import Image
ImportError: No module named Image

```
Same problem here,I am running ArchLinux.

Edit: installing python-imaging solved problem

---

### Post by snoxu on 2010-06-16
I'm running bzr branch on Arch. It is still crashing though. Any ideas?

---

### Post by M7S on 2010-06-16
Ok. We take it from the start once again, since I don't remember all the details. You still get no error messages when running in window?
```
dockbarx_factory.py run-in-window
```
It crashes some times on login (or every time?) and not if added to dockbarx later?

Do you have a /usr/bin/dockbarx.py file? If so, it should be deleted.

---

### Post by snoxu on 2010-06-16
```
dockbarx_factory.py run-in-window

** (dockbarx_factory.py:3775): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:3775): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:3775): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload
Opened window matched with gio app on id: chromium
Opened window matched with gio app on id: terminal
```

It only crashes **sometimes** at login. When added later it does not crash.

I do not have the  /usr/bin/dockbarx.py file. I have  /usr/bin/dockbarx_factory.py

Thanks again.

---

### Post by vauge on 2010-06-25
#sudo apt-get install python-keybinder

Solved it for me. :)

---

### Post by ls8_ on 2010-07-17
I have installed the bzr version, removed dockbarx.py, installed all the various suggested dependencies and deleted saved-session, still not working here.

```
robert@robert-laptop:/usr/share/dockbarx$ dockbarx_factory.py run-in-window

** (dockbarx_factory.py:2281): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:2281): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:2281): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory.py", line 26, in <module>
    import dockbarx.dockbar
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 36, in <module>
    from groupbutton import *
  File "/usr/lib/python2.6/dockbarx/groupbutton.py", line 39, in <module>
    import zg
  File "/usr/lib/python2.6/dockbarx/zg.py", line 40, in <module>
    result_type=datamodel.ResultType.MostRecentSubjects,
NameError: name 'datamodel' is not defined

```

---

### Post by M7S on 2010-07-17
Yes, there's a new bug in the latest version.  Zeitgeist which is supposed to be an optional package was accidentally made mandatory. To fix it, install zeitgeist with these commands:

```
sudo add-apt-repository ppa:zeitgeist/ppa && sudo apt-get update[FONT=Verdana]
[/FONT]sudo apt-get install zeitgeist libzeitgeist-1.0-0
```

---

### Post by ls8_ on 2010-07-17
Success, thank you!:D

---

### Post by anantshri on 2010-07-20
> **M7S said:**
> Yes, there's a new bug in the latest version.  Zeitgeist which is supposed to be an optional package was accidentally made mandatory. To fix it, install zeitgeist with these commands:

```
sudo add-apt-repository ppa:zeitgeist/ppa && sudo apt-get update[FONT=Verdana]
[/FONT]sudo apt-get install zeitgeist libzeitgeist-1.0-0
```

thanks that solved my problem.

but if its made mandatory why don't the deb package mark it as dependency.

---

### Post by M7S on 2010-07-21
Well, because the bug is fixed in x.0.39.6, which hasn't been built for the ppa yet.

---

### Post by Dragonlaw on 2010-07-21
Hello,

after installing Zeitgeist the problem went away, but after I did the upgrade to 0.39.6 the problem's back!

I got "The panel encountered a problem while loading "OAFIID:GNOME_DockBarXApplet"

---

### Post by M7S on 2010-07-22
~ppa4 were finnished building 40 minutes ago. Hopefully the problems are fixed now.

---

### Post by Vince N on 2010-07-26
Having the same issue here.

---

### Post by M7S on 2010-07-26
Same error message dialog? That message just tells us that something is wrong, not what.

run dockbarx in window and post the error.

```
dockbarx_factory.py run-in-window
```

---

### Post by Tenntrailblazer on 2010-07-30
brian@brian-desktop:~$ dockbarx_factory.py run-in-window

** (dockbarx_factory.py:2003): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:2003): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:2003): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory.py", line 71, in <module>
    dockbarwin = DockBarWindow()
  File "/usr/bin/dockbarx_factory.py", line 39, in __init__
    self.dockbar = dockbarx.dockbar.DockBar(None)
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 173, in __init__
    self.reload()
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 289, in reload
    self.update_pinned_apps_list()
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 949, in update_pinned_apps_list
    path = gb.desktop_entry.getFileName()
AttributeError: 'NoneType' object has no attribute 'getFileName'
brian@brian-desktop:~$ 

This is what I get.  I think I have tried everything in this thread

---

### Post by bububub on 2011-04-08
Hi everyone!!

After hours an hours of looking for a solution i've found it, well i thing so..

After installing this package: indicator.applet.session the dockbarx start perfect.

Hope this help you. Bye Bye!

---

### Post by adonet on 2011-06-05
> **bububub said:**
> Hi everyone!!

After hours an hours of looking for a solution i've found it, well i thing so..

After installing this package: indicator.applet.session the dockbarx start perfect.

Hope this help you. Bye Bye!

This doesn work for me I&#7743; afraid. The applet isn´t even capable of placing itself on the panel. It gives this error: Het paneel heeft een probleem geconstateerd bij het laden van ‘OAFIID:GNOME_DockBarXApplet’. (something as the panel had a problem loading  "OAFIID:GNOME_DockBarXApplet")

What shall I do?

---

### Post by M7S on 2011-06-05
Start with  ```
dockbarx_factory run-in-window
``` if you haven't done so already.

---

### Post by FanatikCZ on 2011-07-12
The solution with bzr branch worked. Thanks a lot!

---


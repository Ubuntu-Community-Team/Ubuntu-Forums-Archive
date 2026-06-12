---
title: "DockbarX no longer shows open apps or launchers, i.e. nothing."
date: 2010-06-17
forum: General Help
---

### Post by finny388 on 2010-06-17
Ubuntu 10.04 fresh install on eee 900.

I had previously tried Cairo-Dock and AWN (successfully but I like that DockbarX is integrated into the panel)

I installed Dockbarx like so:
```
sudo add-apt-repository ppa:dockbar-main/ppa
sudo apt-get update
sudo apt-get install dockbarx
```

DockbarX was working.

Then I uninstalled Cairo and AWN with Synaptic.

I got a notification of an error in the panel saying I had broken packages - see broken package filter to check it out.

I can't find filters in Synaptic.

Then I noticed DockbarX was empty (and I had pinned Firefox to it)

So I tried uninstalling and reinstalling via terminal. No problems with that but when added it to the panel again it was still empty .

I rebooted several times during these attempts.

I read on launchpad.net: [URL="https://bugs.launchpad.net/dockbar/+bug/579029"]https://bugs.launchpad.net/dockbar/+bug/579029
[/URL]
> Symptoms:
------------------------------

- Launchers disappear
- Open applications not reflected in launchers

Jun 7/2010 status:  	 New &#8594; Incomplete

Affected Versions:
------------------------------

- 0.24.x
- 0.30.x.

But I have 0.39.3-1.

Any ideas?

---

### Post by finny388 on 2010-06-17
^

---

### Post by M7S on 2010-06-18
Run dockbarx in window

```
dockbarx_factory.py run-in-window
```

and post the errors you've got. Perhaps you have uninstalled some dependencies, or something.

Regards,
M7S
DockbarX developer

---

### Post by finny388 on 2010-06-18
Thanks M7S. Here is the result:

```
dockbarx_factory.py run-in-window

** (dockbarx_factory.py:1889): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1889): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1889): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory.py", line 71, in <module>
    dockbarwin = DockBarWindow()
  File "/usr/bin/dockbarx_factory.py", line 39, in __init__
    self.dockbar = dockbarx.dockbar.DockBar(None)
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 303, in __init__
    self.reload()
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 393, in reload
    self.add_launcher(identifier, path)
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 758, in add_launcher
    self.make_groupbutton(identifier=identifier, launcher=launcher, path = path)
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 702, in make_groupbutton
    gb = GroupButton(class_group, identifier, launcher, app)
  File "/usr/lib/python2.6/dockbarx/groupbutton.py", line 285, in __init__
    self.button.drag_source_set_icon_pixbuf(self.icon_factory.find_icon_pixbuf(32))
  File "/usr/lib/python2.6/dockbarx/iconfactory.py", line 514, in find_icon_pixbuf
    message_format='%s %s.'%(_("Cannot load icon for launcher"), self.launcher.get_identifier())
AttributeError: 'NoneType' object has no attribute 'get_identifier'

```

I thought a reinstall would restore dependencies. (not a linux guru by any means). Does this mean the package is corrupted?

DockbarX seems highly configurable yet light on resources. I hope to see it working. Thanks again.

---

### Post by M7S on 2010-06-18
Rigth, ok. Didn't understand the problem you had correctly before. The error message tells me that you suffer from this bug: [https://bugs.launchpad.net/dockbar/+bug/592304](https://bugs.launchpad.net/dockbar/+bug/592304)

There is a (possible) fix that will be in the next release of dockbarx. I might release it tomorrow or some time next week.

---

### Post by finny388 on 2010-06-18
Okay thank you.

How can I know when the new release is out?
How to upgrade?

p.s. is this a purely python project?

thank you so much for your attention to this problem.

---

### Post by M7S on 2010-06-19
Well, if you use the repositories, it will turn up as an update. Othervice you can subscribe to DockbarX's gnome-look page. [http://gnome-look.org/content/show.php/DockbarX?content=101604](http://gnome-look.org/content/show.php/DockbarX?content=101604)

If you don't feel like waiting you can get the unreleased fix right away from bzr (Ignore the message about not being logged in, you'll still get the code):
```
sudo apt-get install bazaar
bzr branch lp:dockbar/dockbarx
```

Yes, dockbarx is a pure python project. I've been thinking about porting the theme stuff to C to speed things up but I have no experience of programming in C and don't know if it would make installing dockbarx more complicated.

---

### Post by finny388 on 2010-06-19
Thank you for the reply.

Do I need to check off Unsupported updates to receive dockbarx's update?

I currently have the following in Synaptic's Sources box:
```

Important security updates (lucid-security) -checked
Recommended updates (lucid-updates) -checked
Pre-released updates (lucid-proposed) -unchecked
Unsupported updates (lucid-backports) -unchecked
```

---

### Post by M7S on 2010-06-19
DockbarX isn't in any ubuntu repository so you need none of those. You need the dockbar ppa, which you should have if you installed dockbarx from it.

---

### Post by finny388 on 2010-06-24
Hello M7S,

Originally I installed the ppa for dockbarx with:
```
sudo add-apt-repository ppa:dockbar-main/ppa
```

I see there is a new version released on gnome-look.

**When will it be in the repository?**

I ran:
```
sudo apt-get update
[sudo] password for frank: 
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ lucid/partner Translation-en_CA              
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/ lucid/main Translation-en_CA
...
```

then
```
sudo apt-get install dockbarx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dockbarx is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

---

### Post by M7S on 2010-06-25
The ppa always comes a little time after I released the code on gnome-look and launchpad. I'm not the one that does the packaging for the ppa, so it depends on when the packager sees the new release and has time to package it.

I can see that the package is building now though, it will be in the ppa within a couple of hours:
[https://launchpad.net/~dockbar-main/+archive/ppa](https://launchpad.net/~dockbar-main/+archive/ppa)

---

### Post by finny388 on 2010-06-25
It's there now
and it appears to work again
thanks M7S!!

---

### Post by finny388 on 2010-06-25
It says it can't find the icon for Firefox and shows a question mark in its place.

I can't see any way to point it to the icon file. Is it possible?

Also, is there a dockbarx forum or more appropriate place for me to post questions like this?

thanks

---

### Post by finny388 on 2010-06-25
just to let you know:

in Preferences/Popup Window/Alignment, left and right are backwards.

---

### Post by M7S on 2010-06-25
Thanks for confirming that the bug is fixed.  

Unpin firefox and pin it again. That should fix it.

Align left and right is correct (on my machine at least). Align left means that the left side of the popup window is in line with the left side of the group button, and vice versa.

---

### Post by finny388 on 2010-06-25
about alignment, I understand now
unpinning and pinning Firefox fixed the icon

2 more questions
1. On the 2nd screen shot on the [gnome look page]("http://gnome-look.org/content/preview.php?preview=2&id=101604&file1=101604-1.png&file2=101604-2.png&file3=101604-3.png&name=DockbarX&PHPSESSID=30657440814596806fcdae4046d182f8") each icon appears to show a number over top indicating the number of instances of that app that are open. How do I do this?

2. is there a dockbarx forum or more appropriate place for me to post questions like this?

thanks again

---

### Post by M7S on 2010-06-25
1. That is dependant on the theme. Quite a few themes has icons. The theme in that screenshot is sunny-c, you can find it in the package dockbarx-themes-extra.

2. No, there's no forum. On gnome-look you can leave comments if you like. On launchpad you can file bugs and you can ask questions there as well.

---

### Post by finny388 on 2010-06-25
OK, thanks for the info

Well while I'm here I'd like to tell you that every time I reboot or every time I add DockBarX to a panel, I get this dialogue box message (twice (I click ok, it comes up again, I click ok, then DockBarX starts)):
> DockBarX

Cannot load icon for launcher Firefox Web Browser.

So every reboot I have to unpin and pin again.

If I can provide you with any more info let me know.

thanks

---

### Post by M7S on 2010-06-29
Sorry for not answering on this one.

Firstly, just so that we don't talk about different things... You pin by right clicking the group button and choose pin, right?

Is your firefox installed in any unusual way?

Add the file /usr/share/applications/firefox.desktop as an attachment to your post or copy-paste it's content.

---

### Post by finny388 on 2010-06-29
> You pin by right clicking the group button and choose pin, right?
Correct


Firefox was pre-installed.

I did update yesterday using
```

sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
sudo apt-get update
sudo apt-get upgrade
```

The problem is now worse: if Firefox is closed or minimized, the icon changes to a default white window icon despite unpinning and repinning.

See attachment.
Thanks for helping.

---

### Post by finny388 on 2010-07-04
FYI M7S

I re-established the Firefox shortcut in the Ubuntu's main menu, unpinned the old one, and dragged the re-established link to DockbarX and it has been fine ever since.

---


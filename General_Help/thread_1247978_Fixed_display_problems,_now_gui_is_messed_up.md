---
title: "Fixed display problems, now gui is messed up"
date: 2009-08-23
forum: General Help
---

### Post by Sleette on 2009-08-23
Pretty much brand new at this, having installed 9.04 just two days ago (never used Linux before).  I've been through a few tutorials so I can get around via the command line and do basic stuff but the whole thing is still pretty new.

After installation, which seemed to go very smoothly, I was up and running with no problems to speak of.  At some point I shut down the computer and when I next restarted my desktop resolution was set to 640x480 (it had been running at 1280x1024).  As I have an Nvidia card installed I used the Nvidia control panel to change the diplay back to the proper resolution but couldn't save the settings (error writing to the xconf file or some such) and each time I rebooted would end up at 640x480 again.

So I read some forums and found that I could manually save the settings by executing nvidia-xconfig and nvidia-settings from the command line.  Which I did, and it fixed my problem; that is, I could reboot and it would keep my resolution settings.

Then I noticed that the gui was messed up in a few ways:  windows didn't have a close button any more; my panels (which I hadn't changed from the default installation) had the icons re-arranged; some dialog windows just don't seem to show up at all any more (just a white box); I can no longer re-size windows; and probably worst of all I couldn't launch a working terminal (just a white box with no borders that I couldn't type in).  I was able to execute a terminal session directly from the terminal file in the shell though, just not from the menu.

So I was thinking that maybe there was some way to reset Gnome (which I understand is the app that controls such things) to default settings or something to that effect but I couldn't find anything and frankly don't even know if that's the right way to go anyway.  At this point I'm debating between just re-installing the distro from the disk and starting over but I thought I'd pose my problem here and see if anyone has any suggestions for a fix.

Any suggestions would be much appreciated..

---

### Post by loomsen on 2009-08-23
You're obviously missing a window decorator.

Add a startup entry (System -> Preferences -> Session/Startup Applications)

command: metacity --replace

[[img]http://www.ubuntu-pics.de/thumb/22772/shot_19_BmTW7G.png[/img]](http://www.ubuntu-pics.de/bild/22772/shot_19_BmTW7G.png)

This should launch metacity at startup, providing window manager functionalities like resizing, closing, minimizing, focussing and such.

If you want a fresh user account, simply add another user...

```

adduser foobar
```

follow the instructions to set up a password and then you should be able to login using this newly created account (/etc/skel is the folder holding default user home's files, so if you didn't change /etc/skel the new account will look like the initial account just after installation.

---

### Post by Sleette on 2009-08-24
Thanks, adding the metacity fixed up the window behaviour.. but the panels were still screwed up so I did as you suggested and added a new account.  I was surprised to see that I had to add the metacity at startup for the new account as well or else the windows didn't function properly as before.  But all is good now, I've got a couple learning/beginning Linux books coming in the mail soon so I'm sure one day I'll understand it.

Thanks for your help, much appreciated.

---


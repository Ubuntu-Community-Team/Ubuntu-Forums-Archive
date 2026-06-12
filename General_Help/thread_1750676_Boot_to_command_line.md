---
title: "Boot to command line"
date: 2011-05-05
forum: General Help
---

### Post by chadcan on 2011-05-05
I installed Ubuntu 11.04 desktop, it's a fresh install. Everything is running great. But how do I configure it to boot to command prompt instead of the GUI. None of the old methods work in version 11.04.
Like change the changing /etc/default/grub to "quiet splash text"
Or
sudo update-rc.d -f gdm remove

Any idea?

---

### Post by Hakunka-Matata on 2011-05-05
[http://help.ubuntu.com/community/Grub2#Reinstalling](http://help.ubuntu.com/community/Grub2#Reinstalling)

---

### Post by wilee-nilee on 2011-05-05
> **Hakunka-Matata said:**
> [http://https://help.ubuntu.com/community/Grub2#Reinstalling]("http://https//help.ubuntu.com/community/Grub2#Reinstalling")

That is a 404 link that is a redirect, OP do not click it is nowhere.

---

### Post by sisco311 on 2011-05-05
> **chadcan said:**
> I installed Ubuntu 11.04 desktop, it's a fresh install. Everything is running great. But how do I configure it to boot to command prompt instead of the GUI. None of the old methods work in version 11.04.
Like change the changing /etc/default/grub to "quiet splash text"
Or
sudo update-rc.d -f gdm remove

Any idea?

You can disable gdm by runnig:
```
echo manual | sudo tee -a /etc/init/gdm.override
```

EDIT: it's the Upstart equivalent of *sudo update-rc.d -f gdm remove*

See:
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
or more precisely:
[http://upstart.ubuntu.com/cookbook/#ubuntu-natty-override-files-ubuntu-transient](http://upstart.ubuntu.com/cookbook/#ubuntu-natty-override-files-ubuntu-transient)

EDIT2: and
[http://upstart.at/2011/03/11/override-files-in-ubuntu-natty/](http://upstart.at/2011/03/11/override-files-in-ubuntu-natty/)

---

### Post by Hakunka-Matata on 2011-05-05
HyperLink in Post #2 corrected, sorry

---

### Post by matthewh3 on 2012-02-13
> **sisco311 said:**
> You can disable gdm by runnig:
```
echo manual | sudo tee -a /etc/init/gdm.override
```

EDIT: it's the Upstart equivalent of *sudo update-rc.d -f gdm remove*

See:
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
or more precisely:
[http://upstart.ubuntu.com/cookbook/#ubuntu-natty-override-files-ubuntu-transient](http://upstart.ubuntu.com/cookbook/#ubuntu-natty-override-files-ubuntu-transient)

EDIT2: and
[http://upstart.at/2011/03/11/override-files-in-ubuntu-natty/](http://upstart.at/2011/03/11/override-files-in-ubuntu-natty/)

If I run this command Ubuntu will always boot to the command line instead of the GUI yes?  If so how could the desktop be restarted?

---

### Post by HiImTye on 2012-02-13
ctrl+alt+f1 to get to a CLI and then kill lightgdm
```
sudo service lightgdm stop
```when you want to restart
```
sudo reboot
```

---

### Post by drs305 on 2012-02-13
> **matthewh3 said:**
> If I run this command Ubuntu will always boot to the command line instead of the GUI yes?  If so how could the desktop be restarted?
You can add "text" to the kernel options in the Grub entry which will cause the boot to a login prompt. I've tried it in a VM and it works.

You can test it by pressing 'e' at the grub menu to enter the editing mode. Cursor to the end of the 'linux' line. Remove 'vt.handoff=7" and add *[COLOR="DarkRed"]text[/COLOR]*

CTRL-x to boot. 

If you like what it did, open */etc/default/grub* as root and add *text* (and remove "vt.handoff=7" if it exists) from the "GRUB_CMDLINE_LINUX_DEFAULT=" line.

Save the file, then run "sudo update-grub" to make it permanent.

---

### Post by Cookieh on 2012-02-13
Every time I booted I used recovery console to boot into command line but that isnt great so thanks for posting this, it worked for me

---

### Post by Rafterman414 on 2012-02-13
I did a different method to get cli only. I edited the file /etc/init/lightdm.conf and changed this:
```

start on ((filesystem
                         and runlevel [!06]
                         and started dbus
                         and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                                or stopped udev-fallback-graphics))
                                or runlevel PREVLEVEL=S)
stop on runlevel [016]

```I changed it to this:
```

start on []
stop on runlevel [0123456]
```

then I edited ~/.profile to contain an alias to start lightdm. This is what I added.

```
 alias startgui='sudo service lightdm start'
```Then I added an alias to stop lightdm by also adding this:

```
 alias stopgui='sudo service lightdm stop'
```if I want to start up the GUI i enter startgui and if I want to shut it down I do CTRL+ALT+F1 and then enter stopgui.

---


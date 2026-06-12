---
title: "Help w/ Dual monitor display"
date: 2012-05-25
forum: General Help
---

### Post by latinlightning on 2012-05-25
Ubuntu 11.04 32-bit on a old OmniTech Pentium 4/2.4GHz processor.

I need help with getting my dual monitors set-up. As of right now, both monitors are displaying the same output. When I head to System>Preferences>Monitors it states "Unknown" when I click the "Detect Monitors" button. Also, "Additional Drivers" does not detect any proprietary drivers.

Here are the outputs of the following commands:

```
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G400/G450 [102b:0525] (rev 82)
``````
sudo lshw -C display
[sudo] password for user: 
  *-display               
       description: VGA compatible controller
       product: MGA G400/G450
       vendor: Matrox Graphics, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
       configuration: driver=matrox_w1 latency=32 maxlatency=32 mingnt=16
       resources: irq:16 memory:f2000000-f3ffffff memory:fe9fc000-fe9fffff memory:fe000000-fe7fffff memory:fe9c0000-fe9dffff

```

---

### Post by papibe on 2012-05-25
Hi latinlightning.

There is a chance that we can get some useful info from the X log file.

Turn off your computer, then turn on and plug all your monitors. Then turn on your computer.

Once you get to the desktop, please take the content of this file:
```
/var/log/Xorg.0.log
```
and paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"). Post back the links here so we can take a look.

Regards.

---

### Post by latinlightning on 2012-05-25
As requested:

[http://paste.ubuntu.com/1007387/]("http://paste.ubuntu.com/1007387/")

---

### Post by papibe on 2012-05-25
Looking into... not as easy I as thought (more experience with Nvidia).

How the monitors are connected?
Both using a different VGA output and cable?

Regards.

---

### Post by papibe on 2012-05-25
For what I've seen the only solution is to hardcode the xorg.conf.

Here's are a few ideas:
[LIST]
[*][Matrox Readme]("ftp://ftp.matrox.com/pub/mga/archive/linux/2001/beta_1_2_0/readme.txt").
[*][Matrox Millenium G400]("http://ubuntuforums.org/showthread.php?t=878780")
[/LIST]

You would have to start by creating an appropriate configuration file. Take a look at [this]("http://ubuntuforums.org/showpost.php?p=11964907&postcount=4") to create a basic one.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by latinlightning on 2012-05-26
> **papibe said:**
> Looking into... not as easy I as thought (more experience with Nvidia).

How the monitors are connected?
Both using a different VGA output and cable?

Regards.

Yes, both monitors are connected to the Matrox card using their own VGA output and cable.

---

### Post by latinlightning on 2012-05-26
> **papibe said:**
> For what I've seen the only solution is to hardcode the xorg.conf.

Here's are a few ideas:
[LIST]
[*][Matrox Readme]("ftp://ftp.matrox.com/pub/mga/archive/linux/2001/beta_1_2_0/readme.txt").
[*][Matrox Millenium G400]("http://ubuntuforums.org/showthread.php?t=878780")
[/LIST]

You would have to start by creating an appropriate configuration file. Take a look at [this]("http://ubuntuforums.org/showpost.php?p=11964907&postcount=4") to create a basic one.

I hope that helps, and tell us how it goes.
Regards.

Papibe, this is what I got:

```
sudo Xorg -configure
[sudo] password for user: 

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

and I don't have a /etc/X11/xorg.conf

```
ls -l
total 84
drwxr-xr-x 2 root root  4096 2012-01-12 19:34 app-defaults
drwxr-xr-x 2 root root  4096 2011-04-25 18:05 cursors
-rw-r--r-- 1 root root    14 2011-04-25 18:04 default-display-manager
drwxr-xr-x 4 root root  4096 2011-04-25 18:00 fonts
drwxr-xr-x 3 root root  4096 2012-01-12 19:34 ja_JP.eucJP
drwxr-xr-x 3 root root  4096 2012-01-12 19:34 ja_JP.UTF-8
-rw-r--r-- 1 root root 17394 2010-02-18 18:02 rgb.txt
lrwxrwxrwx 1 root root    13 2011-09-10 18:57 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2011-04-25 18:05 xinit
drwxr-xr-x 2 root root  4096 2011-02-08 07:27 xkb
-rw-r--r-- 1 root root   269 2011-09-21 11:09 xorg.conf.failsafe
-rwxr-xr-x 1 root root   709 2010-11-02 16:17 Xreset
drwxr-xr-x 2 root root  4096 2012-01-28 08:47 Xreset.d
drwxr-xr-x 2 root root  4096 2012-01-28 08:47 Xresources
-rwxr-xr-x 1 root root  3730 2010-12-01 21:34 Xsession
drwxr-xr-x 2 root root  4096 2012-04-22 19:54 Xsession.d
-rw-r--r-- 1 root root   265 2010-02-18 18:02 Xsession.options
-rw-r--r-- 1 root root   601 2011-04-25 17:54 Xwrapper.config

```

---

### Post by papibe on 2012-05-26
Try doing it on text mode, with the X server down:

Close all your graphic applications.

Press Ctrl+Alt+F1 to go to console text mode.

Log into your account with your user.

Run this to stop all graphics running in the background:
```
sudo service gdm stop
```
Now generate the configuration file:
```
sudo X -configure
```
Restart your graphics:
```
sudo service gdm start
```
That should take you to the GUI login screen, but if not press Ctrl+Alt+F7

Tell us how it goes.
Regards.

---

### Post by latinlightning on 2012-05-26
> **papibe said:**
> Try doing it on text mode, with the X server down:

Close all your graphic applications.

Press Ctrl+Alt+F1 to go to console text mode.

Log into your account with your user.

Run this to stop all graphics running in the background:
```
sudo service gdm stop
```Now generate the configuration file:
```
sudo X -configure
```Restart your graphics:
```
sudo service gdm start
```That should take you to the GUI login screen, but if not press Ctrl+Alt+F7

Tell us how it goes.
Regards.

Hi Papibe,

How would I show the results of the *sudo X -configure* command? When I performed *sudo X -configure > outpu*t and I log back in with the *sudo service gdm start*, that file is empty. Am I missing something here?

---

### Post by papibe on 2012-05-26
Usually this command:
```
sudo X -configure
```
generates a xorg.conf either in one of 3 places:
[LIST]
[*]The current directory
[*]the root's home (/)
[*]your user's home
[/LIST]
When you find it, move it to /etc/X11

Regards.

---

### Post by latinlightning on 2012-05-26
Yes, you are right. It was under my Home folder. I have moved both a **xorg** and a **xorg.conf.new** file to /etc/X11.

Here is *ls* of /etc/X11:

```
ls /etc/X11
app-defaults             ja_JP.UTF-8  xorg                Xresources
cursors                  rgb.txt      xorg.conf.failsafe  Xsession
default-display-manager  X            xorg.conf.new       Xsession.d
fonts                    xinit        Xreset              Xsession.options
ja_JP.eucJP              xkb          Xreset.d            Xwrapper.config

```

---

### Post by latinlightning on 2012-05-26
Here is content of xorg.conf.new:

[http://paste.ubuntu.com/1008898/](http://paste.ubuntu.com/1008898/)

And of xorg:

[http://paste.ubuntu.com/1008900/](http://paste.ubuntu.com/1008900/)

---

### Post by BLewis on 2012-05-26
Look, I'll be honest, you really are wasting your time playing around trying to get multi monitor support in 11.10, just install 12.04 which actually has multi monitor support, that way there shouldn't be any bugs!

---

### Post by papibe on 2012-05-26
The xorg.conf file looks like the ones I've seen setting up dual monitors (although for some reason it created 3 screens and monitors).

Did it make any difference?
Is the other monitor recognized or available on 'Monitors'?

Regards.

---

### Post by latinlightning on 2012-05-29
No difference :(

After looking at the previous two links that you provided and doing research on my own, it seems like no one has been able to configure this display card on recent distros of Ubuntu (I believe I read someone stating that the last know distro support was back in 2004). It honestly is an old card, but I figured I may give it a try since it seems like anything is possible with Linux.

I'll probably just start looking for a new video card that's guaranteed to work out of the box. 

Thanks for the help papibe.

---


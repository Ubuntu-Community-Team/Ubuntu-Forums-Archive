---
title: "Ubuntu 11.10 Freezes on splash screen can't update"
date: 2011-12-27
forum: General Help
---

### Post by drcmcs on 2011-12-27
I'm running a dual boot Win 7 and installed 11.10.  At first I thought I was having problems with my Radeon 6450 graphics card driver, but I think I have the right driver.  Now I'm freezing at the Ubuntu splash screen and can only get to a command line.  When I do apt-get update, I get a bunch of "Failed to fetch" messages.  I am not good at the command line and don't know how to post files etc. I really can't find any solution on the forums.  Thanks.

---

### Post by LinuxFan999 on 2011-12-27
What happens if you type "startx" in the terminal, and press enter?

---

### Post by collisionystm on 2011-12-27
> **drcmcs said:**
> I'm running a dual boot Win 7 and installed 11.10.  At first I thought I was having problems with my Radeon 6450 graphics card driver, but I think I have the right driver.  Now I'm freezing at the Ubuntu splash screen and can only get to a command line.  When I do apt-get update, I get a bunch of "Failed to fetch" messages.  I am not good at the command line and don't know how to post files etc. I really can't find any solution on the forums.  Thanks.

I went through the whole radeon thing so I am sure I can help.

What driver did you install? The one from the amd website?

---

### Post by drcmcs on 2011-12-28
When I boot in recovery mode and chose "Drop to root shell prompt" and run the startx command, it displays a lot of what I think are option for the command ending in "-nohwaccess   don't access hardware ports directly".  Then it says:

Fatal server error:
Could not create lock file in /tmp/.tx0-lock

Please consult the The X.Org Foundation support
    at [http://wiki.x.org](http://wiki.x.org)
  for help

 ddxSigGiveUp: Closing log
xinit:  giving up
xinit:  unable to connect to X server: Network is unreachable
xinit:  server error
xauth:  error in locking authority file /root/.Xauthority

However, if I first run "Check all file systems (will exit read-only mode)", I get to a prompt which says "Drop to root shell prompt with networking".  If I choose this selection and run startx, after quickly displaying ten or so lines (too fast to read) the screen goes blank and the computer is locked.

Many thanks for your help.

---

### Post by drcmcs on 2011-12-28
As to the driver for my Radeon HD 6450, I didn't install a driver, but when I ran:

lspci -nn | grep VGA

I got back:

01.00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Caicos [AMD RADEON HD 6450] [1002:6779]

I assumed that this meant that the Caicos driver was installed, which (from everything I could read on the web) I thought was the right one.  I would need instructions to install a different driver.

In the recovery mode I have no problems with screen resolution only in graphics mode.

Thank you too.

---

### Post by drcmcs on 2011-12-29
I think my problem is that I'm using the HDMI output on the Radeon HD 6450.  I guess HDMI is a problem?

---

### Post by collisionystm on 2011-12-29
> **drcmcs said:**
> I think my problem is that I'm using the HDMI output on the Radeon HD 6450.  I guess HDMI is a problem?

I read about a lot of problems regarding HDMI outputs with ubuntu.

did you try the VGA?

I suggest you install

fglrx-updates

also install 

compizconfig-settings-manager

once fglrx-updates installs and you have your GUI, open the amd catalyst control, enable tear free

in compiz config, click OpenGL, disable sync to vblank and set texture filter to fast.

log out and back on

try your hdmi then

---

### Post by drcmcs on 2011-12-30
Thanks for you suggestions, collisionystm.  I'm afraid I'm in a little over my head - usually I can muddle through it, but I can't seem to run anything.  When you ask about VGA, I think when I go to the command line, it is VGA and works fine, but I don't know how to set it in GUI mode.  If I get to GUI mode the screen is flashing sometimes where I can read it sometimes not. But I can't get to GUI mode.  When I get the command line through recovery mode, and run the fglrx-updates, I get the messages:

W: Not using locking for hte read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

I read a little but I don't know about deleting lock files, etc.  When I run apt-get update, I get the "Failed to fetch . . . " messages.  

I'm pretty hosed and can't seem to get to a place where I can run anything.

Thanks for your help anyway.  I think Ubuntu's a little too complicated when I get into this type of problem.

---

### Post by LinuxFan999 on 2012-01-01
It looks like the only thing you can do now is reinstall Ubuntu.
Remember to back up your data, if possible.

---


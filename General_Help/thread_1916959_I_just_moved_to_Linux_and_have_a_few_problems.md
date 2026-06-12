---
title: "I just moved to Linux and have a few problems"
date: 2012-01-29
forum: General Help
---

### Post by Shenarah on 2012-01-29
Hi.

I was finally convinced that Linux was better than Windows so took the plunge and installed it. I really like it but find I have a few problems. Firstly, I leave my PC on without use for a few hours and when I return the mouse starts to misbehave. I can move the pointer but the buttons stop working and I cannot click anything. It randomly returns for a few clicks then stops again. The only way to cure it is to log off and back on again.

I managed to run the system test and it said it was unable to grab the mouse and that I might be under the control of malicious software which was eavesdropping on me. Needless to say I am worried by this seeing as I was told that Linix is more secure than Windows.

Secondly, after first installing Linux the graphics set itself to 1280x1024 via the nvidia configuration but this just squashed everything up and movies looked stupid. The Display settings in system said 'Unknown Monitor' and wouldn't let me set the screen higher than 1280x1024. The nvidia control allowed me to set the correct one that I used in Windows to 1360x768 but whenever I reboot it goes back to auto and the wrong settings, sometimes with a white panel of errors. The nvidia correctly sees my monitor as an LG Electronics M2343A.

I am sorry for the length of this and apologise if it's incorrectly placed but I am close to going back to Windows and don't really want to do this.

Thank you

Shenarah

---

### Post by dino99 on 2012-01-29
which ubuntu are you using ? 11.10 ?

into a terminal:

sudo rm /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

close the running apps if any (like browser ...)
sudo reboot

---

### Post by Shenarah on 2012-01-29
Thanks for that. I will try it. What does it do? Which problem does it address?

---

### Post by Shenarah on 2012-01-29
And now, after rebooting things are bad. The screen resolution is correct but the desktop is buggered. The status bar at the top has gone grey and has lost the cog for logging off. Ctr-alt-del doesn't bring up the shutdown. Most of the icons are missing from the left hand bar and in the settings panel and my home folders have gone grey. 

Help!

---

### Post by Shenarah on 2012-01-29
Help! I restarted again and the screen came back normal but now the mouse buttons do not wok at all and I cannot click on anything. I managed this reply using the cursor keys on my keyboard. My PC is becoming unusable.

---

### Post by Shenarah on 2012-01-29
Also, when it first loads the desktop after starting, I get a box up saying an application wants to access the keyring 'default' but is locked. Does this mean anything?

Sorry to go on but things seem to be going from bad to worse.

---

### Post by L a r r y on 2012-01-29
What version of Ubuntu are you running?  To find out, bring up the Terminal and type:```
lsb_release -a
```
All lowercase letters only, underline before "release," and space before -a.

Mine shows:```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid

```

It is true that Linux is more secure than Windows, for I have never had to worry about a virus attack.  

Security can be enhanced by using a strong log-on password, which is required each time you attempt to modify system settings (like removing the xorg.conf file).  

In the terminal, the word "sudo" will prompt you for your password when you are working on editing or removing system files outside of your home.  Nothing is shown on the screen as you type the password.

You may substitute the word "gksudo" for "sudo" to pop up a password prompt window that will show ***** as you enter your password. 

To answer your question, "what does it do," responding to the first answer you received, I will repeat the response from dino99 and add explanation comments preceded with a # sign:
> Into a terminal:
```

# sudo asks your password, then rm removes
# the file xorg.conf:
sudo rm /etc/X11/xorg.conf
# xorg.conf contains configuration details
# for video card, monitor, mouse, keyboard
# and so on.
# Its removal will cause the system to
# reconfigure itself and recreate an
# xorg.conf file with new settings.

# apt-get update Updates the Package Index

# updates in this case:
sudo apt-get update

# sudo is always required ahead of commands
# that require administrative privileges.
# Commonly referred to as root privileges.

# apt-get install -f attempts to correct
# a system with broken dependencies
# in place.  Dependencies are other
# files that need to be present for
# a given software package to work.
sudo apt-get install -f

# dpkg-reconfigure will reconfigure an
# already-installed package. 
# -phigh sets priority to high.
# -a Reconfigure all installed packages
# that use debconf. Warning: this
# may take a long time.
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

```
close the running apps if any (like browser ...)
```

# Requires password to reboot the computer
# from the command line Terminal:
sudo reboot

```

Sources:
Online:
[https://help.ubuntu.com/8.04/serverguide/C/apt-get.html](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)
In your Terminal:
```
man apt-get
man dpkg-reconfigure

```
These "man pages" are the documentation for each command in your version of Ubuntu.

Navigation in a man page:  Space or page-down to advance a page, page-up to go back a page, up arrow goes back a line at a time, down arrow and Enter will move a line forwards.  Quit the man page with the lowercase Q.

---

### Post by Shenarah on 2012-02-04
Thank you. Most of my issues are now solved. The main problem seems to be the mouse button randomly stopping working. I see this has been reported a number of times but nobody seems to know what the problem is. Every time it happens I have to log out and back again. It's a real pain.

---

### Post by L a r r y on 2012-02-06
> **Shenarah said:**
> The main problem seems to be the mouse button randomly stopping working. 

I use a wireless laser mouse, and there are times when I click and drag, and release, and I still am dragging.  Solution is to click clear and then click and drag again, and release, and if now still dragging I repeat.

That's a pain when trying to draw a selection using the free select tool in Gimp.

The ONE thing about this computer is that its sound card seems to be almost spot-on in its frequency calibration, but it has some USB issues with both a usb keyboard and the mouse.

Cheers.

---

### Post by ecopccare on 2012-02-07
I came across a problem once and it happened to be that all ps2 mice had the problem but when i plugged a usb mouse in it was just fine... 
Linux does have a slightly better security model than windows, but as long as you play within certain rules.  Most software you will every want to use can be found within the repositories (ie Ubuntu Software Center).  These are tested to work on your system, malware free and are generally high quality and should work without too much initial setup or configuration.  If you go around installing stray .deb files you find online you no longer have that safety, and could potentially find something damaging to your system, but those are pretty dang rare in the wild.  It could happen tho...

---


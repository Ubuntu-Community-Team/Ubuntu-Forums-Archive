---
title: "Computer Boots into Terminal"
date: 2011-05-02
forum: General Help
---

### Post by Hoogs on 2011-05-02
I recently upgraded to 11.04, and after messing around with Unity for awhile decided I'd try out Gnome 3.  After rebooting to finish the installation, I noticed that the interface had reverted to what my desktop looked like in 10.10, except the color scheme was different.  I also got an error message saying my computer's graphics couldn't handle Gnome 3 (I'm on a netbook).  Then I went online to look up instructions on how to switch back to Unity (since the option wasn't available on the login screen).  After following the first step, which involved entering a command into the terminal, I left the house for awhile.  When I got back, the screen was black with white text (terminal-esque) asking for my username.  After typing it in and pressing enter, it asked for my password, and after entering that it became a "terminal".  This screen comes up every time I start my computer now, and I have no idea what to do.  I could reinstall Ubuntu from a flash drive, but I want to be able to access my files.  Is there any way to get around this, or recover my files without taking out the hard drive?  As you can probably tell from my post, I'm very new to Ubuntu and Linux, and the mess I'm now in is the result of acting on uneducated impulse.  I appreciate any advice.

---

### Post by Hoogs on 2011-05-02
Bump.

---

### Post by x C0MMAND0 x on 2011-05-02
After you login via the terminal as you are stating, try typing 

```
startx
```

to see if that starts a graphical desktop.

If you do get to a graphical desktop, check the file **/etc/default/grub file** line that as shown says "text".  If it does, then it should be booting to text.  If you don't want it to, change it from "text" to "quiet splash".  You can edit this file by running gedit or nano or whatever means you want.

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=**"text"**
GRUB_CMDLINE_LINUX=""

```

Try that as a starting point.

---

### Post by Hoogs on 2011-05-02
After logging in, typing startx, and hitting enter it brought me to another terminal, except the font is different (a little smaller) and I'm unable to type anything.

---

### Post by x C0MMAND0 x on 2011-05-02
Once you are logged in, type 

```
 cat /etc/default/grub 
```

And post the output of that here please.

---

### Post by Hoogs on 2011-05-02
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#    info -f grub -n 'Simple configuration'
 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=**"quiet splash"**
GRUB_CMDLINE_LINUX=""
 
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD . . . .)
#GRUB_BADRAM="0x01234567, 0xfefefefe, 0x89abcdef, 0xefefefef"
 
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command 'vbeinfo'
#GRUB_GFXMODE=640x480
 
# Uncomment if you don't want GRUB to pass "root-UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
 
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
 
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by NightFoxyarrith on 2011-05-02
Try entering these commands (it's what I did to get rid of gnome 3):
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get dist-upgade
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

If that doesn't get you back to unity you might try reinstalling your graphics driver (I don't which one but I'm assuming intel because most netbooks have an intel chipset)
sudo apt-get install xserver-xorg-video-intel

---

### Post by x C0MMAND0 x on 2011-05-02
Yea, it looks like your settings are correct in that file, so the problem is not being able to start x server.  Run the commands above that the user posted and see how that goes.  Keep us updated.

---

### Post by cipherboy_loc on 2011-05-02
Also try pressing Ctrl+Alt+F7, and seeing if that takes you to the log in screen. If that doesn't (Ctrl+Alt+F1 to get back to where you logged in), try:

```

sudo /etc/init.d/gdm start

```

And post the output of that command.



Cipherboy

---

### Post by Hoogs on 2011-05-02
This:  "sudo apt-get install ppa-purge" returned:  "Unable to fetch some archives".
These:  "sudo ppa-purge ppa:gnome3-team/gnome3"
"sudo apt-get dist-upgade"
"sudo apt-get upgrade" didn't upgrade anything.
This:  "sudo apt-get install ubuntu-desktop" returned:  "Broken packages".

I tried reinstalling the graphics driver and it said it was already at the newest version.

Pressing Ctrl+Alt+F7 led to the purple Ubuntu loading screen, and it looked like it was loading, but nothing happened.

I tried "sudo /etc/init.d/gdm start" but it said "command not found".

I really appreciate all the advice guys.

---

### Post by cipherboy_loc on 2011-05-02
So first of all you might want to try installing gdm:

```

sudo apt-get install gdm

```

Reboot, and if it doesn't take you to a log in page, try the following (from the terminal after login):

```

sudo service gdm status
# If the above says it is stopped try the following:
## If this gives errors, report back.
## If this also returns command not found, try /etc/init.d/gdm start.
sudo service gdm start

```



Cipherboy

---

### Post by Hoogs on 2011-05-02
"sudo apt-get install gdm" didn't work.
 
"sudo service gdm status" returned "gdm stop/waiting".
 
"/etc/init.d/gdm start.sudo service gdm start" returned "No such file or directory".

---

### Post by cipherboy_loc on 2011-05-02
It was supposed to be:

```

sudo service gdm start

```

the /etc/init.d/gdm start. was supposed to be on the line above it. What was the error on the apt-get install? If it is already installed, try:

```

sudo apt-get install --reinstall gdm

```



Cipherboy

---

### Post by Hoogs on 2011-05-02
Both the apt-get install and reinstall asked for a y/n, saying it would require around 20 mb, but they both ended up saying "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

---

### Post by cipherboy_loc on 2011-05-02
Is this a laptop? If so, make sure you plug into an ethernet cable to continue. No, I don't think --fix-missing would fix anything, but the apt-get update might help.


Cipherboy

---

### Post by Hoogs on 2011-05-03
Ok, I'm connected with an Ethernet cable now.

---

### Post by cipherboy_loc on 2011-05-03
Did the apt-get update and apt-get installs work? If so, try the `**sudo service gdm start**`


Cipherboy

---

### Post by NightFoxyarrith on 2011-05-03
Try the steps for deleting gnome 3 again with ethernet, because I think you just didn't have network connection when you tried it, and try this for the graphics:
```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

---

### Post by Hoogs on 2011-05-03
Ok, I deleted Gnome 3 with Ethernet, reinstalled the graphics, rebooted, and it brought me into Unity!  Thanks for all the help everyone, I really appreciate you guys sticking with me on this.

---


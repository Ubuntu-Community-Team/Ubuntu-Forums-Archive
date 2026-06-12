---
title: "Screen unreadable after login"
date: 2012-05-13
forum: General Help
---

### Post by bledsoe on 2012-05-13
After upgrading to 12.04 my system boots to the login screen just fine, and in fact, both of my sons' accounts (one an administrator, one a regular user) seem to work just fine. But when I log in to my account, I get an unreadable screen: the system tries to display my desktop but it looks kind of like an old TV with the vertical hold and the horizontal hold messed up. Lots of flashing and scrolling and unreadable images.

If I do a Ctrl-Alt-F1 from the login screen I can log in to my account, but I'm not sure what to do from there. I also don't understand why both of my sons are experiencing no issues at all on their accounts on this same machine.

Any suggestions (or pointers to similar already-resolved-issues) greatly appreciated.

---

### Post by grahammechanical on 2012-05-13
I am just guessing really.

Are all three of you logging in to the same desktop. Such as Ubuntu (Unity 3D) or Ubuntu 2D?

What video card do you have? Are you using a proprietary video driver or an open source one.

Perhaps your sons are logging in to Ubuntu 2D and you are logging in to Ubuntu. That might be the reason for the difference.

Perhaps one of your sons could run Additional Drivers and find out if a proprietary driver is activated.

Regards.

---

### Post by bledsoe on 2012-05-13
Thanks for the response.  Here's what I was able to find out:

When I type "lspci" at a command line the line with "VGA compatible controller" says "Intel Corporation 82G965 Integrated Graphics Controller (rev 02)".  

I ran the Additional Drivers app from one of my sons' accounts and it says "No proprietary drivers are in use on this system."

Here's what I don't know how to find out:

a) what video driver I'm using;

b) if we are all logging into the same desktop.  Is there some way that I can run Unity (2D or 3D or whatever) from the command line after I log in?  If I just type "unity" at the prompt I get 6 lines of error messages starting with "WARNING: no DISPLAY variable set, setting it to :0"

---

### Post by bogan on 2012-05-14
Hi!, **bledsoe**,

> a) what video driver I'm using;?From a Terminal running:```
sudo lshw -C video
```will list the driver in a line near the bottom.```
sudo  hwinfo --glxcard 
```may give you more info, especially if there is more than one driver available. ```
sudo apt-get install hwinfo 
```if you do not have it already.

You could try 'unity --reset' after you log-in, [for myself, it gives a long string of errors, and does not seem to make any difference.]

If you get a normal GUI log-in screen, you can set the mode Unity 2D, 3D, or Gnome Classic, with the drop-down menu activated by clicking the Icon top right of the login window, [ not top-right of the screen] before entering your password.

Chao!, **bogan**.

---

### Post by HiImTye on 2012-05-14
I think the command you want is
```
unity --replace &
```
unless you want to perpetually reset your Unity settings

---

### Post by bledsoe on 2012-05-14
Thanks bogan and HilmTye.

Apparently my video driver is "i915" though I have no idea what that means.

I have tried setting the mode to Ubuntu 2D, Ubuntu 3D, and Gnome before logging in, but I still get the same unreadable screen.

I can't tell that entering "unity --reset" or "unity --replace &" from a command line do anything at all except give me a few error messages starting with "WARNING: no DISPLAY variable set, setting it to :0"

Other ideas?

---

### Post by bledsoe on 2012-05-18
Well, I finally found a solution of sorts [here]("http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html"), but it's not particularly elegant.

1. From the login screen, I type Crtl-Alt-F1, then login.

2. I then enter "sudo apt-get remove --purge xserver-xorg".

3. I then type Ctrl-Alt-Del to reboot the computer.  During the boot process, before the login screen is displayed, while my computer is displaying the purple "Ubuntu" screen with the five dots on it, I type Ctrl-Alt-F1 to get the terminal screen.  (For some reason it's important to do this before the login screen appears, otherwise the next commands won't work right.)  I wait for the login prompt, then login again as before.

5. I enter "sudo apt-get install xserver-xorg".

6. I enter "sudo dpkg-reconfigure xserver-xorg".

7. Finally, I enter "startx", which starts the GUI and I'm logged in to my Ubuntu account with my GUI running and the flickering unreadable screen is fixed.

The bad news is that this doesn't permanently fix the problem.  (In fact, I'm still not entirely sure what the problem is.)  If I reboot the machine I have to go thru these same steps all over again the next time I want to log back in.  So if anyone has any ideas for a longer term fix, I'd love to hear them.

---

### Post by bogan on 2012-05-19
Hi!, **bledsoe**,

I do not see in your Posts an answer to the query as to in what way differently the other users were operating.  However, it is by no means unusual for problems that affect one user to not do so for others, usually because of some settings that messed things up for that one user.

Having said that, I do not hold a lot of hope that my suggestion will work out because of that fact, but it does work for many using your video card and driver. SO HERE GOES:

When the grub menu opens, highlight the entry you wish to boot to, and press 'e' to display the grub boot script.

Use the arrow keys to navigate to the line that begins with 'Linux', and along it to ' ro ', probably followed by ' quiet splash ', and maybe other options. 

Alter this to read:>  " ro i915.modeset=0 xforcevesa quiet splash " - without the inverted commas; the spaces are important - '=0' is a zero.

Then press 'Ctrl+x' to boot.

Post the results, if it works it can be made permanent, you will find full instructions in MAFoElffen's Blank Screen Sticky in the Installations & Upgrades Forum, Post #1.

[http://ubuntuforums.org/showpost.php?p=10740083&postcount=1](http://ubuntuforums.org/showpost.php?p=10740083&postcount=1)

Chao!, **bogan**.

---

### Post by bledsoe on 2012-05-31
Hi bogan, thanks for the response.

Yes, this seems to work, though the steps I went thru differed slightly from those you suggested:

1. Early in the boot process there's a 2-second window in which you have to press the [ESC] key in order to edit the grub file (grub menu?).

2. I just highlighted the top entry (already selected) and pressed 'e'.

3. I then used the arrow keys to highlight the line that begins with 'kernel' (not 'Linux'), and pressed 'e' again.

4. On this line I changed the part that read 'ro quiet splash' to read 'ro i915.modeset=0 xforcevesa quiet splash' as you suggested.

5. I then pressed [ENTER] to save and exit, then 'b' to continue the boot process.

After that, the machine appeared to boot properly, although the purple "Ubuntu" screen looks a little different than normal, as though the graphics aren't quite right or the screen resolution is set too low.  I also notice a few quick lines of error messages (didn't catch what they said), and then the login screen appears and I can log in normally.  After logging in, the screen resolution appears slightly off (like the desktop doesn't quite fit correctly onto the screen), but it's relatively minor.

I have not yet been able to make these changes permanent, partly because I can't seem to find my "grub" file; it doesn't seem to be in my /etc/default directory as indicated in the link you supplied.  Perhaps that file has been moved or replaced in the Ubuntu version that I have?

At any rate this helped a lot.  I'm going to try to learn some more about grub and the kernel boot process and see if I can't institute a more permanent fix.

---

### Post by bogan on 2012-05-31
Hi!,** bledsoe,**

Glad you are making some progress.

I do not understand how the 'grub' file can **not **be in /etc/default/ and grub still work. It is there in all my versions from 10.04 to 12.04.

I can only suggest you copy it from another installation - if you have one - or from the live CD/Usb -- and I am not even sure that that is possible.

Alternatively ask, and I will post a copy.

Chao!, **bogan**.

---

### Post by bledsoe on 2012-06-29
As far as I can tell, I do not have a /etc/default/grub file. Everything I've read tells me that I should have this file in order to boot properly, but it's not there.

I looked around for a way to re-create this file, but have not been successful. Is there a generic copy somewhere that I could use?

Thanks,

---

### Post by bogan on 2012-06-29
HI!, **bledsoe**,

Here is a copy of my /etc/default/grub file; the only alteration from the standard file for 12.04 LTS and Grub2, is the "#GRUB_GFXMODE=" line, which I have 'commented out'. As far as I remember, the original would have been: "=640x480". 

Alter it to suit your set-up, or leave it commented out. ```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# GRUB_GFXMODE="1920x1080x32"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```You will need to use: ```
gksu gedit
``` to copy/paste and save it in the /etc/default folder as "grub".

Chao!**, bogan**.

---

### Post by bogan on 2012-06-30
Hi!,**bledso**e,

PS. to my Post #12:

After saving the grub file to /etc/default/, you will need to update grub:```
sudo ubdate-grub
```And watch for any error messages as it re-creates grub.conf.

Chao!,** bogan**.

---

### Post by bledsoe on 2012-06-30
I created the grub file in /etc/default. I started with the one you posted and added what I believe are the correct changes so it looks like this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 xforcevesa quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# GRUB_GFXMODE="1920x1080x32"
GRUB_GFXMODE="680x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Then I saved the file, ran sudo update-grub, and didn't see any error messages.

But when I restart, then login from the login screen, I get the same garbled screen as before. If I restart again, but interrupt the boot in the grub stage and manually enter the "i915.modeset=0 xforcevesa" part, I can login to a normal GUI.

Any ideas why this isn't working?

Thanks,

---

### Post by bogan on 2012-07-01
Hi!,** bledsoe**,

I assume you have multiple Ubuntu versions showing in the grub menu- Yes?

If you are saying that the changes do not show in the grub menu displayed when you select the default menu entry, and press 'e', then grub is installed to a different Ubuntu entry.

Try booting to a different entry and checking the /etc/default/grub file there.

Chao!, **bogan.**

---

### Post by bledsoe on 2012-07-01
I have a total of 17 Ubuntu versions that show up in the grub menu: 8 regular ones (e.g., "Ubuntu 12.04 LTS, kernel 3.2.0-26-generic"), 8 recovery mode ones (e.g., same as above but with "recovery mode" at the end of the line), and one that says "Ubuntu 12.04 LTS, memtest86+".

In the grub menu, I selected each of these entries separately, pressed the "e" key, selected the "kernel" line and pressed the "e" key again, and all of them end with "ro quiet splash"; none of them have the "i915.modeset=0 xforcevesa" part that I added to the /etc/default/grub file.

I booted to the second "regular" version in my grub menu (i.e., I entered the i915 stuff manually in the grub menu), then looked at the /etc/default/grub file; it looks the same as when I booted to the first "regular" version.

Do I need to boot to every single different version in my grub menu and check the /etc/default/grub file? What exactly am I looking for?

Thanks,

---

### Post by bogan on 2012-07-01
HI!,** Bledsoe**,

Wow! I've had multiple entries in the grub Menu before, but not that many. I have no idea what causes it except that it happens after a kernal update. Unless, of course if they are all different, which would be quite normal.

Did you in fact check **all** the entries, and none of them showed the changes you made?

Please Post:```
grep "menuentry" /boot/grub/grub.cfg
```Depending on what shows, what we are looking for is which entry script in the grub menu alters after: booting to it, editing the /etc/default/grub, updating grub and restarting to the same entry and check its script. 

The alternative - and i am a bit wary of advising this without more understanding of what works and what does not - is to boot to the latest kernal and run:```
sudo grub-install /dev/sda  # where sda is drive containing the Ubuntu partition you want to be operative
# note: not "sda2"or whatever the partition is called. just the letters of the drive
```There is also another command needed- I need to do a bit more research.

I do not understand your:> In the grub menu, I selected each of these entries separately, pressed  the "e" key, selected the "kernel" line and pressed the "e" key againIf I do that, all the second 'e' press does, is to put a 'e' character in the line. 

EDit: After re-reading all the Posts:  In your Post#9 you gave similar details:>  I then used the arrow keys to highlight the line that begins with 'kernel' (not 'Linux'), and pressed 'e' again.You are describing something quite different to how my grub menu behaves. What version of grub shows at the top of the menu screen?

I would expect it to show: v1.99, though it is actually Grub2. The reason I ask is that I beieve earlier versions did not use an /etc/default file!!

Chao, bogan

---

### Post by bledsoe on 2012-07-01
Ah, things are starting to become clear.

Based on your question about my grub version, I opened a terminal and entered "grub-install -v" and discovered that I had grub version 0.97, which I believe is also referred to as "legacy grub". I followed the instructions at [https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading) and updated to version 1.99, and now my computer seems to boot properly.

I'm not sure why I had the older version of grub. Does grub not update along with the rest of the Ubuntu system?

At any rate, many thanks for all your help, you've been very patient. Hopefully I won't have any further problems with this particular issue.

Thanks, again,

---

### Post by bogan on 2012-07-02
Hi!, **Bledsoe,**

Right! Great! Mystery solved!!

Please mark this thread as 'Solved', and also the other one - you might add a Link to this one, or a para explaining what the solution was.

[ Use the Thread Tools Menu at the top of the thread.]

Chao!,** bogan.**

---


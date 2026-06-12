---
title: "Grub Customizer does not work"
date: 2012-07-24
forum: General Help
---

### Post by gilloz on 2012-07-24
When I try and start Grub Customizer, I get an error window that says the following:  
/usr/sbin/grub-mkconfig:7: /etc/default/grub:9: not found.

I was originally trying to make my Windows 7 as the default program to start.  Searching the Internet I found that using Grub Customizer would help me do this.  It was already installed in my applications so I thought I would try it.  No clue where to start to fix this problem.

---

### Post by oldfred on 2012-07-25
Did you by any chance upgrade and are still using grub legacy? 
This is a grub2 file, does it actually exist?
/etc/default/grub

You can manually change without grub customizer although for most the manual way is more difficult as you have to directly edit /etc/default/grub.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You can use the number it is in the menu or or title to boot Windows as the GRUB_DEFAULT=0 where 0 is changed to the correct menu item line number or exact title. Note that 0 is first line.

If grub 1.99 with submenus it is a bit different - drs305
[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)
find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by gilloz on 2012-07-25
Thanks oldfred for your response.  I do have a /etc/default/grub file and also a /boot/grub/grub.cfg file.  I don't know what version it is.  I need to digest your response and links for a bit before I get back to you.  I am using Ubuntu 12.04 LTS.  I tried to make Windows 7 the default in grub and used the procedures shown in link below.  Did not work so I tried Grub Customizer and got that error window I mentioned above.

[http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader](http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader)

---

### Post by oldfred on 2012-07-25
If there is a typo in /etc/default/grub, I think it will create problems. I had a typo in my 40_custom and it would not update grub.cfg , but a backup or error file.

The procedure I posted I think is identical to the askUbuntu site. I have not done that with 1.99, but do not think it has changed since previous versions of grub2.

Post your /etc/default/grub.

---

### Post by gilloz on 2012-07-25
Here is my /etc/default/grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_FONT=/boot/grub/DejaVuSansMono.pf2
GRUB_DEFAULT= "Windows 7 (loader) (on /dev/sda1)"
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
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by JKyleOKC on 2012-07-25
> **gilloz said:**
> 
```
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2
[COLOR="Red"]GRUB_DEFAULT= "Windows 7 (loader) (on /dev/sda1)"[/COLOR]
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Your GRUB_DEFAULT line is at least part of your problem; it should be a number within quote marks. That is, to boot the topmost item in the Grub menu, it would be
```
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2
[COLOR="Red"]GRUB_DEFAULT="0"[/COLOR]
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```To make it boot your Win7 by default, replace that 0 with the 0-based count of menu lines. That is, if the Win7 item is the 8th line, use "7" for the default.

There may be other errors but this is definitely one, and it seems to match the error message you're getting.

---

### Post by oldfred on 2012-07-25
Unless it just changed with the newest grub as I have not tested that, descriptions are ok, but have to be exact or copy & pasted so even spaces are the same. And I think the quotes are optional on using the line number.

Also did you copy the font to the correct location & is it a valid font? grub's default is the only one in the grub folder normally.
[FONT=Arial]
If not sure you can comment both out and then see if it works, then try one setting, then the other to test.


Grub 1.99 Submenus[/FONT]
[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)
> 
[LIST]
[*]Entries displayed on the main menu can be designated by number or title as with earlier versions of Grub 2.
[LIST]
[*]GRUB_DEFAULT=0
[*]    GRUB_DEFAULT="Ubuntu, with Linux 2.6.38-8-generic"
[/LIST]
 
[/LIST]


---

### Post by gilloz on 2012-07-26
Made the change to Grub_Default = "0", but there is no change.  When I enter sudo update-grub in the terminal, I get the error window: /usr/sbin/grub-mkconfig:7: /etc/default/grub:0: not found.

The /etc/default/grub file has the changes, but it will not update the /boot/grub/grub.cfg file because of the error above.

---

### Post by oldfred on 2012-07-26
Not sure why your grub has issues, I might just uninstall grub including deleting the grub file and totally reinstall. Make sure you have Internet working as it has to download it to reinstall.

If you can boot, you do not have to chroot, skip that step.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by gilloz on 2012-07-26
Just a reminder.  I can still boot into Windows 7 or Ubuntu, but I can't make Windows 7 the default in the grub menu.  That is the only issue I have right now.  Can't seem to get rid of that error window I mentioned above in my replies.

---

### Post by drs305 on 2012-07-26
I'm not sure about the GRUB_FONT line, you might try placing a # symbol at the start just to test it.

In any case, what happens if you upate-grub with the following:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
Since you are getting the 'grub-mkconfig' error this command probably won't work either, but it is a different way of invoking it (as opposed to update-grub).

I'd be inclined to purge/reinstall Grub if you aren't having any success. We can tell you how if you'd like.

---

### Post by gilloz on 2012-07-26
You're right. It didn't work.  It came back with:  /usr/sbin/grub-mkconfig: 7: /etc/default/grub: 8: not found
OK.  I am ready for this purge information.  Thank you.

---

### Post by drs305 on 2012-07-26
This assumes you are currently running your Ubuntu OS.

```

sudo apt-get purge grub-customizer
sudo apt-get update # Retrieve latest package lists
sudo apt-get update # Make sure everything is up to date.
# If you don't have an Internet connection, do not continue!
sudo apt-get purge grub-common # Removes GRUB packages. You will be warned. TAB to OK.
sudo apt-get install grub-pc # Reinstall the GRUB packages

```
When reinstalling, you will be asked where to install. Use the SPACEBAR to select the sda drive. Do NOT select the partition. TAB to OK.

It should automatically run update-grub. You can watch the terminal for the message that it is generating grub.cfg

The generic settings will be restored. If you want to return some of the settings you are currently using to /etc/default/grub, you can refer to the settings you posted earlier in this thread.

If it still fails, you may have to repeat the process after manually deleting all the GRUB Customizer files/folders remaining after you have purged GRUB and before reinstalling.

---

### Post by gilloz on 2012-07-27
Thanks Drs305.  I just climb out of a hole, and turned around and fell into another hole.  I first want to say that your code for purging and installing grub worked like a charm.  I was back in business again.  Slight problem though.  I had multiple entries of Windows 7, Linux kernels and memory tests.  I re-installed Grub Customizer to see if I could get rid of the multiple entries.  I did such a good job that I can no longer boot into Ubuntu.  I somehow manage to eliminate the kernel entries to Ubuntu.  Now, I am only left with Windows 7 and two memory test 86+ entries.  I will close this thread and start a new one to see how I can recover my grub, yet again.  Thanks for your help.  I also want to thank oldFred and JKyleOKC for their responses.

---


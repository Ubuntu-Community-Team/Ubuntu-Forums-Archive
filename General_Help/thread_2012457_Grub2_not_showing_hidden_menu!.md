---
title: "Grub2 not showing hidden menu! ???"
date: 2012-06-29
forum: General Help
---

### Post by mikeym on 2012-06-29
Hi, 

For some reason my laptop is not showing my hidden grub menu, either the splash to let you know that grub has loaded or the menu itself by pressing the escape key. 

This is my current */etc/default/grub*:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_HIDDEN_TIMEOUT=1
#GRUB_HIDDEN_TIMEOUT_QUIET=true
#GRUB_HIDDEN_TIMEOUT_QUIET=false
#GRUB_TIMEOUT=10
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

The only combination of options for GRUB_HIDDEN_TIMEOUT, GRUB_HIDDEN_TIMEOUT_QUIET or GRUB_TIMEOUT that shows anything or responds to keypresses is to set GRUB_TIMEOUT to a few seconds then I get the grub menu, but anything hidden doesn't seem to be working.

PS. I am using *upate-grub* after any changes I make to */etc/default/grub*.

**([COLOR="Red"]edit[/COLOR])** PPS. The version of *grub2-common* I have installed is Version: 1.99-21ubuntu3.1

---

### Post by ajgreeny on 2012-06-29
It has not been Esc you press for the menu since grub2 arrived, but Shift, so try that.

However, in the section:-[FONT=monospace]
[/FONT]```
GRUB_DEFAULT=saved 
GRUB_SAVEDEFAULT=true 
GRUB_HIDDEN_TIMEOUT=1 
#GRUB_HIDDEN_TIMEOUT_QUIET=true 
#GRUB_HIDDEN_TIMEOUT_QUIET=false 
#GRUB_TIMEOUT=10 
GRUB_TIMEOUT=0
``` your problem is the final line where you have it set to not show the menu, but to boot straight to the default OS.

On my system the similar section looks like:-
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
``` and if I want to see the menu I just use a cursor key quickly in the theoretical 1 second set, though as soon as the machine gets past the POST to move to grub, a few taps on a cursor key will show me the menu without a problem.

You need to change that GRUB_TIMEOUT=0 to a positive but low figure, and you should be good to go.

---

### Post by mikeym on 2012-06-29
**ajgreeny** that's weird, you're right. 

The menu is refusing to appear when GRUB_TIMEOUT is 0. Which is weird because [the grub2 manual](http://www.gnu.org/software/grub/manual/grub.html#Simple-configuration) explicitly says:

[quote="Grub 2 Manual"]&#8216;GRUB_HIDDEN_TIMEOUT&#8217;
Wait this many seconds for a key to be pressed before displaying the menu. If no key is pressed during that time, display the menu for the number of seconds specified in GRUB_TIMEOUT before booting the default entry. **We expect that most people who use GRUB_HIDDEN_TIMEOUT will want to have GRUB_TIMEOUT set to &#8216;0&#8217; so that the menu is not displayed at all unless a key is pressed.** Unset by default. [/quote]  

This is the behaviour I see on my Fedora desktop. 

Also I think it's *holding* shift that works, but pressing escape works during the hidden menu countdown.

I guess it's a bug since there appears to be no way to hide the menu from the user until a key is pressed.

---

### Post by mikeym on 2012-06-29
I've created a bug [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1019313](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1019313)

---

### Post by tguthrie on 2012-08-21
I found this post helpful for setting the grub menu settings:

[http://superuser.com/questions/181064/activate-grub-to-show-up-at-start-up](http://superuser.com/questions/181064/activate-grub-to-show-up-at-start-up)

---


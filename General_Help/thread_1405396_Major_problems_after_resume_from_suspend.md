---
title: "Major problems after resume from suspend"
date: 2010-02-12
forum: General Help
---

### Post by 121Lazz on 2010-02-12
Hi there,

I am using Ubuntu NBR on an eeepc 1005ha with karmic.
Suspend/hibernate and resume worked fine for a while, but not anymore :-(

On resume, I couldn't log back in because the password verification would take forever with no result or return a timeout message.
I then disabled the screensaver and now I'm able to see the desktop and a few things like keyboard, mouse and sound still work.

However, if I try to do anything like pressing the startbutton, open up wicd-client(because ethernet is disconnected...) or start a new app everything starts freezing. Switching between windows, starting more apps, keyboard shortcuts stop working.

I noticed that while the keyboard itself still works, I can't type in the terminal.

If I manage to initiate a restart or shutdown the system goes to the box / console with a few messages but nothing happens after that.
ALT+print+R E S U B is the only way for me to restart besides pressing the powerbutton for a few secs(which makes my hdd "scream").


I am fairly new to Linux, so I don't know what information I could / should provide. I did some poking around in the systemlog and found this in pm-suspend:

/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
/etc/pm/sleep.d/00-eeepc-wifi resume suspend: 

Don't know if it means anything, but these are always the last lines before another suspend/resume process.
Previously the last line(without "success") used to be Pulseaudio, which I uninstalled and replaced by now.

Another thing I tried was using s2ram / s2disk as alternatives, but that didn't work either (i think the 1005ha is not on the whitelist).

I am happy to provide any additional information.
Also, any ideas are appreciated! :)

---

### Post by gordintoronto on 2010-02-12
I Googled:
suspend 1005ha

and found some interesting threads.  The number one suggestion seems to be to turn off the wireless before suspending, then turn it back on after resuming.  Also install eee-control from Synaptic.

---

### Post by 121Lazz on 2010-02-12
I already tried it with eee-acpi-utilities which has the same functions as eee-control(which didn't set the fsb correctly).
Unfortunately, that didn't make a difference.
Also, i executed this script before another unsuccessful attempt:

```

#!/bin/bash
# 
# eeepc wifi suspend/resume
# Unload the ath9k module on suspend, and reload it on resume
#

case "$1" in
  hibernate|suspend|sleep)
  rmmod ath9k
    ;;
  thaw|resume)
  modprobe ath9k
    ;;
  *) exit $NA
    ;;
esac

```
Was executing it beforehand the correct usage?
Thanks for your input!

---

### Post by gordintoronto on 2010-02-12
I'm sorry, I can't answer your question.  I don't have a netbook, I was just trying to get you moving in the right direction, which is Google.

Isn't there a key-combination to turn the wireless on and off?  I don't think unloading the module affects the hardware.

---

### Post by 121Lazz on 2010-02-13
Yes, in my case its fn + f2. Both the eeepc-acpi-utilities and the shortcut turn off wifi. A look at iwconfig confirms that.

This is the first problem that I can't seem to fix by using google :|

---

### Post by simcha on 2010-02-13
I too have related issues. I'm running Ubuntu NBR on a 1005HA eeepc. I have an external monitor hooked up, and everything works great on boot, but after resume from hibernate the screens are screwy: the quick launch menu is messed up, the mouse clicks don't correspond to the location of the cursor on the screen, and when windows open full screen their location and size is incorrect.

---

### Post by 121Lazz on 2010-02-20
*bump*
I realize my description is pretty vague, but I can't tell exactly which processes are locking up. 
So it would already help if you could tell me what information / logs I should provide.

---


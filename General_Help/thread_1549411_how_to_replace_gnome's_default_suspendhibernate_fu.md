---
title: "how to replace gnome's default suspend/hibernate functions?"
date: 2010-08-09
forum: General Help
---

### Post by blur xc on 2010-08-09
I foolishly upgraded my dell mini 10 to lucid and have been having a hell of a time getting it back into the same running condition it was under 9.10.  Apparently 10.04 has a newer xserver version that has issues with the poulsbo gma500 driver.  I've got almost everything fixed- all that is left to resume normal computer using is the suspend and hibernate functions.

Right now, resuming crashes the xserver- so in effect, it's like having it do a gdm restart, all open programs are closed and you are greeted with the login screen after some ctrl-alt-f key action, followed by a ctrl-alt-f8 (best case).  Other times it's unrecoverable and need to be hard shut down...

I've been doing a lot of Googling on this issue, and found [s2ram]("http://tr.opensuse.org/S2ram").  It's wonderful, as is s2disk (hibernate).  I think it suspends and resumes considerably faster than the standard Ubuntu functions.  My only question is how do I get gnome to invoke these commands in place of its default suspend/hibernate functions- esp. while closing the net-book lid.

I read in a few places to edit the /usr/lib/hal/scripts/linxu/hal-system-power-suspend files, but the /usr/lib/hal/scripts directory does not exist on my system (dunno why), let alone any subdirectories of it.  I created those folders and files, but it didn't fix anything (no surprise).

thanks,
BM

---

### Post by kerry_s on 2010-08-09
hal was replaced with dbus.

it's suppose to use it automatically when installed.

anyways in /etc/acpi are the scripts. rename them & put your own scripts.

example:

sudo mv /etc/acpi/sleep.sh /etc/acpi/sleep.sh-remove

gksudo gedit /etc/acpi/sleep.sh

put:
#!/bin/bash
s2ram -f

make it executable:
chmod +x /etc/acpi/sleep.sh

do the same for hibernate.sh

---

### Post by blur xc on 2010-08-10
> **kerry_s said:**
> hal was replaced with dbus.

it's suppose to use it automatically when installed.

anyways in /etc/acpi are the scripts. rename them & put your own scripts.

example:

sudo mv /etc/acpi/sleep.sh /etc/acpi/sleep.sh-remove

gksudo gedit /etc/acpi/sleep.sh

put:
#!/bin/bash
s2ram -f

make it executable:
chmod +x /etc/acpi/sleep.sh

do the same for hibernate.sh

That's fantastic- thanks!

When did they switch to dbus?  I've got a desktop pc running 10.04 (clean install) 64bit, and it has the hal script files but the netbook, 10,04, clean install, 32bit doesn't?  Seems weird.

I still don't know for sure what I'm going to do with this netbook.  I ran updates last night and the thing went all to hell again, I'm at a command prompt and I can't get a wifi connection (tired the various network commands, I figure is got something to do with the stupid broadcom chip)...  Either way- this is great to know.

thanks again,
BM

---

### Post by blur xc on 2010-08-13
It still doesn't work.  I made my scripts, and selecting suspend from the shutdown menu and closing the lid put it to sleep, but then it fails to wake up, or best case, logs me out and I'm back at the login screen.

I don't understand why it works if I manually enter the commands in the terminal, but it fails from within the script.  Something else must be going in.

Also, even after shutting down, while powering back up, right after the dell bios slash screen it shows the message "resume: libgcrypt version 1.4.4" at the top of the screen.  Don't know why- is it trying to resume instead of booting up clean?  It's quite confusing.

Thanks,
BM

---

### Post by blur xc on 2010-08-13
I marked this thread as solved- I found the solution here [http://ubuntuforums.org/showpost.php?p=9378826&postcount=52](http://ubuntuforums.org/showpost.php?p=9378826&postcount=52)

Hope this helps others with this same problem...


edit- one  exception, my pm-suspend and s2disk files are located in /usr/sbin, not /sbin.  So, you should verify the locations of your files before getting upset at this fix not working for you.

BM

---


---
title: "USB boot problem"
date: 2011-09-04
forum: General Help
---

### Post by Myglaren on 2011-09-04
I created a bootable USB stick with 11.04 on it.
This worked well on several laptops that were otherwise failing to boot Windows.

I have another laptop here with the same problem - boots then crashes or just loops.

I tried the USB stick and it loaded as usual but then asked for my password.  As I had never created one (just running the desktop version) I couldn't log in.

I wiped the USB stick and reinstalled 11.04 on it and in the meantime tried to boot from a CD.

It couldn't see 11.04 but did boot 10.04 with a few error messages, wouldn't start Firefox and was extremely slow trying to do anything else then said the Gnome manager had failed.
On closing it seems Firefox was running but no GUI.

I have booted into the clean install on the USB stick and it is still asking for a username and password.
Naturally tried the one on the computer used to create the USB but that is incorrect.

Any guesses on how to proceed from here as I am stumped.  Never been asked for a password on a non-installed version before.

Thanks in advance for any thoughts,
Steve.

---

### Post by dcstar on 2011-09-05
> **Myglaren said:**
> I created a bootable USB stick with 11.04 on it.
This worked well on several laptops that were otherwise failing to boot Windows.

I have another laptop here with the same problem - boots then crashes or just loops.

I tried the USB stick and it loaded as usual but then asked for my password.  As I had never created one (just running the desktop version) I couldn't log in.

I wiped the USB stick and reinstalled 11.04 on it and in the meantime tried to boot from a CD.

It couldn't see 11.04 but did boot 10.04 with a few error messages, wouldn't start Firefox and was extremely slow trying to do anything else then said the Gnome manager had failed.
On closing it seems Firefox was running but no GUI.

I have booted into the clean install on the USB stick and it is still asking for a username and password.
Naturally tried the one on the computer used to create the USB but that is incorrect.

Any guesses on how to proceed from here as I am stumped.  Never been asked for a password on a non-installed version before.

Thanks in advance for any thoughts,
Steve.

[LIST=1]
[*]The Live system username and password is usually "ubuntu" & "ubuntu"
[*]On some systems with existing Linux installs on the hard disk the Live USB/CD can incorrectly use the existing configuration on those drives which can interfere with things.
[/LIST]

---

### Post by Myglaren on 2011-09-10
Excellent, thanks for the reply.  As usual a very simple solution that completely scrambled my brains.
I am still a bit confused as to why it should demand a username and password on one computer but not another.  Presumably related to permissions set by the machine's owner.
Back to work on that machine now:)

---


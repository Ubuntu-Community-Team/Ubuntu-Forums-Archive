---
title: "Ubunutu 10.04 won't boot anymore (2nd time)"
date: 2010-11-17
forum: General Help
---

### Post by Night Owl Google on 2010-11-17
Hey everyone,

I have a repeated issue with a Ubuntu 10.04 system.  The system runs fine for a while (weeks) after a clean install.  Eventually, the system will no longer startup and drops into busybox instead.  This is the 2nd time this has happened to me on the same hardware (other PCs in the same network run just fine) which has me quite concerned.  Last time, I simply blew away the content of the drive and re-loaded from scratch, this time I'd like to take the time to figure out what is going on and maybe learn how to get myself out of this bind.

The drive seems to be fine (ran HDAT2 diags - came up fine).  I've run the Boot Info Script ([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)) and attached the output.

I'd consider myself a NOOB when it comes to troubleshooting these types of issues and kindly ask for your help and guidance on this.

---

### Post by Barriehie on 2010-11-17
See if you've got a file /etc/default/bootlogd and if so you can enable boot logging.  File should look like this:
```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
#BOOTLOGD_ENABLE=No
```

---

### Post by yuki-nagato on 2010-11-17
> **Night Owl Google said:**
> Hey everyone,

I have a repeated issue with a Ubuntu 10.04 system.  The system runs fine for a while (weeks) after a clean install.  Eventually, the system will no longer startup and drops into busybox instead.  This is the 2nd time this has happened to me on the same hardware (other PCs in the same network run just fine) which has me quite concerned.  Last time, I simply blew away the content of the drive and re-loaded from scratch, this time I'd like to take the time to figure out what is going on and maybe learn how to get myself out of this bind.

The drive seems to be fine (ran HDAT2 diags - came up fine).  I've run the Boot Info Script ([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)) and attached the output.

I'd consider myself a NOOB when it comes to troubleshooting these types of issues and kindly ask for your help and guidance on this.

so basically the system isn't listing your primary desktop environment or is it just defaulting to busybox?

what happens when you delete .metacity (warning! this resets gnome to its defaults!) or enter safe graphics mode through the recovery console at the kernel listing (hit esc after the bios screen goes away)

---

### Post by Night Owl Google on 2010-11-17
Thank you for your response.

Ok, the file was present but the parameter was set to "No"... I changed to "Yes", shutdown the live cd, started the system and it prompted me for a disk check which I accepted.  It subsequently completed the startup process and presented a functional desktop environment.

... prior to this, it never asked me to do the disk check.

I've attached the boot.log file.  At this point, it looks like I'm up-and-running and I wonder 
a) what I should do if (when?) it happens again (i.e. what forced the disk check - was it the fact that I wrote to the filesystem from the live cd?)
b) if there are any additional checks that I can / should perform to give the system a clean bill of health or maybe determine the root cause of this recurring issue

> **Barriehie said:**
> See if you've got a file /etc/default/bootlogd and if so you can enable boot logging.  File should look like this:
```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
#BOOTLOGD_ENABLE=No
```

---

### Post by Night Owl Google on 2010-11-17
the system stays in text mode and defaults to busybox.  Not sure if this adequately addresses your question (sorry).

At this point (see above), it appears that I'm up-and-running again so I can't recreate the error condition and provide more details.  I have a better idea on what else to try (i.e. your suggestion below) though.

> **yuki-nagato said:**
> so basically the system isn't listing your primary desktop environment or is it just defaulting to busybox?

what happens when you delete .metacity (warning! this resets gnome to its defaults!) or enter safe graphics mode through the recovery console at the kernel listing (hit esc after the bios screen goes away)

---


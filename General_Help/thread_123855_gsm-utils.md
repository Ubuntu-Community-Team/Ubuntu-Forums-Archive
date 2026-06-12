---
title: "gsm-utils"
date: 2006-01-31
forum: General Help
---

### Post by sect2k on 2006-01-31
Hi!

I'm having some trouble with gsm-utils.

I have a GSM terminal (Siemens MC35) connected to the serial port (/dev/ttyS0).

The default device for gsm-utils is /dev/mobilephone which does not exist on my computer.

I would like to set the default device to /dev/ttyS0, but nothing seems to work. I tried changeing both the /etc/defaults/gsm-utils file and also the startup script in /etc/init.d/gsm-utils directly.

Could someome with more experience with shell scripts give me some insight on the subject.

Thanks,
/me

---

### Post by sect2k on 2006-02-01
I have since been able to remedy the issue. The problem was broken gsm-utils init script.

More info:
[https://launchpad.net/distros/ubuntu/+source/gsmlib/+bug/30228]("http://https://launchpad.net/distros/ubuntu/+source/gsmlib/+bug/30228")

Thought I'd let you know, just in case some has the same problem! ;)

Cheers,
/me

---


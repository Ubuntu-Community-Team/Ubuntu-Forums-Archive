---
title: "udevd: SYSFS{} will be removed in a future version"
date: 2010-05-29
forum: General Help
---

### Post by BKossmann on 2010-05-29
Hello,

I've just upgraded from 8.04LTS to 10.04LTS and after the "Starting up..." message I see a whole bunch of error message lines that say something to the effect of "udevd : SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device". 

According to 

[INDENT][http://linuxindetails.wordpress.com/2009/12/30/udevd-sysfs-will-be-removed-in-a-future-udev-version-please-use-attr-to-match-the-event-device/](http://linuxindetails.wordpress.com/2009/12/30/udevd-sysfs-will-be-removed-in-a-future-udev-version-please-use-attr-to-match-the-event-device/) 
[/INDENT]

it says that I need to replace SYSFS with ATTR on line 10, but the problem is I get the error on a whole bunch of lines, not just 10.

Also, my file is at /etc/udev/rules.d/ not /lib as above.  Odd thing is, my cursor is negatively effected and KeyPassX does not resolve properly (is this related?).

To be honest, I don't know enough to know how to proceed.

Would one of you kind and knowledgeable souls please point me in the right direction?  

Thank you!

Regards,

Bill

---

### Post by Avionix on 2010-05-30
Hi Bill, I have exactly the same problem I have had nothing but dramas with udev since attempting to upgrade from 8.04 to 10.04. It says please use ATT= to match the event device or ATTRS{}to match a parent device in /etc/udrules.d/85-hplj10xx.rules:X Xbeing any one of 30 or so lines. If I page down I get a splash screen with a purple background  and the word ubuntu (this is after following another thread which had me download and install another kernel)I can't get a terminal or anything to deal with this.
If any one could help Bill and I with this I would be grateful.

---

### Post by BKossmann on 2010-05-30
Well, I think I fixed my problem (and hope I haven't screwed up anything else by doing so).

I typed out /var/log/boot.log and determined that there were two rules files that were causing the error messages: 50-xserver-xorg-input-wacom.rules and 85.brltty.rules.  I backed up the files and modified the 50... and 85... rules by replacing all SYSFS with ATTR.

I figured that since I don't have a Watcom tablet nor a Braille TTY I should be okay, so I rebooted and hey presto, no errors!

I still have an issue with screen corruption but I'll take that up in another thread.

By the way, if anyone thinks that I've only created more problems for myself, PLEASE let me know.

Thanks!

Bill

---

### Post by dino99 on 2010-05-30
no need to worry about these comments

---

### Post by Favux on 2010-05-30
Hi BKossmann,

I think you're good.  There was a change in syntax with:
> ATTRS - match a sysfs attribute of the device, or a sysfs attribute of any of the parent devices
rather than SYSFS just as you figured.  [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by Avionix on 2010-05-31
Hi anyone got any idea how I can get a terminal up to make the changes described above.

---

### Post by BKossmann on 2010-05-31
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Wonderful resource.

---

### Post by hhoyt on 2010-09-18
Well Done !!

/var/log/boot.log
took me right to the problem.

As I recall, it was /etc/udev/rules.d/01-mountmanager.rules
in my case.

Thanks, Howie

---


---
title: "Fonts/Tinkertoyish look"
date: 2006-01-27
forum: General Help
---

### Post by newbee on 2006-01-27
Is there a set of fonts, or some setting(s) to change in order to get rid of the "tinkertoyish" look?
Using the Mozilla browser with XP, the fonts look good, but with Ubuntu(default install using the downloadable X86 iso) the fonts look very "tinkertoyish", for lack of better words.
My only previous experience with any Linux is RHEL WS, and it was already set up for me, and I didn't have to do any configuring, so I am a little lost when it comes to this.  I'm liking Ubuntu, all in all, however....
Also, is there a way to minimize the "sudo's", as this becomes a drag after a while.

Thanks, and move this if not in correct forum.

---

### Post by kverde on 2006-01-27
Although this reduces security a bit, to reduce sudos, try this:

**[FONT=Courier New]sudo visudo -f /etc/sudoers[/FONT]**

then edit the document to make the "defaults" line look like this.

**[FONT=Courier New]Defaults        timestamp_timeout=600,!lecture,!tty_tickets,!fqdn[/FONT]**


Basically, this keeps it remembering from place to place as well as remembering for a longer time.

---

### Post by newbee on 2006-01-27
Bump. 
(Will be my only bump)

---

### Post by dcstar on 2006-01-28
[QUOTE=newbee]Is there a set of fonts, or some setting(s) to change in order to get rid of the "tinkertoyish" look?
Using the Mozilla browser with XP, the fonts look good, but with Ubuntu(default install using the downloadable X86 iso) the fonts look very "tinkertoyish", for lack of better words.
My only previous experience with any Linux is RHEL WS, and it was already set up for me, and I didn't have to do any configuring, so I am a little lost when it comes to this.  I'm liking Ubuntu, all in all, however....
Also, is there a way to minimize the "sudo's", as this becomes a drag after a while.

Thanks, and move this if not in correct forum.[/QUOTE]
As far as the fonts go, have a look here:

[http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)

As far as sudo goes, just enable your root account and use the "Root terminal" system tool to do stuff (do a forum search on the many posts on how to enable root).

---

### Post by escape on 2006-01-28
Try this for Firefox - it's font settings copied from a Windows machine. If I understand you correctly, I was annoyed at this same thing, and this fixed it well. You can do similar things for Thunderbird, and probably other apps. 

In Firefox go to Edit -> Prefs -> General -> Fonts & Colors, and try these settings:

Proportional - Serif - Size 16
Serif - Arial
Sans-serif - Times New Roman
Monospace - Courier-New - Size 13

---

### Post by vol_freak on 2006-03-05
[QUOTE=escape]Try this for Firefox - it's font settings copied from a Windows machine. If I understand you correctly, I was annoyed at this same thing, and this fixed it well. You can do similar things for Thunderbird, and probably other apps. 

In Firefox go to Edit -> Prefs -> General -> Fonts & Colors, and try these settings:

Proportional - Serif - Size 16
Serif - Arial
Sans-serif - Times New Roman
Monospace - Courier-New - Size 13[/QUOTE]

Just what I had been looking for. This looks much more natural than the settings I had. Thanks.

---


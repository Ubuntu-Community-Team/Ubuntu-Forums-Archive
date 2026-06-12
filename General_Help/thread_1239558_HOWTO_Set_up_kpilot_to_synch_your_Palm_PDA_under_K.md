---
title: "HOWTO: Set up kpilot to synch your Palm PDA under Kubuntu"
date: 2009-08-13
forum: General Help
---

### Post by helmut_hed on 2009-08-13
These directions are current as of Jaunty and cover synching contacts (addressbook) and calendar to Kontact (the KDE calendar/addressbook/todolist app):

1) install the "akonadi" and "kpilot" packages:
sudo apt-get install akonadi-kde kpilot

2) identify the kontact calendar and addressbook resources to akonadi:
System Settings -> Advanced -> Akonadi configuration
click the "std.vcf" and "std.ics" entries in turn, pointing them to the following files:

~/.kde/share/apps/kabc/std.vcf
~/.kde/share/apps/korganizer/std.ics

(the first is your addressbook in "vcard" format and the second is your calendar, as used by Kontact)

3) Tell kpilot to use the Akonadi collections by going to the kpilot config screen and selecting the "Contacts" and "Calendar" conduits in turn, clicking on the std.vcf or std.ics names, and clicking Apply.

4) Tell kpilot to sync via usb and not /dev/pilot by going to General Setup -> Device in the config window and putting "usb:" (four characters ending in a colon) into the "Pilot device" field.  This is correct for most people.

5) Put your device in its cradle (and/or plug it in) and press the hotsync button.

If you use these instructions and find problems (or not) please reply.  Would be interesting to know how many users are out there.

---

### Post by poet_imp on 2009-09-04
Ok, I am trying to make this work and am having little success. First a couple updates to your instructions (which are very much appreciated). 

1) apt-get install akonadi**-kde** kpilot
2) The address book came up by default in the akonadi configuration but I had to add the calendar. I added a "traditional" calendar. The default file name is the same as the one you mention. I called it "Calendar".

After those two updates I got it to install and it configured correctly. I was even able to watch it attempt to sync. I think my problem is that I have a LOT of calendar entries; going back to 2002, thousands of them. When I attempt to sync I tail -f the .xsessions-errors file and I see hundreds of thousands of lines saying that one string does not match another and the strings are the appointment names. I let it run for 50 minutes and it did eventually quit but the connection to the pilot timed out long before then.

Whatever algorithm is being used by the kpilot program, it is highly ineffecent. It may work if I had only a few appointments but I really do not want to delete my history to try it out.

---

### Post by poet_imp on 2009-09-04
Just found bug that describes the problem:

[https://bugs.kde.org/show_bug.cgi?id=182932](https://bugs.kde.org/show_bug.cgi?id=182932)

---

### Post by InesP on 2010-02-04
Hi!

you made my day! Your description worked from the beginning. :)

Inés

---

### Post by phaedral on 2010-02-09
I'm on 9.1 netbook remix, and I don't know how much that varies from kbuntu, but I know it's gnome based, not kde based. Any special "gotchas" I should look for before trying this solution? I'm running on an 8gb flash drive, and would prefer not to have both kde and gnome installed due to space concerns (need some empty for the occasional download...)

Thanks!

---


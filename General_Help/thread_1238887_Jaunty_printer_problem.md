---
title: "Jaunty printer problem"
date: 2009-08-12
forum: General Help
---

### Post by fire_beast on 2009-08-12
I tried to get a printer up and running on my mother's 9.04 pc.  it is a canon bjc-610, which is supposed to be supported.  the computer wouldn't auto detect it, so I attempted to set it up manually.  after it was set up, I'd send it print jobs, but it failed to print.  it would just sit there...are their any known problems with Jaunty and printing?  I just installed Jaunty on that PC today, and fully updated it...I'm running Jaunty on my home PC as well, so this has some bearing on myself as well as my mothers business.  any help would be so greatly appreciated.

Thanks!!

---

### Post by fluffman86 on 2009-08-12
Go to System > Administration > Printing, and delete your current printer.  Now click new.  Is it detected then?

If not, try adding it manually again, but this time provide the ppd file from [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-610](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-610)

---

### Post by fire_beast on 2009-08-12
how do I use the driver available there?  I've been to that site numerous times, and always seem to get lost...maybe its because I'm running on like 2 hours of sleep.

---

### Post by fire_beast on 2009-08-13
well, now it seems a bit more obvious...its amazing what a little bit of sleep can do!  Thanks!

---

### Post by fire_beast on 2009-08-13
Ok, now it just says processing...never does anything else..time to revert back to the LTS version?

reverted back, problem solved.  new HP printer/scanner used.

---


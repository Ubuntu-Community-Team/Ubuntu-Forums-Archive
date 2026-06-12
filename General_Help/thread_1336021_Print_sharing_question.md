---
title: "Print sharing question"
date: 2009-11-24
forum: General Help
---

### Post by axiom7 on 2009-11-24
Hi All,

I'm somewhat of a rookie and having a problem sharing a printer connected to my ubuntu desktop with my windows laptop.  This all worked perfectly for quite a while.  I recently shut down all my computers for a few days and when I powered 'em back up I could no longer print from the laptop.  I keep getting an "access denied" error.

I used wireshark to get a look at what was going on.  As far as I can see the laptop sends an NBNS request but never gets a reply.  I used tcpdump on ubuntu server to verify.  Odd thing is that each computer can see the other (i.e. on laptop I see CUPS traffic from ubuntu).

I'll stop here...I'm stuck.  Any help is much appreciated.

Thanks!

---

### Post by XubuRoxMySox on 2009-11-24
On your 'buntu 'puter, open a browser and navigate to [http://localhost:631/](http://localhost:631/)

This is a CUPS administration site - a graphical way to edit your CUPS file. Click on the **Administration** tab (username and password for your computer may be needed) and see if it recognizes your printer. There's a li'l box next to "Share this printer" that may be unchecked. Check it, save, and close. And let us know if it worked.

-Robin

---

### Post by axiom7 on 2009-11-24
Hi Robin,

Thanks for the reply.  The info on that page seems like the same information I see thru System->Administration->Printing->ServerSettings.  Either way these were set properly.

I kept searching the web for similar issues and came across this link [http://www.jonathanmoeller.com/screed/?p=224](http://www.jonathanmoeller.com/screed/?p=224).

Samba was already installed so I went directly to the section regarding editing the smb.conf file.  I didn't touch the "interfaces" or "bind interfaces only" parameters but I did change the "security", and "guest account" params and then restarted samba after saving the changes.

This seems to have worked.  What I can't figure out for the life of me is why this used to work and then stopped.  I made no changes to anything...I wouldn't know what to change even if I wanted to.

Well...lesson learned.  Thanks for the help.

---


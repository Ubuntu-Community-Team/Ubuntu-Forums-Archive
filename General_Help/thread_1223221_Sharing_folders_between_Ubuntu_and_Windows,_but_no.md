---
title: "Sharing folders between Ubuntu and Windows, but no password required?"
date: 2009-07-25
forum: General Help
---

### Post by artemenko on 2009-07-25
I have a 150 gig USB drive connected to a laptop on my network running Ubuntu Jaunty.

I would like the Ubuntu computer to act as a file server for other computers on the network.

The good news is I can see the 150 gig USB drive from another Windows laptop and browse the folders.

Should I be worried there is no password prompt?  I thought I set up a samba password for this on the Ubuntu Jaunty laptop, and I'd feel more comfortable if Windows prompted me for it, instead of just making if available.

How do I get the Windows laptop to prompt me for a password to access the Jaunty laptop which has the USB hard drive connected to it?

---

### Post by swerdna on 2009-07-26
If you shared it using the "sharing options" tool in Nautilus, you need to untick the box that says ok for "Guest Access".

If you made the share by putting a stanza in the samba config file (smb.conf) then you need to edit out the line "guest ok = yes".

Either way, you then must add users to the samba user database. See here for that: [Permission to Access Ubuntu Shares]("http://ubuntu.swerdna.org/ubulanprimer.html#access")

---

### Post by philcamlin on 2009-07-26
> **artemenko said:**
> I have a 150 gig USB drive connected to a laptop on my network running Ubuntu Jaunty.

I would like the Ubuntu computer to act as a file server for other computers on the network.

The good news is I can see the 150 gig USB drive from another Windows laptop and browse the folders.

Should I be worried there is no password prompt?  I thought I set up a samba password for this on the Ubuntu Jaunty laptop, and I'd feel more comfortable if Windows prompted me for it, instead of just making if available.

How do I get the Windows laptop to prompt me for a password to access the Jaunty laptop which has the USB hard drive connected to it?

mine doesnt ask me either :o

never had any issues though

---

### Post by artemenko on 2009-07-26
> If you shared it using the "sharing options" tool in Nautilus, you need to untick the box that says ok for "Guest Access".

That worked -- Thank you!

---


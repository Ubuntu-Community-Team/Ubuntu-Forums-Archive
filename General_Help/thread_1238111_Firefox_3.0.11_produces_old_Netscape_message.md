---
title: "Firefox 3.0.11 produces old Netscape message"
date: 2009-08-12
forum: General Help
---

### Post by desconocido on 2009-08-12
Security updates from Ubuntu often bump up my version of Firefox. It has been at 3.0.11 for a few moths now. This version suddenly has a new feature - it crashes once or twice a week.

On one occasion only, it crashed and I found the following collection of dialogue boxes on my screen (see picture).

This appears to be a Netscape Communicator Quality Feedback Agent from about 1998. Could this be a virus or is it a feature of Firefox 3.0.11?

(I also have Google SketchUp installed under Wine, which may use Netscape, but I don't understand why a Firefox crash would provoke that.)

(I also have AdBlock Plus and FlashBolock installed.)

By the way, any info on why Firefox has started crashing?



Sorry about the typos, but I thought they were amusing so left them in.

---

### Post by jmszr on 2009-08-12
desconocido,

Looks like leftovers from the Netscape code from back in the day, This link gives a timeline for Netscape > Firefox: [http://www.linuxjournal.com/article/10150](http://www.linuxjournal.com/article/10150) .

Don't know why you're crashing, but Firefox is up to 3.0.13 now (not to mention 3.5.2), so it might help to update.

---

### Post by 3rdalbum on 2009-08-12
Wow. I've never seen that before. It's certainly not a virus, but I'm astonished that the code is still inside Firefox considering that the Netscape browser is no more.

Are you sure you haven't run an old Unix version of Netscape and crashed it just to hoax us? :-P

---

### Post by bobince on 2009-08-12
I can't see how Firefox could have generated this; Firefox 3 [no longer uses]("http://en.wikipedia.org/wiki/Crash_reporter#Mozilla") the [Talkback]("http://support.mozilla.com/en-US/kb/Quality+Feedback+Agent"), and it hasn't looked like that with the Netscape branding since version nought point ancienthistory. Also the name &#8216;Netscape Communicator&#8217; would be off; Communicator was the integrated-suite predecessor of SeaMonkey.

(Did Ubuntu ever ship Firefox with Talkback on anyway?)

> any info on why Firefox has started crashing?No such behaviour here. Plugins?

---

### Post by desconocido on 2009-08-12
> **3rdalbum said:**
> Are you sure you haven't run an old Unix version of Netscape and crashed it just to hoax us? :-P

Promise. Could it be the browser bundled inside Wine/SketchUp that does the help pages?

---

### Post by bobince on 2009-08-13
> **desconocido said:**
> Could it be the browser bundled inside Wine/SketchUp that does the help pages?

I wasn't aware there was one; it always uses the system browser for me (though I'm using SketchUp under VirtualBox rather than WINE).

In any case the dialogue boxes don't look like Windows/WINE is rendering them. They're in ancient Motif-toolkit styling, with a non-default default-application icon... I have no idea where those resources could come from in a modern Linux environment.

---


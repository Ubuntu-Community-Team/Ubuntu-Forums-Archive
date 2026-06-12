---
title: "What's the point of bug-buddy if there's no sendmail?"
date: 2006-06-24
forum: General Help
---

### Post by jnoreiko on 2006-06-24
Bug-buddy is great, but it falls flat at the last step because sendmail isn't installed.

What's the point?

---

### Post by lamego on 2006-06-24
I would report it as a bug on [Launchpad]("https://launchpad.net/") .

---

### Post by jnoreiko on 2006-06-24
Looks like it already is:
[https://launchpad.net/distros/ubuntu/+source/bug-buddy/+bug/36780](https://launchpad.net/distros/ubuntu/+source/bug-buddy/+bug/36780)

you'd think they would have noticed sooner, it's been a problem for several versions.

---

### Post by H.E. Pennypacker on 2006-06-25
I had no problems with Bug Buddy using sendmail.  All you have to do is download "sendmail" from Synaptic (since it isn't installed by default), and at the last step of Bug Buddy, put in /usr/sbin/sendmail.  Do it exactly as I typed it: /usr/sbin/sendmail. 

It sends the report to [email]submit@bugs.gnome.org[/email].

---

### Post by stimpyaw on 2007-01-31
> **H.E. Pennypacker said:**
> I had no problems with Bug Buddy using sendmail.  All you have to do is download "sendmail" from Synaptic (since it isn't installed by default), and at the last step of Bug Buddy, put in /usr/sbin/sendmail.  Do it exactly as I typed it: /usr/sbin/sendmail. 

It sends the report to [EMAIL="submit@bugs.gnome.org"]submit@bugs.gnome.org[/EMAIL].
----------------------------------------------------------------------------------------------------
THANKS H.E. Pennypacker! Your suggestion worked and helped this newbee submit his frist bug.  Thats all the help file has to say.
I went to "https://launchpad.net/ubuntu/+source/bug-buddy/+bug/36780" and they said you have to update to U6.10.  All you have to do is install ***sendmail*** and then Bug Buddy will work. WOOHOO!!

U :guitar:!!! LOL

---


---
title: "Can't set alternative Mail Clients in Preferred Applications."
date: 2011-04-28
forum: General Help
---

### Post by zonky on 2011-04-28
I'm trying to set Desktop-Webmail to be the preferred Mail Client in Preferred Applications in Natty, but Evolution is the only selectable option.

Purging Desktop-Webmail didn't help, nor did trying other such apps like gnome-gmail.

Any ideas on how the list of Mail Clients can be set?

---

### Post by zonky on 2011-04-28
So, quick hutn around suggests that for gnome to register a preferred app, it is supposed to drop a xml file in

/usr/share/gnome-control-center/default-apps/

Which these packages are doing- so has preferred apps been changed to break this working?

---

### Post by zonky on 2011-04-28
Ho-hum - seems like this is some sort of problem indeed:

[https://bugzilla.novell.com/show_bug.cgi?id=684747](https://bugzilla.novell.com/show_bug.cgi?id=684747)

---

### Post by zonky on 2011-04-28
Here we go - here is the issue on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/708382](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/708382)

---

### Post by zonky on 2011-04-29
Here is how to fix.

>sudo nano /usr/share/applications/desktop-webmail.desktop

add as the last line:

MimeType=application/mbox;message/rfc822;x-scheme-handler/mailto

then run:
>sudo update-desktop-database

You should be able to select it as a preferred application now!

success....

---

### Post by zonky on 2011-04-29
It's actually better to use Gmail Gnome if you get it from this PPA:

[https://launchpad.net/~daves/+archive/daves](https://launchpad.net/~daves/+archive/daves)

You don't need to mess with the .desktop file in that case.

This also adds sendto functionality to Nautilus.

If you want to use it with google apps, you'll need to change something in gconf-editor see: [http://sourceforge.net/projects/gnome-gmail/forums/forum/1004940/topic/3606317](http://sourceforge.net/projects/gnome-gmail/forums/forum/1004940/topic/3606317) for instructions.

---


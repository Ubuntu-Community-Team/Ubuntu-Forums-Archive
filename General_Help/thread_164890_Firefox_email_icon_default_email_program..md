---
title: "Firefox email icon default email program."
date: 2006-04-23
forum: General Help
---

### Post by ajgreeny on 2006-04-23
I am trying to find a way to change the email program that starts when I click the email icon on the Firefox toolbar from Evolution to Thunderbird, which is what I always use for mail.  I've searched the Firefox website but not found anything so far, so thought I'd try here.
I've set my default email client as Thunderbird in kcontrol both as user and as root, but it hasn't worked as far as I can see, though I may need to restart KDE first before the changes are seen.  I'm just about to do that now, so I'll report back soon.

I've just restarted KDE and that didn't work so I'm a bit foxed, if you'll forgive the pun.  Anyone got an idea?

---

### Post by Ensnared on 2006-04-23
Funny... I was researching this to find an answer for you, and realised I don't even _have_ the email-button in Firefox anymore - it's not even available when I try customising the toolbar.
I came across a similar problem though the other way around - Thunderbird always opened links in Konqueror while I of course prefer Firefox. Turned out Thunderbird executes "x-www-browser" to open URL's, and a simple "update-alternatives --config x-www-browser" took care of that, but apparently there's no such thing for the email client.

My best guess would be that Evolution is set as the default mail-client in Gnome, and that Firefox uses that instead of the KDE setting to determine which program to open. If so, you just need to launch the Gnome control-panel app for helper programs - can't remember what it's called and I don't have Gnome installed, but it's probably called gnome-something-something (yea, that helps a lot, huh? :p) and set Thunderbird as your mail-client there as well.

No idea if that's the cause, but it's worth a shot I hope :)

---

### Post by ajgreeny on 2006-04-24
Wow, thanks Ensnared, that's done it for me!  It didn't occur to me that I might need to change gnome configuration, as I never use it these days, but keep it on the machine as I understand it can have some influence on updating the system.

Anyway it all works as I want now so thanks a bunch.

---


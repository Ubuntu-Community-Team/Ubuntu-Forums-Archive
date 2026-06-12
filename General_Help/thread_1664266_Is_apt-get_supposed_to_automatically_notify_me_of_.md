---
title: "Is apt-get supposed to automatically notify me of available updates?"
date: 2011-01-10
forum: General Help
---

### Post by ryankask on 2011-01-10
I recently switched from Xubuntu to Ubuntu.

In Xubuntu, every time I logged in apt-get would check for updates and notified me in the task bar.

Now that I've switched to Ubuntu, I no longer see the updates and it doesn't seem apt is checking. 

update-notifier is in my autostart applications.

Any tips?

Thanks,
Ryan

---

### Post by kerry_s on 2011-01-10
update-notifier, yes.
apt-get, no. apt-get is the command line program, not a notifier.

for 10.10 there haven't been updates, once a version has been released only security updates are provided. ubuntu is not a rolling release yet.

---

### Post by ryankask on 2011-01-10
Okay thanks. Yes, I meant update-notifier. What I mean is that in Xubuntu I normally had a little icon that appeared in the upper right task bar notifying me of N number of package updates. I use a lot of frequently updates PPA's so it would be convenient to know which have updates.

The icon would appear grey if a package manager was working, red if there were critical updates and orange if recommended updates were available.

How do I re-obtain this functionality? I've tried reinstalling update-notifier but it doesn't work.

Thanks,
Ryan

---

### Post by mike555 on 2011-01-10
If you want to use the old update manager behavior, open a terminal and paste this:

gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by kerry_s on 2011-01-10
in gnome it does not show till there are updates.

you can check the settings in synaptic. i have mine set to auto install.

---

### Post by ryankask on 2011-01-11
Thanks mike555! That's exactly what I wanted.

Why did the behavior change and am I supposed to be seeing anything in its place?

Thanks!

Ryan

---


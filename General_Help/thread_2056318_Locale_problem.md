---
title: "Locale problem"
date: 2012-09-11
forum: General Help
---

### Post by lesliek on 2012-09-11
I'm using 12.04 with Gnome Classic.

I wanted the clock on the right of my top panel to display time in the 24-hour format.

When I checked Date and Time under System Settings, it showed 24-hour, but that hadn't had any effect, since I still had an am-pm clock.

I found this ([http://www.bitsbythepound.com/use-a-24-hour-clock-in-ubuntu-352.html](http://www.bitsbythepound.com/use-a-24-hour-clock-in-ubuntu-352.html)) and followed it.

Now I had 24-hour time, but other changes too.

Then I discovered that I could set up a custom time format by using dconf-editor, so I did that too, changing the default to %T.

Then I went back to /etc/default/locale and deleted the entry I'd added, so that file again says only: LANG="en_US.UTF-8". However, when I run the locale command, I get the following results:

LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=en_DK.UTF-8
LC_TIME=en_DK.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=en_DK.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=en_DK.UTF-8
LC_NAME=en_DK.UTF-8
LC_ADDRESS=en_DK.UTF-8
LC_TELEPHONE=en_DK.UTF-8
LC_MEASUREMENT=en_DK.UTF-8
LC_IDENTIFICATION=en_DK.UTF-8
LC_ALL=

Deleting my earlier change to /etc/default/locale obviously hasn't reversed the effect of it.

What more can I do to eliminate all these en_DK entries?

---


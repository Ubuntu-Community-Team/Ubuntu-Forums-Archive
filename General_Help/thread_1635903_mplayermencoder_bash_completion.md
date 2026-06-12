---
title: "mplayer/mencoder bash completion"
date: 2010-12-02
forum: General Help
---

### Post by jdratlif on 2010-12-02
I wasn't sure where to post this. It's a bash-completion issue.

bash-completion for mplayer/mencoder assumes -cdrom-device and -dvd-device should only accept /dev/cdrom and /dev/dvd. But these can also accept ISO files and DVD_VIDEO folders.

I changed mine to use _filedir instead of _dvd_devices for the -dvd-device completion, but I'm not very familiar with it and am not sure if this is the proper change. Maybe there is something better. It should be restricted to ISOs, folders, and the /dev/[cd|dvd] devices.

I'm a recent kubuntu convert, and I would like to send this note to whoever can fix this, but I'm not sure who that is. Do I file a bug report on launchpad?

Thanks.

---

### Post by sisco311 on 2010-12-03
Yes, you should file a bug report against bash-completion at launchpad.
[uhelp]community/ReportingBugs[/uhelp]

---


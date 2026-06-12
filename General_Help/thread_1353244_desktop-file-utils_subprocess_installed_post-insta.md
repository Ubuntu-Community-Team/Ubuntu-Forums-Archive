---
title: "desktop-file-utils: subprocess installed post-installation script"
date: 2009-12-12
forum: General Help
---

### Post by hilather on 2009-12-12
Hey Guys,

Looking for some help with this problem, as its driving me batty.  I have Karmic 64 bit 
Linux hilather-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

I recently tried installing the nouveau open source nvidia driver and everything went horribly wrong.  Parts of my gnome desktop were removed and gdm was also removed.  After I reinstalled the proprietary nvidia drivers and gdm I was left with all these post-installation script errors. While my desktop still works, everything I install packages I get these errors and as you can imagine its incredibly annoying.

I'v tried removing all of them with apt-get purge, aptitude purge, reinstall installing with the -f option and I'm getting no love.

I've tried removing ubuntu-desktop, gdm, all of the below packages and it always comes back the same.  I've deleted the /var/cache/apt/pkgcache.bin file (blindly following instructions in other posts) and nothings worked.

I really don't want to have  to reinstall my desktop, any ideas why this is happening?


E: desktop-file-utils: subprocess installed post-installation script returned error exit status 127
E: nautilus: dependency problems - leaving unconfigured
E: gnome-control-center: dependency problems - leaving unconfigured
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-session: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: indicator-applet: dependency problems - leaving unconfigured
E: indicator-messages: dependency problems - leaving unconfigured
E: indicator-session: dependency problems - leaving unconfigured
E: indicator-applet-session: dependency problems - leaving unconfigured
E: nautilus-dropbox: dependency problems - leaving unconfigured
E: nautilus-share: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

---

### Post by hilather on 2009-12-12
So, I commented out the whole /var/lib/dpkg/info/desktop-file-utils.postinst file and  everything configures now. Running the update-desktop-database produces the g_option_context_new error. While I bet this is a symptom of another problem, since apt-get and synaptic have stopped harassing me, I could care less.  However is someone can explain how to fix this please do! I've seen so many other threads on Google where the only options given were to reinstall... 

Here is what the postinst file looks like now, plus the output of running that command.

```

#!/bin/sh
set -e

#update-desktop-database -q

#if [ "$1" = "triggered" ]; then
    exit 0
#fi
```

```
$ update-desktop-database -q
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_option_context_new
```

---


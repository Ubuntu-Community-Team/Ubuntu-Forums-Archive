---
title: "flash not working in swiftfox, but in firefox"
date: 2010-02-07
forum: General Help
---

### Post by gelse on 2010-02-07
Hello everyone.

It took my several hours yet, but i could not find a solution to my problem anywhere in the net, so you are my last hope.

Facts:
Installed Flash version: via flashplugin-installer
Installed Firefox version: current (3.5.7)
Installed Swiftfox version: current (3.6)

Anyway, it does not matter which Flash version i install, non of them works in Swiftfox - but all of them i got to work in Firefox.

Both Swiftfox and Firefox are using the same mozilla-profile.

What i see is that - for example - youtube has a black box where the flash video should be. Not even the controls show up.

I am lost here now and have no idea what i could change to get flash working in swiftfox.
By the way - when i open an swf file in swiftfox, it works. Just embedded in a webpage seems has a problem.

If you need any further information, tell me, i will post.

Thanks

---

### Post by lovinglinux on 2010-02-07
See Removing Conflicting plugins from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by gelse on 2010-02-07
Thanks.

I still dont get it, why the plugin was working in firefox all the time, but that thread did help.

Anyway, to imporve my knowledge, could you please tell me why swiftfox had troubles and firefox did not?

---

### Post by lovinglinux on 2010-02-07
> **gelse said:**
> Thanks.

I still dont get it, why the plugin was working in firefox all the time, but that thread did help.

Anyway, to imporve my knowledge, could you please tell me why swiftfox had troubles and firefox did not?

When you install flash it creates several symlinks inside the /usr/lib/ installation directories, so any application that need flash can find the plugin. When you installed Swiftfox it probably linked to the incorrect place where *libflashplayer.so* is stored or didn't link at all. Perhaps is because version 3.6 is now linking to /usr/lib/mozilla/plugins/libflashplayer.so instead of /usr/lib/xulrunner/plugins/libflashplayer.so. Anyway, usually reinstalling flash fixes those issues.

---


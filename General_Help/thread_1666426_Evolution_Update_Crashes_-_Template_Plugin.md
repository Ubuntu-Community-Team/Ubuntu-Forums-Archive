---
title: "Evolution Update Crashes - Template Plugin"
date: 2011-01-13
forum: General Help
---

### Post by drs305 on 2011-01-13
Today I opened Evolution after running Update Manager.  Either immediately after opening or clicking on the right message pane Evolution crashes. 

When starting from the terminal, errors include various camel * messages.

dpkg.log shows activity installing evolution 2.30.3-1ubuntu7.2.

Nothing on my system had changed other than today's updates, and I've been running Evolution over a year without issue.

Evolution will run without crashing by starting it with:
```
evolution  --disable-eplugin
```

After starting, disabling the "Templates" plugin via Edit, Plugins, will allow Evolution to run without crashing.

Bug report filed but closed due to apport failure... 
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/702675]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/702675")

---


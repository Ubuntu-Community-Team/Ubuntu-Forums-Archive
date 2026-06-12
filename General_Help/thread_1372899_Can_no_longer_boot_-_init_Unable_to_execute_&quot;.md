---
title: "Can no longer boot - init: Unable to execute &quot;/bin/sh&quot; for rcS: Not a directory"
date: 2010-01-05
forum: General Help
---

### Post by newlinux on 2010-01-05
Now when I boot I get a couple of lines (about 3 lines past the mounting root filesystem message) and I get a set of lines like:

init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS main process (2089) terminated with status 255
init: Unable to execute "bin/sh" for rc-default : Not a directory
init: re-default main process (2090) terminated with status 255

I've verified (via liveCD) /bin/sh is a link /bin/dash. Any ideas? I can't boot into older kernels either.

This is on 8.04 LTS...

Hoping I don't have to reinstall. This has been running stable for a while and I have a lot of configs on here...

Also, any idea what could have caused this?

---

### Post by newlinux on 2010-01-05
I'm thinking maybe I need to rebuild initramfs? anybody know how I do that from a liveCD?

---


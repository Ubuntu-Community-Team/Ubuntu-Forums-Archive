---
title: "Some applications not starting"
date: 2010-10-24
forum: General Help
---

### Post by nic-clark on 2010-10-24
Hi,

I have a strange problem with some applications in 10.10. This applies so far to virtualbox and skype. When I try to start them, nothing happens. Virtualbox just flickers the edge of the screen. Virtualbox has worked before, and i'm reluctant to delete it as I have another machine installed. Skype has never worked, and even when I have reinstalled, the same happens.

Anyone come across this before or have any suggestions?

Thanks,

Nic

---

### Post by amauk on 2010-10-24
Run them from the terminal, capture the output, and post here

Eg.```
VirtualBox 2>&1 > ~/Desktop/virtualbox.log
skype 2>&1 > ~/Desktop/skype.log
```

Hopefully, with the output, the reasons will be obvious

---

### Post by nic-clark on 2010-10-29
Hi,

Thanks, I ran the commands, and this is what came up. I don't think it worked properly as both the logfiles created on the desktop are empty. The skype command was not found.

VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: /usr/lib/libQtOpenGL.so.4: undefined symbol: _ZN14QWidgetPrivate15checkWindowRoleEv

Thanks,

Nic

---


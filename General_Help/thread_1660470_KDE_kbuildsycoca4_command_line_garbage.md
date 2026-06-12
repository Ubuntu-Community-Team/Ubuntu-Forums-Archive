---
title: "KDE kbuildsycoca4 command line garbage"
date: 2011-01-05
forum: General Help
---

### Post by arloth on 2011-01-05
Is there a way to stop kbuildsycoca4, and klauncher from spitting messages over all over my console windows every time I start a kde program from the console?  I absolutely hate it when I'm typing a command and suddenly I get a million messages from kbuildsyscoca/klauncher and can no longer see what I was typing.

I'm tired of seeing messages like this ```
kbuildsycoca4(24102) KMimeAssociations::parseAddedAssociations: "/home/arloth/.local/share/applications/mimeapps.list" specifies unknown service "mplayer.desktop" in "Added Associations"
```  which seem to have little significance in terms of an actual error message.

For examlpe redirecting kate stderr to /dev/null, you'll still get messages from klauncher, and kbuildsyscoca4. Is there a way to silence this garbage for good?

---

### Post by Zorael on 2011-01-06
Hmm, any and each of these may be enough. In order of neatness and effort needed;

A. Start **kdebugdialog** and tick Disable all debug output.

B. Open up that **~/.local/share/applications/mimeapps.list**, look for lines including **mplayer.desktop** and redact it or remove the entire section including it.

C. Start your programs with '**dolphin &>/dev/null**'. Or to fork and disown it; '**dolphin &>/dev/null & disown $!**'. Annoying workaround though.

---

### Post by arloth on 2011-01-06
hmm, i'll try the kdebugdialog fix first.  I'll see how it goes tomorrow.

Also, fix B isn't really an option, as there are tens of errors like that one.

---

### Post by edwinclout on 2011-10-17
> **Zorael said:**
> Hmm, any and each of these may be enough. In order of neatness and effort needed;

A. Start **kdebugdialog** and tick Diable all debug output.

B. Open up that **~/.local/share/applications/mimeapps.list**, look for lines including **mplayer.desktop** and redact it or remove the entire section including it.

C. Start your programs with '**dolphin &>/dev/null**'. Or to fork and disown it; '**dolphin &>/dev/null & disown $!**'. Annoying workaround though.

Excellent help info, Zorael.. Thanks.
The debug info has been bugging me, too!

---


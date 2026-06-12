---
title: "Making ubuntu easier to use for someone"
date: 2009-12-21
forum: General Help
---

### Post by mediate on 2009-12-21
Hello.
I am planning on installing Ubuntu for someone. However, this person does not understand computers at all. So, I need to make it easier to use than normal. I'm using and installing ubuntu 9.10 Desktop. I need the OS to:

[LIST]
[*]Automatically log in (since i'm using the desktop CD, there is an option to do this through the install)
[*]Automatically mount a FAT32 hard disk from boot (the disk contains music, videos, and photos).
[*]Automatically install all updates.
[*]Use a webcam to communicate with family through Yahoo Messenger.
[/LIST]
As well, it will be installed on a computer with a SiS onboard video card. It uses SiS UVGA3_390 and AGP121 drivers for windows. Are there any Linux drivers for it? Are there any open-source drivers that support this video card?

Thanks for the help.

mediate

---

### Post by zaffe93 on 2009-12-21
windows...

---

### Post by Chesamo on 2009-12-21
> **mediate said:**
> [list][*]Automatically log in (since i'm using the desktop CD, there is an option to do this through the install)[/list]
You've got that under control.
> **mediate said:**
> [list][*]Automatically mount a FAT32 hard disk from boot (the disk contains music, videos, and photos).[/list]
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
> **mediate said:**
> [list][*]Automatically install all updates.[/list]
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)
> **mediate said:**
> [list][*]Use a webcam to communicate with family through Yahoo Messenger.[/list]
This one's tricky - make sure your webcam is supported.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Also, Empathy IM supports the Yahoo! IM protocol, but not video over IM. Neither does Pidgin.

---


---
title: "Live USB Natty problem"
date: 2011-07-19
forum: General Help
---

### Post by nikaberidze on 2011-07-19
I have created a live USB Natty Narwhale and tried it on several computers. After a while, it won't start, but shows the start-up screen with dots. I waited for half an hour without any change. This is the second time it happens, and on a different computer. These are probably P3 processors, I can find more specific hardware specifications if necessary. But it is so surprising that a live linux distro actually does not boot, that I want to check whether this is a known issue. I have used Knoppix live CD for a number of years and have never had any such problem. Could it be connected to the "persistent" file system on the USB?

Regards,

Nika

---

### Post by nikaberidze on 2011-07-19
Just a thought: I have connected this USB to a machine running Windows, and the anti-virus program has found infected files on it, and "quaranteened" them. Is it possible that an anti-virus program identifies some of Ubuntu's files as viruses?

Nika

---

### Post by 2F4U on 2011-07-19
It may be the case that the antivirus program thinks that there is a virus. However, it is unlikely that there really is a virus since there are not many known viruses for Linux in the wild. Did you do the virus scan before or after your problems started? The antivirus software may have damaged the software on the usb stick.

---

### Post by nikaberidze on 2011-07-20
I "did" the virus scan multiple times both before and after my problems started, as I am using computers at various internet cafes which have anti-virus software that automatically scan and "repair" files when I insert a USB stick. I have tried to stop them from doing this whenever possible. 

Now I made a new fresh live USB, and it works. If there is any interest in this issue, I might proceed more methodically and deliberately let the anti-virus software repair the files it thinks are infections, if this is useful to the Ubuntu community.

---


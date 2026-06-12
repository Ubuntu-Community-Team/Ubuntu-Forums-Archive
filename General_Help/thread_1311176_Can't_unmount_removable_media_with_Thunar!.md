---
title: "Can't unmount removable media with Thunar!"
date: 2009-11-02
forum: General Help
---

### Post by EGA on 2009-11-02
Hey all,

after reading the tutorial at [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager) i replaced Nautilus file manager with Thunar. If i try to unmount removable devices (USB flash drive, MP3 player, etc.) via a right click on Thunar's sidebar i get the following error message:

```
Cannot open /media/.hal-mtab.
```

A screenshot is attached below. As i'm using Karmic Koala atm i guess that the switch from HAL to udev and DeviceKit is the reason behing this issue.

The file itself (/media/.hal-mtab) doesn't exist, but there is a file called /media/.hal-mtab-lock.

Do you know a way to solve this problem? Thank you for your efforts!

---

### Post by EGA on 2009-11-04
...btw, it's no problem to unmount removable media with Nautilus!

---

### Post by EGA on 2009-11-07
Nobody out there who knows how to solve this error?

---

### Post by Stolea on 2009-11-07
So why do you want to use Thunar if it is giving you problems??? Just use Nautilus as you did before. The odds are that it is a bug that became a problem with Karmic. I have found a few programs that worked just fine under 9.04 but either don't work or have problems under 9.10
I am sure it will be sorted out, but that may be a while.

---

### Post by EGA on 2009-11-07
Weighing up pros and cons of both file managers i decided to use Thunar. I'm sticking at it 'cause it's much faster (especially on my netbook) than Nautilus. Well, i don't think that this is a normal bug which will be sorted out after a while. What i'm "searching for" is a confirmation that Thunar is making use of HAL instead of DeviceKit. In this case the problem won't be fixed until the developer of Thunar decides to shift to DeviceKit.

---

### Post by Stolea on 2009-11-08
I was under the impression that Thunar was an XBuntu application. Dunno if this of any help, but maybe worth a thought.

---

### Post by EGA on 2009-11-08
> **Stolea said:**
> I was under the impression that Thunar was an XBuntu application.

I know, it's the default file manager of XFCE (and thus a Xubuntu application). Maybe i should file a bug report on Launchpad.

---


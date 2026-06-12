---
title: "Dual Boot Access Windows &quot;C&quot; Drive From Ubuntu"
date: 2012-02-24
forum: General Help
---

### Post by kevsim on 2012-02-24
I have a dual boot system with Windows XP SP3 and Ubuntu 11.04 installed.
Form Ubuntu can I access Windows "C" drive, also if I install "Wine" in Ubuntu can I run windows programs installed on Windows "C" in Ubuntu using Wine?

From within Windows can I access the section of drive where Ubuntu is installed?

I would appreciate your advise.
kevsim

---

### Post by HeroOfCanton on 2012-02-24
Don't believe so. Windows is unaware that linux exists on any dual boot system I've run. If that's wrong someone will surely beat me down with knowledge shortly. :D

Do you need access to some files on the linux drive? You could setup a separate partition in NTFS or FAT that both windows and ububtu can read if that's the case.

---

### Post by yetiman64 on 2012-02-25
> **kevsim said:**
> .. also if I install "Wine" in Ubuntu can I run windows programs installed on Windows "C" in Ubuntu using Wine?

Wine is only a code compatibility layer in Linux for running *_some_* Windows executables that are installed to a hidden filesystem in your Ubuntu home folder. 

As far as I understand the workings of Wine it is not possible to run a Windows application installed on the Windows partition.

> **kevsim said:**
> From within Windows can I access the section of drive where Ubuntu is installed?... There used to be ext 2/3 filesystem drivers for Windows (read and write capable), last I heard there was an experimental driver that allowed ext 4 partition access (read only, **not** writable).

Rather than trying to access a non native filesystem under Windows, have you considered a shared partition for your data formatted to NTFS as both Windows and Ubuntu can read/write to NTFS. I don't recommend FAT because of its filesize limit (4 GB), it is a limitation of the filesytem itself.

Also a word of caution, writing to the Windows system partition from Ubuntu has been known to cause filesystem corruption in Windows, it is generally not recommended around here as a practice.

---

### Post by 3rdalbum on 2012-02-25
> **kevsim said:**
> I have a dual boot system with Windows XP SP3 and Ubuntu 11.04 installed.
Form Ubuntu can I access Windows "C" drive

Yes.

If you installed Ubuntu using Wubi, then your Windows drive will be in the /host/ folder inside "Filesystem".

If you installed Ubuntu the proper way by booting from the CD, then your Windows drive should be listed in the sidebar in the file manager. Or, I believe, even the Launcher on the left of the screen.

> also if I install "Wine" in Ubuntu can I run windows programs installed on Windows "C" in Ubuntu using Wine?

Not quite. Windows programs, even on Windows, depend on all their support files being within the running Windows installation, not on a different disk. In short, you need to install the program within Wine before you can use it.

Wine is not perfect, it will only run around 20% of Windows programs. Use it as a last resort for if you absolutely need a particular program.

> From within Windows can I access the section of drive where Ubuntu is installed?

Not easily enough, and I would be worried about the implications if your Windows ever got a piece of Ransomware.

---


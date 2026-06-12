---
title: "Trying to install Quake 2. Need help with path to install and tutorial."
date: 2009-12-17
forum: General Help
---

### Post by flak_monkey on 2009-12-17
[https://help.ubuntu.com/community/Games/Native/Quake2](https://help.ubuntu.com/community/Games/Native/Quake2)

I'm looking at the above link. It says <path to install> I'm very new to linux and I don't know what that would be, since I'm really unfamiliar with the way the files are set up in this OS. This doesn't seem to make sense with the way I'm used to operating a machine, where there are drive letters and the path would be (ex. C:\Program Files\Quake 2) Are there drive letters? Can somebody break this tutorial down to be even simpler than it already is? Total effing noob.

---

### Post by Canha on 2009-12-17
No offence, waste a couple bucks on Windows 7 and have fun with games mate, Not saying it's not possible, you will just find playing games on Linux inconvenient and annoying.

---

### Post by Darael on 2009-12-17
> **Canha said:**
> No offence, waste a couple bucks on Windows 7 and have fun with games mate, Not saying it's not possible, you will just find playing games on Linux inconvenient and annoying.

With respect, I strongly disagree. What is annoying is trying to run **New Windows-only** games. Native games (and the link is to a native setup procedure) are little trouble at all, in my (quite extensive) experience.
Now then, the file system.

In Linux, there is only one file system from the user's point of view. The equivalent of C: is /, the bottom of the filesystem. Your user files are in /home/<username> - this should give an idea of how it works. In Ubuntu, external drives are all "mounted" in folders under /media - usually named after their label. CD's and DVD's are also under /media/cdrom. Anyway, drive letters are replaced by special cases of folders called mountpoints. That means that you can (for example) have a memory stick always appear as a subfolder of your documents folder.

Anyway, your home folder, the only one your user can write to, is /home/<user>, but is also called "~". If you're installing the game just for you, you probably want to install it as a subfolder of ~/ - but I'll read the link and get back to you.

EDIT: Yes, for a one-user install, just make a folder in your home folder called (for example) user-apps, and replace <path to install> with "/home/<user>/user-apps" in the instructions.

FURTHER EDIT (!): For a much better explanation of the Unix filesystem layout that I gave, look at this:
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows#Where To Put Your Files](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows#Where To Put Your Files)

---

### Post by flak_monkey on 2009-12-19
Thanks fellows. This seems to be working well. Apart from running cs4 i'm disinclined to go back to windows and I'm thinking that this is going to work nicely for me once I get the hang of it.

---


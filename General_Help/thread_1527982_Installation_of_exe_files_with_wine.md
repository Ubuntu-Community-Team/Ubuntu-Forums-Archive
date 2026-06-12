---
title: "Installation of exe files with wine"
date: 2010-07-10
forum: General Help
---

### Post by Ctulhu on 2010-07-10
I downloaded the new Notepad++ version 5.7 from the regular Sourceforge website and wanted to install it with Wine (Wine 1.2). So far, I always just doubleclicked on it and ran a normal Windows installation process directly in Ubuntu (10.4). however, now I get this crap:

The file '/home/XYZ/Desktop/npp.5.7.Installer.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

which links to <https://wiki.ubuntu.com/Security/ExecutableBit>.

So, how do I install this now, any ideas/hints? Any help would be much appreciated ...

---

### Post by jbrown96 on 2010-07-10
Why, on earth, are you trying to install Notepad++ on Linux?

The entire purpose for Notepad++ is to bring a decent text editor to Windows. Linux has tons of excellent text editors. If you like GUI editors, then there is gedit and kate. For command line utilities, there is emacs, vi, and nano. 

Emacs is my favorite and has a command line and GUI version.

---

### Post by Theda54 on 2010-07-10
Notepad++ is a pretty good editor. Some people might just prefer that to vi or emacs. Of course, Linux has a ton of great editors, but it's all preference...

Anyways, I'm not exactly sure, but try using the "ls -l" command (no quotes. The command simply lists everything in the current directory.) in the directory where the executable is, and see if you have the permissions to run it. It might look something like -rwxrw-r--. The 4th space should be an x if your user has permission to run the file. If you don't have permissions to run it, try "chmod u+x putfilehere" to give permissions.

Sorry if this doesn't help.

---

### Post by mc4man on 2010-07-10
Just right click on the .exe -> properties -> Permissions and mark (ck. the box) the file as executable.

(The cause of this is that ill-advised security policy

---

### Post by Ctulhu on 2010-07-10
Thanks so much, the right-click permissions thing did it. (BTW: I am installing Notepad++ because I teach courses on my Ubuntu computers to people who use Windows.)

---


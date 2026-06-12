---
title: "Problems Opening .zip Files in KDE"
date: 2011-09-22
forum: General Help
---

### Post by Valkyr333 on 2011-09-22
Hi, everyone...

I'm having trouble opening .zip files in KDE. My phone plan makes me download all the pictures I take as .zip files, and this used to work fine with Dolphin. For some reason, as of this morning, opening .zip files with Dolphin opens up an empty folder (like it should be in the right place, but the files just aren't there) and for some reason the system wants to automatically open those files with Ark (which doesn't let me do jack with the photos even though I can see them) and telling it to open them with Dolphin instead suddenly turned into opening *two* blank windows with no files displayed in them. The only changes I've made to the system recently were to set up a bunch of multimedia stuff so I could play and rip my DVD's and CD's. I used this [comprehensive how-to]("http://ubuntuforums.org/showthread.php?t=766683") following the instructions that pertain to Ubuntu/Kubuntu 10.04.

Does anybody have any ideas what might have happened here?

---

### Post by ankspo71 on 2011-09-25
Hi,
I'm not sure what could have happened but check to see if you still have the packages called 'zip' and 'unzip' installed. These are the packages that ARK (the archive manager in KDE) uses to compress and extract zip archives.

Now try testing and extracting the zip files with unzip in your terminal. If using unzip in the terminal works, then there must be something wrong with ARK itself.

Change to the zip archive's directory:
```
cd /path/to/folder
```

Test the zip file:
```
unzip -t myfile.zip
```

Extract the zip file:
```
unzip myfile.zip
```

Unzip as a requirement of ARK:
[http://docs.kde.org/development/en/kdeutils/ark/requirements.html](http://docs.kde.org/development/en/kdeutils/ark/requirements.html)

How to use unzip:
[http://linux.about.com/od/commands/l/blcmdl1_unzip.htm](http://linux.about.com/od/commands/l/blcmdl1_unzip.htm)
[http://linux.about.com/od/commands/a/blcmdl1_unzipx.htm](http://linux.about.com/od/commands/a/blcmdl1_unzipx.htm)

Hope this helps.

---

### Post by Valkyr333 on 2011-09-27
It's strange. I've been gone for the weekend and when I got back, this problem had gone away. Should I just mark this thread as "Solved," or leave it open for others who might have the same problem? o.o

---

### Post by searchfgold6789 on 2011-09-27
Mark it as solved, because people who are having the same problem as you can always start a new thread which will be more effective than adding to this one.

---


---
title: "problems with installing Live Messenger 2011"
date: 2010-11-10
forum: General Help
---

### Post by JBark1 on 2010-11-10
When opening the wlsetup-web.exe file I received this error: 

Archive:  /home/NAME/Downloads/wlsetup-web.exe
[/home/NAME/Downloads/wlsetup-web.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/NAME/Downloads/wlsetup-web.exe or
          /home/NAME/Downloads/wlsetup-web.exe.zip, and cannot find /home/NAME/Downloads/wlsetup-web.exe.ZIP, period.

What should I do now?

Thank you

---

### Post by TeoBigusGeekus on 2010-11-10
If it's an archive, i.e. a self extracting zip archive, archive manager can't find the rest of it, meaning it is a part of a larger archive.

If it's a windows executable, you can't run it in linux without wine.

---

### Post by TBABill on 2010-11-10
Any .exe will not run natively in Ubuntu (or any Linux distro). Those are Windows executables, as stated above, and you would need to either be running Windows in a virtual box or try to run the file via Wine, which is available to install via the repos. However, not all Windows software runs in Wine either so you'd have to verify compatibility as well.

---

### Post by Mark Phelps on 2010-11-10
Generally speaking, the newer "Live" stuff will not work well in Wine -- if at all.

See the page below for Windows Live Messenger from the WineHQ site:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=127]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=127")

As you can see, all the recent versions are rated Garbage.

---

### Post by Ancanus on 2010-11-10
If you plan on using WLM exclusively, make sure to check the Linux alternatives [emesene]("http://emesene.org/") and [aMSN]("http://www.amsn-project.net/").

---


---
title: "Wine looking for .zip file?"
date: 2010-09-19
forum: General Help
---

### Post by labtek on 2010-09-19
Hello to the group. I'm using Ubuntu 10.04 after using 8.04 quite happily for several years.

I'm presently trying to get Wine to run a small Windows app that ran with Wine in 8.04 and I get this message.   


End-of-central-directory signature not found.
Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive.  In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/30MINUTE/setup.exe or
/media/30MINUTE/setup.exe.zip, and cannot find /media/30MINUTE/setup.exe.ZIP, period.

I've installed Wine Windows Microsoft Windows Compatibility Layer Beta Release from Ubuntu Software Center.

Any thoughts for a fix?

Thanks in advance.

---

### Post by themusicalduck on 2010-09-19
Right click on the .exe file and go to Properties. Go to the Open With tab and make sure that Wine is selected.

---

### Post by Joe of loath on 2010-09-19
It's trying to open it in an archiver program, but can't, as, well, it's not an archive.

As the above post says, tell it to open with wine.

---

### Post by labtek on 2010-09-20
Thank you for the posts.

Your suggestion works. I had to change permissions in Properties as well before the program would open.

Thanks again.:)

---


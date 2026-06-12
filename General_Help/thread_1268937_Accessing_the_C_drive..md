---
title: "Accessing the C drive."
date: 2009-09-17
forum: General Help
---

### Post by MA5C on 2009-09-17
Hello, I have just installed Linux the first time, and I would like to know why can't I access the C drive, even though I can access D, even though it's the same HDD. Also, it seems that you can update Firefox either. Can anybody explain a little?

---

### Post by Redundant Username on 2009-09-17
Did you install Ubuntu  using Wubi or a normal install?
If you did a normal install, you probably need to install ntfs-3g.
Go to System->Administration->Synaptic Package Manager. Type in ntfs-3g
check the box, and click apply.
 3.5 isn't available for Ubuntu right now, it should be by next month.

---

### Post by sisco311 on 2009-09-17
Hi and welcome to the forums!

How did you try to access the partition?

Did you get any error message?

Did you shut down Windows properly (no hibernation or suspend)?

[Mount Windows]("http://psychocats.net/ubuntu/mountwindows")

@Redundant Username: the ntfs driver is installed by default.

---

### Post by MA5C on 2009-09-21
The D drive appears, but not the C drive. Which is bad since all my music rips goes there.


EDIT: It seems it was in /host all along. Sorry about that.

---


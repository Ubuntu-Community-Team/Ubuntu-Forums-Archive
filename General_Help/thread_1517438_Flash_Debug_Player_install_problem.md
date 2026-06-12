---
title: "Flash Debug Player install problem"
date: 2010-06-25
forum: General Help
---

### Post by shro0ms on 2010-06-25
I am trying to install flash debug player but the installer keeps telling me that i need to delete xpti.dat from firefox's components directory. I delete the file and then go to install it again, yet i keep getting the same message. I go back into the directory and see that xpti.dat has been recreated.

How do i keep this from happening?

Thanks

---

### Post by VH-BIL on 2010-06-25
Is firefox closed when you are trying to install this?

---

### Post by shro0ms on 2010-06-25
Yes firefox is closed.

I actually just tried installing it again, and i realized it only gets recreated when i open firefox up again. However, having made sure all instances of xpti.dat are removed and double checking with locate -e xpti.dat, i still get the message. It does say it was installed completely, so hopefully it did install.

I just wasn't sure if that message meant it didn't install correctly

---

### Post by VH-BIL on 2010-06-25
I have not used the debug player, but thinking about it a firefox file can only be auto created when firefox is running i guess.

---


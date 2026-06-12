---
title: "autostart launcher not starting"
date: 2010-07-09
forum: General Help
---

### Post by sonic6567 on 2010-07-09
Hello,

ubuntu 9.10

I am working on a custom install preseed.  Part of the process is creating a file: /home/bholt/.config/autostart/starter.sh

That way on first boot, this will execute and continue my custom process.

But it does not start.  After boot if I go double click it it runs fine.

And one time it did auto start correctly.  But I don't know what I did to break it.

All i can think is I changed starter.sh to in turn start something else rather than just run itself.

Anyway, any experts on startup launchers out there?

thanks

ben

---

### Post by sonic6567 on 2010-07-09
Never mind.

I figured it out.

When I added the second script (which also runs as root) I forgot a comma in the sudoers file.
Oops.

All better now.

Thanks

---


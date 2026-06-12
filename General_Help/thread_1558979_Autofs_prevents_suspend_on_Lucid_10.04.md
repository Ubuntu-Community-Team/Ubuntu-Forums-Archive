---
title: "Autofs prevents suspend on Lucid 10.04"
date: 2010-08-23
forum: General Help
---

### Post by jfacemyer on 2010-08-23
I've searched through the forums and google, but can't find anything on this.

My laptop is one of the many which has had suspend difficulties after a recent update.  It was working fine before and after my upgrade to Lucid, and only within the last several weeks has there been a problem.

I've updated my kernel to the latest (.35) available from the kernel ppa for Lucid, to no avail.

I narrowed the problem down to autofs.  When it's running, it won't suspend (except every once in a great while), and when it isn't suspend/hibernate work perfectly fine each time I've tested.

I've tried using autofs with sshfs and nfs, same problem.

My pm-suspend log says nothing unusual - it looks as if it suspends fine, then just wakes up automatically.  And that's what it appears the thing is doing when I hit the suspend button/select suspend from the menu.

Any thoughts how to fix this?  Autofs is really critical on this laptop.

Thanks.

---

### Post by jfacemyer on 2010-08-24
Nobody?

---


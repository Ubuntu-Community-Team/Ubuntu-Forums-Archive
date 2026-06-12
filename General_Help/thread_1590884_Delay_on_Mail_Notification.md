---
title: "Delay on Mail Notification"
date: 2010-10-08
forum: General Help
---

### Post by beachblue on 2010-10-08
I use the Gnome Mail Notification Applet and have recently moved from a wired desktop machine to a wireless laptop.

The problem I have is that the Mail Notification shows an error because it tries to check mail immediately, the network hasn't finished connecting at this time though.

Is there a way to add a delay to this?  I can't see one.

Or if anyone can suggest an alternative that is just as good (or better) and allows for a delay?

---

### Post by Gillingham on 2010-10-08
Write a script to execute the mail notification program after a delay and add it to the start-up program.  I use one for conky it is:
```

#!/bin/sh
sleep 20
conky&
```

Replace conky by whatever command launches the mail notification.

David

---


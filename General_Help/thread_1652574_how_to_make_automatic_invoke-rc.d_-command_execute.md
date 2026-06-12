---
title: "how to make automatic invoke-rc.d -command execute when returning from power save"
date: 2010-12-25
forum: General Help
---

### Post by Janiporo on 2010-12-25
When I come back from power save-mode (the one that uses power, but very minimum) I have to run command:
```
sudo invoke-rc.d tvheadend restart
```
Othervice I can not get tvheadend to run correctly. Tvheadend is running, but does not work okay. :neutral:

Question is, how do I make that command run automatically? :roll:

---

### Post by Janiporo on 2010-12-27
After 2 days of googling, I found the answer:


PM-utils must be installed

/etc/pm/sleep.d/ is a directory where ALL .sh -ending scripts will be executed at wake event (return from powersave)

This scripts name is going to be wakeup.sh (can be anything .sh)


To make the file:
```
sudo touch /etc/pm/sleep.d/wakeup.sh
```

To make it executable run:
```
sudo chmod +x /etc/pm/sleep.d/wakeup.sh
```

No edit the file (with Gedit)
```
sudo gedit /etc/pm/sleep.d/wakeup.sh
```

(Blank page opens)

and add next (use copypaste, ofc):

```
#!/bin/bash
case "$1" in
    thaw|resume)
        invoke-rc.d tvheadend restart
        ;;
    *)
        ;;
esac
exit $?
```


Save, and youre all done.

Now test it.

---

### Post by dcstar on 2010-12-28
> **Janiporo said:**
> After 2 days of googling, I found the answer:
.........

Then mark the thread.

---


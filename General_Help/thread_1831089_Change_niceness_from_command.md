---
title: "Change niceness from command"
date: 2011-08-22
forum: General Help
---

### Post by magicalplug on 2011-08-22
Hi.

I'd like to change an application's niceness from the command line but by process name rather than PID.

I can already do this:

sudo renice -10 9461

To change niceness by PID, but this isn't a static value. How do I go about replacing the 9461 with an Application-Name so the same command always works to change the niceness?

Thank you for any help :)

---

### Post by dave01945 on 2011-08-22
just use 

```
sudo renice -10 $(pidof *processname*)
```

---

### Post by magicalplug on 2011-08-23
That's fantastic. Cheers Dave :)

I had to convert it into this to get it to work in a Unity quicklist.

gnome-terminal -x bash -c "sudo renice -10 $(pidof process-name)"

Not sure why I can't gksudo it directly from the quicklist, but this method works just as well.

Thanks again for your help.

---


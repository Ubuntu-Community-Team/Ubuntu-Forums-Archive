---
title: "Sudo shutdown vs Power Button"
date: 2012-01-04
forum: General Help
---

### Post by Thoralyon on 2012-01-04
What's the difference between the sudo shutdown command and simply turning the system off via power button or clicking the appropriate menu item?

My problem is this: I want to turn my computer off on a timer, I use ```
 sudo shutdown -P -t 30 60 
``` for a shutdown in 60 minutes with a 30 sec wait before it kills everything

But this option still kills some programs, causing them to improperly save their status. The power off button never does this.

So my question is this:
How do I properly shut down my computer on a timer so that everything behaves the same way it would if I press the Power off button

---

### Post by Lars Noodén on 2012-01-04
I looked the manual page for [shutdown](http://manpages.ubuntu.com/manpages/oneiric/en/man8/shutdown.8.html) and could not find the option **-t**.  So I looked at the source code (it's part of the Upstart package) for [font=Courier New]shutdown[/font] and **-b** is there, but does nothing.

```

...
        /* Compatibility options, all ignored */
...
        { 't', NULL, NULL, NULL, "SECS", NULL, NULL },
...

```

So if you are relying on it, it does not do what you need it to do.  There might be some other way of sending a signal to your programs but that is not it.

---

### Post by Thoralyon on 2012-01-04
[http://manpages.ubuntu.com/manpages/dapper/man8/shutdown.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/shutdown.8.html)

need to have a closer look at this, it didn't occur to me that it's functionality could have been changed :-/

---

### Post by Lars Noodén on 2012-01-04
Maybe you could subsitute [pkill](http://manpages.ubuntu.com/manpages/oneiric/en/man1/pkill.1.html) to send a signal to all the processes owned by you.

---


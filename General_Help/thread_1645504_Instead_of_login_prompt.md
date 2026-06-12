---
title: "Instead of login prompt?"
date: 2010-12-14
forum: General Help
---

### Post by Yamanipanuchi on 2010-12-14
I wanted to see if anyone knows an easy way for Ubuntu 10.10 server to display a command ex "tail -f /var/log/message" instead of the login prompt?

Making a little memory stick the just runs a bunch of commands, and I just want to see the output.

Any help would be greatly appreciated.

---

### Post by dcstar on 2010-12-15
> **Yamanipanuchi said:**
> I wanted to see if anyone knows an easy way for Ubuntu 10.10 server to display a command ex "tail -f /var/log/message" instead of the login prompt?

Making a little memory stick the just runs a bunch of commands, and I just want to see the output.

Any help would be greatly appreciated.

```
sudo tail -f /var/log/message > /dev/tty2
```

---

### Post by Yamanipanuchi on 2010-12-15
Makes sense. I guess I need to go a step further and ask where would I place this command so that it would execute this at start up. I want this to come up instead of the Ubuntu login screen.

Yes I can login and manually type this in each time I start the system up. I kind of wanted the system to do this automatically for me.

---

### Post by Yamanipanuchi on 2010-12-17
Took a few days, but putting everything I found on different sites together I determined how to do this.

Edit /etc/init/tty1.conf

Added lines

exec /bin/login -f [USERNAME] < /dev/tty1 > /dev/tty1 2>&1
exec /usr/bin -f -n 10 /var/log/message > /dev/tty1

First line automatically logs in as whatever username you put in place of [USERNAME]
Second line run tail to follow /var/log/message

I also added the following two lines to /etc/rc.local to shut off screen blanking.

setterm -blank 0
setterm -store

Either way, Just putting it out there if anyone else looks into doing this.

---


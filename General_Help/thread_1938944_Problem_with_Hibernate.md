---
title: "Problem with Hibernate"
date: 2012-03-10
forum: General Help
---

### Post by McMuffin1892 on 2012-03-10
When attempting to hibernate my HP Pavilion dv7 laptop (it has Ubuntu 11.04 amd64 installed on it), most of the time it doesn't hibernate--while it is powering down, it stops abruptly and displays the error message "Can't reactivate AUX port". The only thing I can do is turn it off manually by removing the battery. When I start it up again, I usually have to turn it on, and force it off again twice before it will actually boot up, but when it does, my desktop environment returns, as if it did hibernate succesfully.

This issue is new--it started a few days ago after it hibernated fine since I first installed Ubuntu on it several months ago.

---

### Post by matt_symes on 2012-03-10
Hi

Hibernate and reboot your laptop to ensure there is something in the logs.

After that can you post the output of (from a terminal)

```
grep -i aux /var/log/syslog | tail -n50
```

```
grep -i pm: /var/log/syslog | tail -n80
```

```
grep -i i8042 /var/log/syslog | tail -n50
```

```
tail -n50 /var/log/pm-suspend.log
```

That may give us a starting place to look at this.

Kind regards

---


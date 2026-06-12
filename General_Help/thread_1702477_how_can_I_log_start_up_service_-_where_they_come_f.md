---
title: "how can I log start up service - where they come from"
date: 2011-03-07
forum: General Help
---

### Post by highspider on 2011-03-07
why im asking this question 
[http://ubuntuforums.org/showthread.php?t=1701098](http://ubuntuforums.org/showthread.php?t=1701098)

how can I log the start up service. 
   to figure out why cups always starts up.

this doesn't seem to help
```

cat /etc/default/bootlogd
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=yes

```NOTE Im not good with log viewer so I might just missing something.

---

### Post by gmargo on 2011-03-07
In 10.10 Maverick, the **upstart** system starts system daemons.  To disable **cups**, edit the **/etc/init/cups.conf** file and comment out these three lines for "start on":
```

start on (filesystem
          and (started dbus or runlevel [2345])
          and stopped udevtrigger)

```

---

### Post by wojox on 2011-03-07
Try this for services:

```
sudo apt-get update; sudo apt-get install sysv-rc-conf
```

Then 

```
sudo sysv-rc-conf
```

This will allow you to start and stop certain services at run time.

---

### Post by highspider on 2011-03-07
> **gmargo said:**
> In 10.10 Maverick, the **upstart** system starts system daemons.  To disable **cups**, edit the **/etc/init/cups.conf** file and comment out these three lines for "start on":
```

start on (filesystem
          and (started dbus or runlevel [2345])
          and stopped udevtrigger)

```


I LOVE YOU :)
 

Serious, it worked perfect and have no Idea how you figured that out or why it-upstart works that way.
 I was at this for a long while

now i have some upstart system reading todo.

---

### Post by highspider on 2011-03-07
> **wojox said:**
> Try this for services:

```
sudo apt-get update; sudo apt-get install sysv-rc-conf
```Then 

```
sudo sysv-rc-conf
```This will allow you to start and stop certain services at run time.

I have this didn't work for Maverick 10.10 check my link.  Thank you for helping thou :)

---


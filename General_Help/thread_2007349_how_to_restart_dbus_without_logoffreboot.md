---
title: "how to restart dbus without logoff/reboot?"
date: 2012-06-20
forum: General Help
---

### Post by orange_roughy on 2012-06-20
Hi,

DBus breaks on me all the time. It happens if my wifi connection temporarily goes down. When the connection comes back up, I cannot connect to any remote server in Nautilus (DBus error). It happens other times, too, but this is the most reproducable one.

How can I restart DBus without logging off or rebooting?

thanks,
orange_roughy

---

### Post by kanikilu on 2012-06-20
On newer versions of Ubuntu, I think ```
sudo service dbus restart
``` should work. On older versions I think it's ```
sudo /etc/init.d/dbus restart
```

---

### Post by orange_roughy on 2012-06-20
> **kanikilu said:**
> On newer versions of Ubuntu, I think ```
sudo service dbus restart
``` should work. On older versions I think it's ```
sudo /etc/init.d/dbus restart
```

Did you actually try your suggestion? I did. And it resulted in an empty desktop with no ability to do anything. I typed and clicked to no avail. My only option was ctrl+alt+backspace. I did that, and it resulted in a full-screen console with some messages. Then nothing. Full reboot required.

Thanks!

---

### Post by kanikilu on 2012-06-20
Sorry it didn't work for you, but yes, I did restart dbus (using my first suggestion), and the screen blinked and eventually came back. The only negative effect was that networking didn't restart automatically so I had to start that manually.

Sounds like something else is wrong on your setup, but what exactly it is, I'm not sure - I was just answering your question on how to restart the dbus daemon...

Good luck.

---

### Post by orange_roughy on 2012-06-20
OK, well thank you.

Is there perhaps a non-Nautilus/Dbus GUI for SCP/SSH?

---

### Post by orange_roughy on 2012-06-20
> **orange_roughy said:**
> OK, well thank you.

Is there perhaps a non-Nautilus/Dbus GUI for SCP/SSH?

nevermind. i found command-line SFTP... saved!

---

### Post by kanikilu on 2012-06-20
Not sure if the dbus problems will interfere, but have you tried Filezilla? It's in the software center, and is a great GUI sFTP client.

---


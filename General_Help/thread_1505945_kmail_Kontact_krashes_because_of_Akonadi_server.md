---
title: "kmail Kontact krashes because of Akonadi server?"
date: 2010-06-09
forum: General Help
---

### Post by Captain Giraffe on 2010-06-09
I kant write an email or do anything until akonadi server says its stopped and I should send a bug report. please?

---

### Post by tbohaning on 2010-06-09
I have the same problem.

Try this "akonadictl restart" as you, not root. That seems to enable the contacts. This appears to be fixed in 4.5, but I would not go there yet. I've found a couple of other issues....

---

### Post by Captain Giraffe on 2010-06-10
"akonadictl restart"
Gives me:
"Unable to connect to dbus interface of control service"

Same message if I sudo it.

---

### Post by padams10001 on 2010-06-29
I have the same problem. With the restart i get

"Unable to connect to dbus interface of control service"

The akonadi problem seems to come and go but today it is constant.

---

### Post by jaxxed on 2010-08-24
If the 'restart' command returns a failure to connect to the server (it is trying to connect over DBUS, so a DBUS failure likely indicates the the service is not running), then try running the 'start' command instead.

The status command will tell you something as well.

<code>
me@machine:~$ akonadictl -h
Akonadi server manipulation tool
Usage: akonadictl [command]

Commands:
  start      : Starts the Akonadi server with all its processes
  stop       : Stops the Akonadi server and all its processes cleanly
  restart    : Restart Akonadi server with all its processes
  status     : Shows a status overview of the Akonadi server

General options:
  -h [ --help ]         show this help message
  --version             show version information

</code>

This thread is quite old, but I thought I'd post for anybody still reading it.

---


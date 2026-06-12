---
title: "Startup applications."
date: 2009-09-30
forum: General Help
---

### Post by running_rabbit07 on 2009-09-30
I have Firestarter set to start automatically upon startup and it pauses the rest of the startup until I input my password to run it. Is there a way to get it to not do that when it starts?

Thanx!

---

### Post by Brandon Williams on 2009-09-30
I assume that you're using something like gksudo in order to launch Firestarter and that gksudo is asking for your user password. Is this correct?

If so, then you can edit the /etc/sudoers file using:
```
sudo visudo
```
and add a line like this:
```
user ALL=NOPASSWD: command
```
where "user" is your user name and "command" is the full path to the firestarter command.

---

### Post by running_rabbit07 on 2009-09-30
I will give that a try. Thanks.

---

### Post by running_rabbit07 on 2009-09-30
The visudo suggestion didn't work out for me. Thanks anyway Brandon. I probably just didn't type it correctly.

I figured out how to fix it. I removed the -X from the code to make it look like this [s]su-to-root -c /usr/sbin/firestarter[/s] and now it works fine.

---

### Post by running_rabbit07 on 2009-10-01
Previous fix didn't work either. Once I restarted, Firestarter never opened after changing the command.

Any suggestions?

---


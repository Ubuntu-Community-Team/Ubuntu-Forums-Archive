---
title: "Can't see the shut down option."
date: 2010-05-19
forum: General Help
---

### Post by refunlike on 2010-05-19
[IMG]http://i47.tinypic.com/qoxdnp.png[/IMG]

I have been on Ubuntu for two days now and the option was always there, but now its gone. As you can see on the top right the time is in the corner were the option used to be.

---

### Post by Smart Viking on 2010-05-19
gnome-session-save -kill

If you run that you can shut down, the shut down icon should be back when you boot up again. :)

EDIT:

gnome-session-save --kill

And it will give the option to log out not shut down as i said :)

---

### Post by refunlike on 2010-05-19
I done that, then logged off then shut down.

But its still the same.

---

### Post by Smart Viking on 2010-05-19
Then it must somehow been deleted, try right click on the panel, and then "Add to panel..." and then choose "Shut down...". :)

EDIT: Maybe you don't have indicator applet installed or enabled, it looks like it.

---

### Post by refunlike on 2010-05-19
Thats it fixed. :D Thanks very much.

---


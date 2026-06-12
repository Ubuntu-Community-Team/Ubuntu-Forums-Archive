---
title: "Xmms command"
date: 2006-01-24
forum: General Help
---

### Post by Kiwinote on 2006-01-24
Hello,
I have just installed the xmms-goodnight plug-in.
When I want to configure it I need a "**Shutdown command( executed by a system() call!)**" 
Does anyone know what command I need for this?

Thanks
    Kiwinote

---

### Post by hentaidan on 2006-01-24
You can put any command you like in there; as long as it works in a terminal, it should at the time you specify.

To shutdown I use:

```
shutdown -h -t time now
```

Dan

---

### Post by Kiwinote on 2006-01-25
Thanks,
     Kiwinote

---

### Post by RAOF on 2006-01-25
[QUOTE=hentaidan]You can put any command you like in there; as long as it works in a terminal, it should at the time you specify.

To shutdown I use:

```
shutdown -h -t time now
```

Dan[/QUOTE]
That command actually specifies **two** times to shutdown at: *now* which is an alias for +0 minutes (I think), and *-t time*.  Which one takes priority?

You could just drop the "now"

Edit: Ooops, tell a lie.  A quick browse of "man shutdown" says that -t <secs> is the delay between starting the shutdown (and preventing new users from logging on, etc) and actually stopping programs/turning the computer off.  So that command is:  "shutdown now, but wait for *time* seconds before doing you start killing programs"

Perhaps a better command would be "shutdown -h hh:mm" to shut down at a particular time, or "shutdown -h +mins" to shut down in so many minutes.

Edit again: I should actually read the context :oops:.  If the plugin runs a the shutdown command at a certain time, just "shutdown -h now" should do.

---

### Post by Kiwinote on 2006-01-25
I just tried this out:
```
shutdown -h -t time now
```
You need root rights for that so then I tried this:
```
sudo shutdown -h -t time now
```
This does work.
> 
Perhaps a better command would be "shutdown -h hh:mm" to shut down at a particular time, or "shutdown -h +mins" to shut down in so many minutes.
I'll try this out later, because I don't have anymore time now.

Thanks for the help,
  Kiwinote

---


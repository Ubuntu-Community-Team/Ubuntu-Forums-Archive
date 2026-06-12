---
title: "How to logout of custom session?"
date: 2012-02-20
forum: General Help
---

### Post by gldearman on 2012-02-20
Hello, all

I'm running Ubuntu 10.04.

I decided to play around and create a custom session, using Compiz as a standalone window manager, but not running Gnome or any other desktop enviroment.  So far, it seems to work well while I'm using it.  But I don't know how to log out and return to the GDM login screen.  When I'm done, I've either powered down or rebooted the computer from the command line.

What's the command to end an xsession and return to the GDM login screen?

Thanks!

---

### Post by gldearman on 2012-02-20
The only references I can find on the internet indicate that the command should be
```
$ gnome-session-save --logout-dialog
```

But that results only in the error message:
```
** (gnome-session-save:3594): WARNING **: Failed to call logout: The name org.gnome.SessionManager was not provided by any .service files
```

From reading the skimpy man page for gnome-session-save, this would seem to make sense; the command ends a session of gnome, not a session in the gnome display manager.

So, this still leaves me with no way to log out.  I can reboot or shut down, but that's it.

Any ideas?

Thanks.

---

### Post by gldearman on 2012-02-21
Something else I've tried and failed.

```
$ gdm-restart
```

is supposed to log out all users and restart gdm, which would then display the greeter.  This would do what I wanted, sort of ... I'd rather have a solution that didn't involve logging out any other users, but it would be a start.  However, running this command just gives me the message "Not supported".  Not helpful.

---

### Post by stinkeye on 2012-02-22
Don't know if this applies to 10.04 but in 11.10 the command is
```
gnome-session-quit
```

---

### Post by gldearman on 2012-02-23
Stinkeye, that command didn't work, but it did give me the information I needed to identify the problem. Thanks!

The command didn't work because the script for my custom session never launches GNOME session manager, or any other session manager. So, there's no session manager to log out of.

So, now I need to have my custom session launched by a session manager. I think I'm going to try lxsession, unless anyone sees a reason I shouldn't.

Thanks again.

---


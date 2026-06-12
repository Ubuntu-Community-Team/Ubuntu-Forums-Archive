---
title: "Silently auto-start application"
date: 2009-11-05
forum: General Help
---

### Post by Wandel on 2009-11-05
I have a bit of a problem. I have a server that needs to run a terminal program at start up. Adding it to the Sessions under System->Preferences worked just fine, but now I need to add a virtual machine on my server, so I've used this guide: [http://www.quicktweaks.com/2008/10/14/run-your-virtual-os-directly-from-gdm-in-ubuntu/](http://www.quicktweaks.com/2008/10/14/run-your-virtual-os-directly-from-gdm-in-ubuntu/)
And created a GDM entry for the VM. And here comes my problem. As the program is never run when I log directly in to the VM, I tried to create a init script to run the application, and used "update-rc.d XXX defaults" to make it start automatically. The problem is that during the boot when it comes to starting the application, it's run as if I would run it in a terminal, so the boot-up process stops until I kill the application. Is there any way to have it start "silently", ie what's the terminal equivalent to adding an application to Sessions?

Thanks.

---

### Post by Giblet5 on 2009-11-05
The "usual" place to put applications that you want to run at system startup is /etc/rc.local.

How you start a non-gui application silently depends entirely on the application.

What does it do, interface-wise? Wait for input?

What application?

Almost any time someone wants to do something like this, it is not really what they wanted to do... There's always a better way.

---

### Post by Wandel on 2009-11-05
Hey, that did the trick, thanks! I had no idea I was over-complicating things. Apparently that ran the program in a new TTY(that was gonna be my next suggestion on how to solve it).

It's an application developed for the company I work for. It waits for input from a wireless receiver hooked up via USB. The application needs to run while the server is being used for it's purpose, but the user does not need to see the output from the program.
Would this not be what I want to do then?

---

### Post by Giblet5 on 2009-11-05
> **Wandel said:**
> Hey, that did the trick, thanks! I had no idea I was over-complicating things. Apparently that ran the program in a new TTY(that was gonna be my next suggestion on how to solve it).

It's an application developed for the company I work for. It waits for input from a wireless receiver hooked up via USB. The application needs to run while the server is being used for it's purpose, but the user does not need to see the output from the program.
Would this not be what I want to do then?


Ah. Only interactive programs (ones you MUST type things into) require a tty.

Anything else can be run as a background process by putting an "&" at the end of it, although it is wise to redirect the output to a log somewhere...

Example of starting xyzapp from rc.local:

```
...

/usr/bin/xyzapp -lotsofoptions > /tmp/xyzapp.log 2>&1 &

...
```

That will log the standard and error output in /tmp/xyzapp.log, which could be useful when xyzapp starts failing for some reason. The final & causes rc.local to continue executing without waiting for xyzapp to finish running; they'll run concurrently.

The only applications that require a tty are those applications that MUST read input from the user in order to function. Most of these apps can still be used by redirecting their input from somewhere else - even the output of another program. Very powerful, that...

I/O redirection is probably the most powerful aspect of Linux architecture. It's worth reading about. The "Bash" (usual linux command shell) documentation is a good source of information.

---


---
title: "Evolution Mail Client fails to start up"
date: 2011-06-06
forum: General Help
---

### Post by bleutyler on 2011-06-06
Hello.

When I start up Evolution Mail client by any means (toolbar, applet or command-line) it starts up, but then the window turns grey immediately and freezes.  I am forced to close it with the "killall" command.

I love the small mailbox in my toolbar (GNOME) and I don't want to lose it.  I am concerned that removing Evolution by the Ubuntu Software Center will eliminate this wonderful tool.  Otherwise I would re-install it.  

I have made no changes to the mail client in months.  My wife who uses Thunderbird on Windows 7 is still operating normally, so I do not believe anything changed on the mail server.

Any recommendations?

---

### Post by philinux on 2011-06-06
> **bleutyler said:**
> Hello.

When I start up Evolution Mail client by any means (toolbar, applet or command-line) it starts up, but then the window turns grey immediately and freezes.  I am forced to close it with the "killall" command.

I love the small mailbox in my toolbar (GNOME) and I don't want to lose it.  I am concerned that removing Evolution by the Ubuntu Software Center will eliminate this wonderful tool.  Otherwise I would re-install it.  

I have made no changes to the mail client in months.  My wife who uses Thunderbird on Windows 7 is still operating normally, so I do not believe anything changed on the mail server.

Any recommendations?

Open a terminal. Apps>access. And type ```
evolution --component=mail
```

Press enter. Post back what the errors are.

---

### Post by bleutyler on 2011-06-06
I am afraid it only gets this far along:


```
tyler@inspiron:~$ evolution --component=mail
evolution-shell-Message: Killing old version of evolution-data-server...
** (evolution:21026): DEBUG: mailto URL command: evolution %s
** (evolution:21026): DEBUG: mailto URL program: evolution
```

---

### Post by philinux on 2011-06-06
> **bleutyler said:**
> I am afraid it only gets this far along:


```
tyler@inspiron:~$ evolution --component=mail
evolution-shell-Message: Killing old version of evolution-data-server...
** (evolution:21026): DEBUG: mailto URL command: evolution %s
** (evolution:21026): DEBUG: mailto URL program: evolution
```

Try this.

```
killall evolution-alarm-notify
```

Then try starting evo. If it starts try to see if a recent calendar appointment is causing it to crash.

You can also try this to get it to start.

```
evolution --disable-eplugin
```

---

### Post by bleutyler on 2011-06-06
Actually, I shutdown the laptop and the evolution alarm process was failing to terminate.  

Now that the computer is rebooted, the error has been resolved.  So it was an error with the evolution-alarm-notify process I believe.  Evolution works great now.

Thank you for your help!

---


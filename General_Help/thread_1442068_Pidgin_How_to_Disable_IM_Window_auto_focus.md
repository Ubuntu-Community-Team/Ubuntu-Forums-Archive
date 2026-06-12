---
title: "Pidgin: How to Disable IM Window auto focus?"
date: 2010-03-29
forum: General Help
---

### Post by morgue on 2010-03-29
When I get a new message from someone who I'm not already talking to, the new IM gets auto focus, how can I disable this?

---

### Post by Elaztic on 2010-03-29
Hi,

In tools - preferences - interface (first tab)
Have you tried to set:

'Hide new IM conversations' to 'always'?

Don't know if it will help but you can try.

---

### Post by morgue on 2010-03-29
That hides it completely and I'm notified via the tray icon, but not exactly what I want, I want it to flash on my task bar (which it already does) but not gain focus... Just stay there minimized until I open it...

---

### Post by morgue on 2010-04-09
bump

---

### Post by morgue on 2010-04-11
On Digsby the option is called
New conversation windows -> start minimized in taskbar

There´s also
automatically take focus
and start hidden (tray icon blinks)

I need to find this on Pidgin =/

---

### Post by morgue on 2010-04-12
This guy has something here
[http://ubuntuforums.org/showthread.php?t=916853](http://ubuntuforums.org/showthread.php?t=916853)

It runs this script on devilspie
```
(if 
        (and
                (is (application_name) "Pidgin")
                (not (is (window_name) "Buddy List"))
        )
        (begin
                (shade)
                (minimize)
                (pin "TRUE")
        )
)
```

But new windows start minimized even if you open them (like when you double click to start a conversation), which is kind of annoying, but close to what I need.

If there is no option nor plugin I guess I have to somehow find if the new window was opened by me, so I don't minimize it.

This tutorial shows how to use devilspie
[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)
You can use gedit instead of vim.

---

### Post by morgue on 2010-04-12
Finally... this is a way to do it, until they include the option on Pidgin, which apparently was removed and was called Minimize new conversation windows.

Anyway... You will need devilspie (available on synaptic).

Follow the tutorial above and use this script:
```
(if
(and
(is (window_class) "Pidgin")
(is (window_role) "conversation")
(contains (window_name) "(*)")
)
(minimize))
```

You will also need to enable the message notification plugin (right now I have 2.6.2... And check the Prepend string into window title option... I have (*) which is the default setting.

And there you go... New conversations will start minimized.

Now just add devilspie to your Startup Applications and forget about it forever XD

:guitar:

---

### Post by morgue on 2010-04-13
Just installed on Windows and what do you think, the Minimize new conversation windows options is right there on the Preferences...

I wonder why is not included on the Linux version...

---

### Post by bonfire89 on 2010-07-02
this method opens the window then minimizes it. 

1. It's annoying because you see the window flash
2. I'm using cairo dock and because the window opens and then minimizes it loses it's "needing attention" state, which means there will be nothing to indicate that I have a new message since the message was already looked at for a split second when the window flashes open.

---

### Post by morgue on 2010-07-02
> **bonfire89 said:**
> this method opens the window then minimizes it. 

1. It's annoying because you see the window flash
2. I'm using cairo dock and because the window opens and then minimizes it loses it's "needing attention" state, which means there will be nothing to indicate that I have a new message since the message was already looked at for a split second when the window flashes open.

Yeah kind of annoying, but that's what we get until the developers add the option to a future version.

How could we request for this?

---


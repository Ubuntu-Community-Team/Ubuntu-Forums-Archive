---
title: "Synergy+ (win server buntu client) how to make it perfect?"
date: 2010-02-27
forum: General Help
---

### Post by Redsandro on 2010-02-27
A topic for the ones who use **Synergy+** on a daily basis.

I was wondering if anyone has it working perfectly? In case you don't know, I am ofcourse talking about [Synergy+]("http://code.google.com/p/synergy-plus/"), the updated [SIZE="1"](2009)[/SIZE] fork of outdated [SIZE="1"](2006)[/SIZE] [Synergy]("http://synergy2.sourceforge.net/").

In order to get Ubuntu to connect automatically to the Windows server, you edit two files:

[SIZE="1"](Tested on Ubuntu 9.10 Karmik)[/SIZE]

**/etc/gdm/Init/Default**
```
#RED Run Synergy+ at login screen
# Synergy+ - place this somewhere before "sysmodmap=/etc/X11/Xmodmap"
/usr/bin/synergyc --daemon Redsandro
```

**/etc/gdm/PreSession/Default**
```
#RED Run Synergy+ after login
# Synergy+ - place this right before initctl
/usr/bin/synergyc --daemon Redsandro
```

[SIZE="1"](I read this somewhere a long time ago. Not my idea. I have this long standing habit of tagging edits with #RED so I know what was there and what I put there.)[/SIZE]

Now it automatically connects when you turn on the Linux machine. So it already works in the login screen. After logging in, it still works. Pretty nice.

**But**

When I go to the **Switch User** screen, it doesn't work anymore. And when I connect back to where it used to work, it still doesn't work anymore.

I have to *killall -9 synergyc* and restart it before it connects properly again.

Does anyone know how to make it so that the synergyc connection is also preserved when

---

### Post by Redsandro on 2010-03-08
Anyone?

AFAIK, none of the following GDM script locations will launch on SWITCH USER:

Init/
PostLogin/
PreSession/
PostSession/

Nowhere can I kill synergyc. But how come it is occupied during the GDM screen but available again at the new login?

-edit-

It won't work in the new session or gdm because the old session is still connected. We can kill synergy before opening a new one like so:

```
if [ ! -z `pidof synergyc` ]; then
  killall -9 synergyc
fi
/usr/bin/synergyc --daemon Redsandro
```

But now the behavior is inverted: synergy works everywhere except when logging out the new session to return to the old one. The synergy that used to be active there is now killed, but since no session scripts are run, it won't get reloaded.

Anyone an idea on how to do this?

---

### Post by Redsandro on 2010-03-10
No one?

Can anyone point out to me where I can edit the fast user switch script?

I've tried these files:
[i]/usr/lib/bonobo/servers/GNOME_FastUserSwitchApplet.server
/usr/lib/bonobo/servers/GNOME_FastUserSwitchAppletGdm.server
/usr/share/gnome-2.0/ui/GNOME_FastUserSwitchApplet.xml[/i]
but those seem only markup for titles, positions and translations.

I just need to hack a script call into the applet after the switch user button is pressed. If I can kill synergyc from there, I am halfway there.

---


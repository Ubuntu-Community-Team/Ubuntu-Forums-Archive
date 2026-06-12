---
title: "The panel encountered a problem while loading [...]"
date: 2010-04-14
forum: General Help
---

### Post by MichaelKohler on 2010-04-14
Hi everyone,

when I want to add a new applet (e.g. the Brightness Applet) to my panel in Lucid (10.04) I get the following error:

```
The panel encountered a problem while loading "OAFIID:GNOME_BrightnessApplet".
```

This happens with all applets. This error also appears when after the login. It's quite annoying to not have a clock, tray area and a window list.

I searched in different forums but didn't find a solution.

What I did:


[LIST]
[*]tested with a new user
[*]reinstalled gnome-applets and gnome-applets-data
[*]logout and login again
[*]update/upgrade (system is fully patched and updated)
[/LIST]
~/.xsession-errors says:

```
 
  [cut]

  (child won, so we're not deferring)
  (processing deferred in-call)
  (child won, so we're deferring)
  (child won, so we're not deferring)
  (processing deferred in-call)

** (gnome-panel:1603): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_BrightnessApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred
  (child won, so we're deferring)
  (child won, so we're not deferring)
  (processing deferred in-call)
  (child won, so we're not deferring)
  (child won, so we're deferring)
  (processing deferred in-call)
  (child won, so we're not deferring)

  [cut]
```

.. doesn't seem to help much, I guess..

Please feel free to ask if you need more information about my system.

I have a HP Pavilion dv 6000 series laptop with a Intel graphic card (onboard).

Thanks in advance.

Sincerely,

Michael Kohler

---

### Post by MichaelKohler on 2010-04-14
I've just done a dist-upgrade and I got the following:

```
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libpanel-applet-2.so.0.2.67 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libgweather.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libgweather.so.1.6.8 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libpanel-applet-2.so.0 is empty, not checked.

```

Is this helpful in any way?

---

### Post by MichaelKohler on 2010-04-18
*bump*

---

### Post by peterpall on 2010-12-05
On my computer the following has helped:
 - On the login screen enter your user name but not your password
 - As soon as you have entered your user name and pressed <RETURN> at the bottom of the screen some checkboxes appear
 - Click on these boxes and select a different gnome session then the one you are currently running
 - then enter your password.

Now everything should work again. And it stays this way even if you switch back to your old session.

At least if you are as lucky as I am :)

---


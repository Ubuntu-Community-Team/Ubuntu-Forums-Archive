---
title: "Empathy Auto Away"
date: 2010-04-28
forum: General Help
---

### Post by clearGround on 2010-04-28
Hello,

I have been using Ubuntu 10.04 RC.  I have set up the chat with my facebook account and everything appears to be working except my status does not get set to away when i am not using the computer.  I have waited over half an hour then checked on another computer, but my status remains available.  The screensaver turns on but the status does not change.  Does anyone know how to change this?

Thanks

---

### Post by keithweddell on 2010-05-05
I'd also like to know how to get auto-away to work.

Keith Weddell

---

### Post by vussvillem on 2010-05-13
I do not have a solution. Quick googleing resulted in a suggestion to move back to Pidgin :) Empathy page tells that it has auto away function and Empathy page in Wikipedia tells that it uses gnome-screensaver for auto-away, so it probably turns your status away when you are truly away and screensaver activates (assuming that you have gnome-screensaver....:))

EDIT: There is ~/.gconf/apps/empathy/ui/%gconf.xml file that has a line:

<entry name="show_offline" mtime="1273762480" type="bool" value="false"/>

I do not know what the mtime stands for or how to edit it, but I changed value="false" to "true" and I'll report back if I notice any change.

---

### Post by HumanAnarchist on 2011-06-09
Did you ever report back?

---

### Post by npjoseph on 2011-08-03
It's tied to the screensaver settings.  

[http://superuser.com/questions/144840/setting-empathys-idle-time](http://superuser.com/questions/144840/setting-empathys-idle-time)

---

### Post by Sepero on 2011-09-15
I wish we could figure this out so I could have your "problem", because for me it is a solution. I do not want my computer to ever show as away.

---

### Post by tomasijeaux on 2011-10-08
> **Sepero said:**
> I wish we could figure this out so I could have your "problem", because for me it is a solution. I do not want my computer to ever show as away.
You can turn autoaway off in dconf. Run dconf and go to org/gnome/empathy and unmark autoaway. This worked for me

---


---
title: "double run Namoroka ??"
date: 2010-04-01
forum: General Help
---

### Post by sky net on 2010-04-01
i can't double run Namoroka !!
when i already have run Namoroka , i cant open another window with Namoroka !! just it doesn't run when i run it again ... not responding for a while , then stops
any help guys ??

---

### Post by sky net on 2010-04-01
help guys ??

---

### Post by lovinglinux on 2010-04-01
First, is not considered polite to bump you thread so early. Please wait at least 24 hours to post again if you don not receive any response.

If you are trying to open Namoroka after closing all windows and it doesn't respond, then open the System Monitor and kill *firefox-bin* process.

If this is not the case, then see [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by sky net on 2010-04-01
sorry for being such a ***
thnx for reply
this is not my problem
i just cant open another window of namoroka when i already have one running !!
::: i have namoroka running , i go to open another namoroka window for seconds then close, it shows on the bar nut never shows as window ..
how can i solve it ??

---

### Post by lovinglinux on 2010-04-01
> **sky net said:**
> sorry for being such a ***
thnx for reply
this is not my problem
i just cant open another window of namoroka when i already have one running !!
::: i have namoroka running , i go to open another namoroka window for seconds then close, it shows on the bar nut never shows as window ..
how can i solve it ??

Are you opening a new window from a web site link, from Namoroka menu or by clicking the browser icon in the Gnome menu?

---

### Post by sky net on 2010-04-01
by clicking the browser icon in the Gnome menu

---

### Post by lovinglinux on 2010-04-01
> **sky net said:**
> by clicking the browser icon in the Gnome menu

Close Namoroka, then open the profile manager with this command:

```
firefox -P
```

Then create a new profile and start it. Test if you can start a second window.

---


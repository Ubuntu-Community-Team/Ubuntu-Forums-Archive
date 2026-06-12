---
title: "Evolution: Receive time in 24 hour time format"
date: 2009-07-03
forum: General Help
---

### Post by vlc on 2009-07-03
Hi *,

is there a way to configure Evolution to use the 24-hour time format for the receive time of the e-mails?

It is possible for the calender, but I have not found yet a way to configure the time format for the E-mail.

Thanks a lot in advance!

---

### Post by philcamlin on 2009-07-03
try changing your system clock format

---

### Post by vlc on 2009-07-03
> **philcamlin said:**
> try changing your system clock format

Where can I do that? I only found /apps/panel/applets/clock_screen0/prefs/custom_format in gconf, but this affects only the panel clock.

---

### Post by dcstar on 2009-07-03
> **vlc said:**
> Hi *,

is there a way to configure Evolution to use the 24-hour time format for the receive time of the e-mails?

It is possible for the calender, but I have not found yet a way to configure the time format for the E-mail.

Thanks a lot in advance!

Doubtful, the field in the list display is "massaged" by Evolution to say things like "Today" Yesterday" etc so all of that is probably hard-coded.

The actual date data in the message pane seems to use the System format.

---

### Post by vlc on 2009-07-04
I found a solution:

```
LC_TIME=en_DK.utf8 evolution
```

Putting this into a script and replacing the starters of evolution with this script replaces the 12-hour time format with the 24-hour time format.

Thanks for the responses!

---

### Post by pabloikba on 2009-09-30
> **vlc said:**
> I found a solution:

```
LC_TIME=en_DK.utf8 evolution
```

Putting this into a script and replacing the starters of evolution with this script replaces the 12-hour time format with the 24-hour time format.

Thanks for the responses!

Is there a way to do this for every program universally?

Thanks,

Pablo

---

### Post by vlc on 2009-10-15
> **pabloikba said:**
> Is there a way to do this for every program universally?

Thanks,

Pablo

Normally you should be able to change your system's language on the logon screen. Before logging on, click on Options (on Hardy Heron in the lower left corner) and then on Select Language. en_DK.utf8 corresponds to English (Denmark). This leaves you with English and some European-style settings for time, money, date and so on.

---


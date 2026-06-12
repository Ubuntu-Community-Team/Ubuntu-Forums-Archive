---
title: "Nautilus Error?"
date: 2010-10-19
forum: General Help
---

### Post by thejonnybgood on 2010-10-19
Hi,
I am posting this under General Help because I am not entirely sure which area it belongs in.

My girlfriend, who lives in a different country, is being weaned off of Windows and onto Ubuntu, gently, with the aid of a persistent live USB version of 9.10 which I gave her on my last visit. She has been loving using it for the past 3 weeks, but today, sadly, her minimise, maximise and close buttons "disappeared". I am no expert, myself, and asked her to try restarting Nautilus from the terminal (it vaguely rang a bell to a problem I had once) and she got the following error:
(nautilus:5558): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

I have NO idea what this means and have not found anything conclusive from forum & Google searches of this string - does anyone have any idea what the issue(s?) may be and/or if this error is connected to the missing close (et al) buttons?

Thank you, in advance, for any assistance :)

---

### Post by sikander3786 on 2010-10-19
A simple reboot should rectify that.

It is not a nautilus error, instead it is related to the windows manager/decorator.

Is compiz installed?

It would be better to install fusion-icon, add it to startup applications and then you can use it to reload the windows manager if the problem appears again. fusion-icon sits in system tray once running so no big deal there.

```
sudo apt-get install fusion-icon
```

To add it to startup, navigate to System > Preferences > Startup Applications. Click 'New' and type 'fusion-icon' in the command text box.

---

### Post by thejonnybgood on 2010-10-19
> **sikander3786 said:**
> A simple reboot should rectify that.

It is not a nautilus error, instead it is related to the windows manager/decorator.

Is compiz installed?

It would be better to install fusion-icon, add it to startup applications and then you can use it to reload the windows manager if the problem appears again. fusion-icon sits in system tray once running so no big deal there.

```
sudo apt-get install fusion-icon
```

To add it to startup, navigate to System > Preferences > Startup Applications. Click 'New' and type 'fusion-icon' in the command text box.

Thank you for the quick response.

I have subsequently discovered this issue has been present for 2 days (I was away on business) so a reboot has not fixed the issue, but, yes, compiz is installed.

Should I get her to change anything relating to compiz, or simply install fusion-icon and use that, as you previously stated?

---

### Post by sikander3786 on 2010-10-19
You wouldn't need to change anything relating to compiz I believe.

You can also switch between windows managers using fusion-icon. It would be better to give it a go. Post back if it doesn't work so we can figure out something else.

---

### Post by thejonnybgood on 2010-10-19
Thank you very much (as ever in this community :) )

I will talk her through it, in the next couple days, or try it myself when I visit next week. If it does not work, I will reply here as you suggest.

Thanks :)

---


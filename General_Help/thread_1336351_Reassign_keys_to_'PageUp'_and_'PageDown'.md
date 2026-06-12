---
title: "Reassign keys to 'PageUp' and 'PageDown'?"
date: 2009-11-24
forum: General Help
---

### Post by Pipps on 2009-11-24
I am running Ubuntu Netbook Remix 9.10 on a Dell Mini 10.

I have no proper PageUp and PageDown keys. Holding the FN key and press ArrowUp or ArrowDown is really troubling me, esepcially as I frequently switch to full-sized keyboards during periods throughout the day.

Would it be possible, within Ubuntu, to reassign my '#' key and my 'RightShift' keys, to 'PageUp' and 'PageDown' respectively?

This would make me the happiest netbook owner alive! :)

---

### Post by fancypiper on 2009-11-24
Have you tried clicking System>Preferences>Keyboard Shortcuts yet?

---

### Post by Pipps on 2009-11-24
Thank you for your interest. Yes I have. 

I can advise that PageUp and PageDown are not keyboard 'shortcuts', but rather, standard keyboard functions.

Is it possible to reassign standard keyboard functions within Ubuntu?

---

### Post by drs305 on 2009-11-24
You can reassign keycodes with xmodmap.

To find the current codes, run an app called "xev" (ctrl-c to exit). It will open a small window. Put your cursor over the box, then press the keys you want to reassign and ***note the keycode and name. They may not be the same as my examples.***

On my computer:
# is 12, numbersign
PgUp is 112 Prior
PgDn is 117 Next

Since on my machine # is upper case 3, I would run this command to make the # symbol be PgUp. I have to put in both "3" and "Prior" because keycode 12 is both 3 and #, so I have to designate both the lowercase and uppercase values.
```

xmodmap -e "keycode 12 = 3 Prior"

```
If the # symbol was both lower and upper case, you would use:
```
xmodmap -e "keycode 12 = Prior"
```

The settings only last for the session. You can experiment and once you get the settings the way you want, you can add them as a command in your startup applications (System, Preference, Startup Applications).

---

### Post by Pipps on 2009-11-24
Thank you so much! That looks incredibly useful!

I greatly look forward to attempting your prescriptions and I shall report-back with my findings!

---


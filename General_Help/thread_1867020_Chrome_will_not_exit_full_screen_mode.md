---
title: "Chrome will not exit full screen mode"
date: 2011-10-22
forum: General Help
---

### Post by 98cwitr on 2011-10-22
Worked fine last night, rebooted this morning and now Google Chrome will not exit from full screen mode. I tried uninstalling and reinstalling (no purge) and that didn't work. Any ideas?

---

### Post by satanselbow on 2011-10-22
Sure it was a general problem and not just a hung script on a particular page? F11 toggles as it should here ;)

---

### Post by 98cwitr on 2011-10-22
Yeah I banged on F11 to my heart's content. No joy. Chrome opens in tab view, not sure of any script that would be running there. How would I check for that?


Installed Chromium...works fine!

---

### Post by 98cwitr on 2011-10-24
bump

---

### Post by 98cwitr on 2011-10-30
Solved. Had to delete the google-chrome folder from ~/.config and did a fresh install. Really wonder what caused that though :/

---

### Post by snakerdlk on 2011-11-21
Happened to me in chromium in arch and ubuntu oneiric with google-chrome.

I've been tinkering around, since removing the whole ~/.config/google-chrome directory removes most of the customizations, so I looked for a better way.

I ended up replacing this section:
(this is a from a new generated ~/.config/google-chrome/Default/Preferences)

"browser": {
      "window_placement": {
         "bottom": 586,
         "left": 9,
         "maximized": false,
         "right": 1013,
         "top": 29,
         "work_area_bottom": 600,
         "work_area_left": 0,
         "work_area_right": 1024,
         "work_area_top": 23
      }
   },

No idea why it happens though...

---

### Post by Francewhoa on 2012-08-23
Easier fix
                               1. Using Ubuntu 10.04 LTS navigate to SYSTEM > PREFERENCES > APPEARANCE
2. Click on VISUAL EFFECTS tab
3. Select NONE then EXTRA. It might take a while to activate the EXTRA. A process bar might open. Wait. After that select NONE. This will refresh both the VISUAL EFFECTS and all windows.
4. Try your windows or document again. Now you should see the top toolbar with button. If not press F11. If that doesn't work redo all the above steps again, but this time during the whole process keep your full screen window open in the background or in another screen.

---

### Post by Dentedmind on 2012-12-23
> **Onopoc said:**
> Easier fix
                               1. Using Ubuntu 10.04 LTS navigate to SYSTEM > PREFERENCES > APPEARANCE
2. Click on VISUAL EFFECTS tab
3. Select NONE then EXTRA. It might take a while to activate the EXTRA. A process bar might open. Wait. After that select NONE. This will refresh both the VISUAL EFFECTS and all windows.
4. Try your windows or document again. Now you should see the top toolbar with button. If not press F11. If that doesn't work redo all the above steps again, but this time during the whole process keep your full screen window open in the background or in another screen.
Thank you Onopoc! That was much easier. :)

---

### Post by seanmcnealy on 2013-02-19
> **snakerdlk said:**
> I ended up replacing this section:
(this is a from a new generated ~/.config/google-chrome/Default/Preferences)


I've been having the same trouble after my last update and this edit solved it. Thanks snakerdlk.

---

### Post by aodry on 2013-06-25
Make sure there is no chrome running. Get a list of running processes, then kill them by they pid
```

>ps aux | grep chromium
>kill pid

```

Now you can remove the preference file: (location could be a bit differ based on your distro)
```
rm .config/chromium/Default/Preferences
```

Restart chrome should generate a new Preferences file with everything back to default.

If you want to know what caused it, then you should first make a backup of the Preferences file, then compare it with the newly created one.. In my case there were an extra section, which overruled the windows layout.

---

### Post by oldos2er on 2013-06-25
Old thread closed.

---


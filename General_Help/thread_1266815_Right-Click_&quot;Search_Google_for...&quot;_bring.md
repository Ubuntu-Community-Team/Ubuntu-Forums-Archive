---
title: "Right-Click &quot;Search Google for...&quot; brings up &quot;Mozilla Firefox Start Page&quot;"
date: 2009-09-15
forum: General Help
---

### Post by gardener on 2009-09-15
When I right click on something to bring up the context menu and choose Search Google For, it often creates a new tab with "Mozilla Firefox Start Page." When this occurs, copy and paste within Firefox does not work. I can copy, but it will not be added to the clipboard. The problem seems to be related to an awesome bar problem, where I begin to type and the awesome bar appears and disappears in less than a second as I type. I can't click on anything because it only appears as I am typing and disappears when I stop.
This has been happening for around a year I believe, and the problem followed me from 3.0 to 3.5 (Shiretoko)
I am currently using 3.5.2 on 9.10, but the problem has occurred since I was running hardy heron
Here is what I have tried:
Reinstalling Firefox/Shiretoko
Completely removing the profile and recreating it
Disabling all addons
Installing fresh with no addons and a new profile

I know this isn't an ubuntu problem, but I have never received a response from Mozilla regarding this problem after many, many, many requests.
I have also googled the issue on and off for about a year without results.
I should point out that these same issues occur with another system of mine with a similar setup. I have also tried these steps there with no resolution.

edit: After posting here and on Firefox support I decided the best solution to my problem was to switch to Opera. Unfortunately it will take some getting used to, but I no longer have these issues.

---

### Post by P4man on 2009-09-15
Ive seen it a few times on jaunty as well. And i believe on windows 7 too with FF 3.0.x. However, since moving to karmic with ff 3.5.3 I don't think I had it yet, though i can't be 100% sure. 

Either way, closing ff and restarting it seems to cure it.

---

### Post by lovinglinux on 2009-09-15
See the Troubleshooting section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by gardener on 2009-09-16
Thank you for the responses.
I am unable to find appropriate troubleshooting steps in the troubleshooting section of that thread. There is also no mention of the issue I am having in that post, and I was unable to find a solution to the problem by searching that thread or the forum.
Is this an ongoing problem which does not have a solution? I am considering replacing Firefox as my browser and I would be grateful for an answer.

---

### Post by lovinglinux on 2009-09-16
> **gardener said:**
> Thank you for the responses.
I am unable to find appropriate troubleshooting steps in the troubleshooting section of that thread. There is also no mention of the issue I am having in that post, and I was unable to find a solution to the problem by searching that thread or the forum.
Is this an ongoing problem which does not have a solution? I am considering replacing Firefox as my browser and I would be grateful for an answer.

It looks like a profile issue. Keep in mind that since you are using FF 3.5, the profile is stored on another folder, which is ~/.mozilla/firefox-3.5

You have said that you tried with a new profile, but are you sure you didn't started it with an old profile instead?

You can create and start a new profile with this command:

```
firefox -P
```

---

### Post by gardener on 2009-09-16
I have both moved .mozilla, and deleted/recreated the profile in the profile manager.

---


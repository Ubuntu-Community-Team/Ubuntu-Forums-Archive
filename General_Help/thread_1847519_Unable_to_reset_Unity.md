---
title: "Unable to reset Unity"
date: 2011-09-20
forum: General Help
---

### Post by papibe on 2011-09-20
...and it happened to me :(

Symptoms:
```
Launcher don't show have numbers anymore, so shortcuts don't work.
Ctrl+Alt+T won't open a terminal anymore.
```
What I've researched so far:
[LIST]
[*]Read [this]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") guide.
[*]Read this [other]("http://askubuntu.com/questions/36773/how-to-reset-compiz-in-unity") guide.
[/LIST]
What I've done:
[LIST]
[*]unity --reset-icons
[*]unity --reset
[*]compiz reset
[*]gnome full reset.
[/LIST]
--reset-icons ends in segmentation fault.
--reset trows bunch of Glib erros, and never ends running.

For compiz reset, I did:
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

```
Others things that I tried:
```
gconftool --recursive-unset /apps/panel && rm -rf ~/.gconf/apps/panel && pkill g

gsettings reset com.canonical.Unity.Launcher favorites

rm -rf .gconf .gconfd .gnome2_private/ .gnome2
```
I also re installed unity on synaptic.

I really appreciate any help.
Regards.

P.D.: Since the installation a couple of months ago, I tried to not modify any setting, and unity was running perfectly. Last night I opened 'Appearance' and click on a couple of themes to see how they look and went back to the default. Today the problems appeared.

---

### Post by papibe on 2011-09-20
Also I'm pretty sure Firefox change its looks also:

---

### Post by wildmanne39 on 2011-09-20
Hi, when you reset unity it will never stop, let it run for about 3 minutes then restart your computer, and do not worry about the error messages.
Thank you

---

### Post by papibe on 2011-09-20
Thanks for responding!

I saw a post explaining that (maybe by you ;)), I tried it, but nothings change, that is, lost terminal icon on the launcher, lost numbers shorcuts, and lost general terminal shortcut (Ctrl+Alt+T).

Since my main problem is the launcher I would think that --reset-icons would be more of what I need, but it seg faults.

Any idea?
Kid regards.

---

### Post by wildmanne39 on 2011-09-21
Hi, when you were at that first link you posted did you reinstall the ubuntu desktop also? if you did everything on that page then I to am out of ideas that almost always fixes the problem.
Thank you

---

### Post by papibe on 2011-09-21
No, that's the only thing I haven't tried yet. If there's no other alternative I'll do it.

Does the fact that Firefox change its looks (like it is using a different theme) doesn't give you any hint or idea?

Regards.

---

### Post by wildmanne39 on 2011-09-21
Hi, it might I looked at it, that looks like the global application menu may be disable as well but I am not sure.

Can you post a screenshot of your desktop that might help.
Thank you

---

### Post by papibe on 2011-09-21
Here it goes.

Edit: as you can see, even if I choose the default theme firefox keep in another (lighter) theme.

Edit2: and I realized that the tabs and address bar are inverted.

---

### Post by wildmanne39 on 2011-09-21
Hi, I am doing some research, I do not know if I will find the answer but I will do my best.

I do not believe that it is a unity reset issue.

Is it possible you are having trouble with your keyboard? Does dash work?
Thank you

---

### Post by papibe on 2011-09-21
Yes, tap super works (dash), alt+f1 and alt+f2 works, holding super calls the launcher (but I have to use the mouse to launch apps), ctrl+alt+l locks screen, etc.

What would be the recommended way to reinstall the desktop?

Regards.

---

### Post by wildmanne39 on 2011-09-21
Hi, I have found 2 bug reports so far on the issue.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/772951](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/772951)
[https://bugs.launchpad.net/unity/+bug/774907](https://bugs.launchpad.net/unity/+bug/774907)

I am still looking to see if I can find a fix, the bug reports mention a work around by opening other programs with a launcher I believe you can take a look at them, while I try to find a fix.
Thank you

---

### Post by wildmanne39 on 2011-09-21
Hi, it appears that may not fix it, this is how you can reinstall the desktop.
```
sudo apt-get install --reinstall ubuntu-desktop
```
Thank you

---

### Post by papibe on 2011-09-21
Bug #772951 seems to describe my problem (expect the firefox issue).

Reinstalling....

---

### Post by wildmanne39 on 2011-09-21
Hi, let me know if it worked.

I personally never use the launcher, I installed awn and put it at the bottom of my screen and put a menu applet on it like gnome to has, here is a screenshot.
Thank you

---

### Post by papibe on 2011-09-21
Little difference: my terminal icon is back, but numbers are still gone. Take a look at this picture taken using my phone. It is kind of blurry, but you can see what happens when you hold super.

Regards.

---

### Post by wildmanne39 on 2011-09-21
Hi, yes I saw it, have you just recently installed 11.04, or have you been using it for awhile? 

I really wanted to help you fix it, I see a lot of your posts and you are very helpful to people and I wanted to pass that a long but I am out of ideas, and the bug reports did not look promising.
Thank you

---

### Post by papibe on 2011-09-21
Thanks wildmanne39 for your kind words.

Hopefully it'll be a fix soon. For now, I just added a link to the picture above on Bug #772951. 

Kind regards.

---

### Post by wildmanne39 on 2011-09-21
Hi, your welcome! I used to go to dallas a lot a few years ago, I just live in New Mexico.
Good Luck.

---


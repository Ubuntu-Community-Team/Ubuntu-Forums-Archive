---
title: "not starting firefox"
date: 2010-02-12
forum: General Help
---

### Post by Gingalone on 2010-02-12
Hello everybody,

this morning I got a bad surprise: Firefox doesn't start upon my click on its icon.
Tried to uninstall and reinstall Firefox.... Even its icon disappeared from menus after reinstallation (no way to see it in the menu editor). I tried to start it from command line: 
code 
firefox %u 
and got this reply from Ubuntu:  
GLib-WARNING **: g_set_prgname() called multiple times

I am using Chrome now but I had some useful add-ons on Firefox and wouldn't like to loose them...
Thanks for any help,
Gingalone

---

### Post by wojox on 2010-02-12
Did you try rebooting your computer?

---

### Post by lovinglinux on 2010-02-12
Start Firefox profile manager with this command:

```
firefox -P
```

Then create a new profile and test it. If it works, then you probably have a corrupt file on your profile, sub-optimal settings or an extension preventing FF form starting.

To find if it's an add-on, close Firefox and start your default profile with this command:

```
firefox -safe-mode
```

If that works, then you need to find which add-on is causing the problem.

Post your results.

---

### Post by colobix on 2010-02-12
have you tried to reinstall the firefox 3 package?
Remember to do the killall mozilla-firefox command before you do that

---

### Post by Gingalone on 2010-02-15
Yes, erasing my profile, Firefox (but Namoroka is the name that appears on top of window) starts.
And/or erasing all add-ons it starts....
But I can't understand why at a certain point Firefox started to dislike my add-ons, after having worked with them for a few months (the last add-on installation occurred a couple of months ago).
The only possible explanation is the development of Firefox to Namoroka, the latter is not stable/doesn't run with Firefox add-ons. And this is VERY disappointing!
What to do now? To forget useful add-ons? To migrate to Chrome or Opera?
:frown:
Ciao to all and thanks for help,
Gingalone

---

### Post by lovinglinux on 2010-02-15
> **Gingalone said:**
> Yes, erasing my profile, Firefox (but Namoroka is the name that appears on top of window) starts.
And/or erasing all add-ons it starts....
But I can't understand why at a certain point Firefox started to dislike my add-ons, after having worked with them for a few months (the last add-on installation occurred a couple of months ago).
The only possible explanation is the development of Firefox to Namoroka, the latter is not stable/doesn't run with Firefox add-ons. And this is VERY disappointing!
What to do now? To forget useful add-ons? To migrate to Chrome or Opera?
:frown:
Ciao to all and thanks for help,
Gingalone

When Mozilla releases a new version of Firefox, sometimes it introduces/modify the extension API, so some extensions might not work properly, until the developer of the extension fixes the code.

Have you updated your add-ons lately? 

Please post your add-ons list, so I can take a look to see which one is causing the problem.

---

### Post by Gingalone on 2010-02-15
Thank you lovinglinux (and others) for help.
I made an interesting discovery: if I start Firefox in safe mode and then I immediately close it, then with the simple command "firefox" in terminal, a normal session of my old Firefox in on (with all my add-ons and everything) perfectly working!
But, if I close this Firefox session, giving again the command "firefox" has no effect.... :?:
Anyway, here my add-ons:
DownloadHelper 4.7
Netcraft Anti-Phishing Toolbar 1.4.5.1
Novell Moonlight 2.0
Prism 1.0b3
Ubuntu Firefox Modifications 0.8
UnMHT 5.5.0

Ciao and thanx again!
Gingalone

---

### Post by lovinglinux on 2010-02-15
> **Gingalone said:**
> Thank you lovinglinux (and others) for help.
I made an interesting discovery: if I start Firefox in safe mode and then I immediately close it, then with the simple command "firefox" in terminal, a normal session of my old Firefox in on (with all my add-ons and everything) perfectly working!
But, if I close this Firefox session, giving again the command "firefox" has no effect.... :?:
Anyway, here my add-ons:
DownloadHelper 4.7
Netcraft Anti-Phishing Toolbar 1.4.5.1
Novell Moonlight 2.0
Prism 1.0b3
Ubuntu Firefox Modifications 0.8
UnMHT 5.5.0

Ciao and thanx again!
Gingalone

You have just a couple of extensions, so it will be easy to find the culprit. Start Firefox in safe mode and select the option to disable all extensions permanentely. When Firefox loads, enable the first extension and restart Firefox. Enable the second one and restart Firefox. When it doesn't load, you will know the culprit. I would bet on Netcraft Anti-Phishing Toolbar.

---

### Post by semacore on 2010-02-15
I have the same problem. It started after the update a couple days ago after an update. 

Using ubuntu 9.10 of course with the latest updates. Some details:.

[LIST]
[*] In the system monitor firefox is running but is using 98% of the cpu and there are 2 firefox processes
[*] I have uninstalled and reinstalled firefox using both the synaptic package manager and the software center
[*] I have also uninstalled the flash plugin to see if that helped but it didn't
[*] I have also tried to start in safe mode and repair things there. 
[/LIST]

I am not sure what to do next. 

I should also note I have the following extentions installed and plugins installed in firefox: google toolbar, fireftp, forcastfox, speeddail, an addblocker and some others. 
I have

---

### Post by semacore on 2010-02-15
I had prism installed to and removed it completely. No effect.

---

### Post by Gingalone on 2010-02-15
It looks my problem is with Prism... (Thanx lovinglinux for the try-and-error suggestion)
Disabling it makes my Firefox run correctly.
It's strange since I installed it at least 5 months ago...:o
Ciao and thank you,
Gingalone

---

### Post by lovinglinux on 2010-02-15
> **Gingalone said:**
> It looks my problem is with Prism... (Thanx lovinglinux for the try-and-error suggestion)
Disabling it makes my Firefox run correctly.
It's strange since I installed it at least 5 months ago...:o
Ciao and thank you,
Gingalone

It doesn't matter if you installed 5 months or 10 months ago, upgrading Firefox is when the problems might appear.

---

### Post by semacore on 2010-02-15
I found the culprit. 
It was a plugin called zemanta

---

### Post by lovinglinux on 2010-02-15
> **semacore said:**
> I had prism installed to and removed it completely. No effect.

Have you tried to create a new FF profile?

---


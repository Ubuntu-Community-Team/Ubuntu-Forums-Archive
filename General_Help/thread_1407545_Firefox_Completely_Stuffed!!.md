---
title: "Firefox Completely Stuffed!!"
date: 2010-02-15
forum: General Help
---

### Post by zak_neutron on 2010-02-15
Help

Both versions of FF (3.5 and 3.6) will not start.

I think both versions are still on my machine but neither works - 

I'm running 64 bit Ubuntu 9.10.

The only menu item is "Namoroka" which is seems to be the default browser - however on clicking any html link the only window opened has the following message:

```
XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 252, Column 5:    <key id="manBookmarkKb" key="&bookmarksGtkCmd.commandkey;" command="Browser:ShowAllBookmarks" modifiers="accel,shift"/>
----^
```

The same is true if I enter "firefox" in the terminal window.

If I enter "firefox-3.5" this fails.

I don't when the 3.6 version of ff came on my machine but it really seems to have screwed things up. 

Any pointers or log files needed to help diagnose the problem I would happily supply.

---

### Post by s.fox on 2010-02-15
Hello,

I did a little reading and came across [this]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=fr&comments_parentId=382121&forumId=1") page which may be of some use to you.  I would try some of the suggestions mentioned :)

-Silver Fox

---

### Post by lovinglinux on 2010-02-15
> **zak_neutron said:**
> I don't when the 3.6 version of ff came on my machine but it really seems to have screwed things up.

You probably have *ubuntu-mozilla-daily* ppa enabled. Go to "System >> Administration >> Software Sources >> Other Software" and disable it. Then re-install firefox from Synaptic. That should restore it to Firefox 3.5.

If you want firefox 3.6 with proper branding, then see the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **zak_neutron said:**
> Both versions of FF (3.5 and 3.6) will not start

I think both versions are still on my machine but neither works

When you upgrade firefox-3.5 using the ppa mentioned above, it becomes Namoroka 3.6. So you probably don't have two versions installed.

> **zak_neutron said:**
> The only menu item is "Namoroka" which is seems to be the default browser - however on clicking any html link the only window opened has the following message:

```
XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 252, Column 5:    <key id="manBookmarkKb" key="&bookmarksGtkCmd.commandkey;" command="Browser:ShowAllBookmarks" modifiers="accel,shift"/>
----^
```

It is probably a profile corruption. If removing firefox 3.6 doesn't work, then start Firefox profile manager with this command:

```
firefox -P
```

Then create a new profile and test it. If it works, then you probably have a corrupt file on your profile, sub-optimal settings or an extension preventing FF form starting.

To find if it's an add-on, close Firefox and start your default profile with this command:

```
firefox -safe-mode
```

If that works, then you need to find which add-on is causing the problem.

---

### Post by nexoncore on 2010-02-15
I had the same issue before, I was told a tonne of commands to try but nothing worked. Someone diagnosed it as a faulty update, but none of the other browsers worked either and I resorted to a fresh install of ubuntu.

May sound like the last resort, but atleast it will sort you out. A little advise is use remastersys to backup your OS every month or so, then you can easily revert it.

---

### Post by zak_neutron on 2010-02-16
Thanks Guys

Will try the suggestions and let you know what works.

:p

---

### Post by zak_neutron on 2010-02-17
Disabling all add-ons in 3.6 worked a treat from starting in safe mode.

I have disabled the "ubuntu-mozilla-daily ppa" repo.

Will this stop 3.6 from being ever updated at all now?

Also, from a web design perspective I should like to have FF 3.5 also back (and run both 3.5 and 3.6) - what do I use to get it back?

Thanks

---

### Post by lovinglinux on 2010-02-17
> **zak_neutron said:**
> I have disabled the "ubuntu-mozilla-daily ppa" repo.

Make sure you re-install firefox after disabling the "ubuntu-mozilla-daily ppa", so the 3.6 gets overwritten with the default 3.5.

> **zak_neutron said:**
> Will this stop 3.6 from being ever updated at all now?

No. Firefox will continue to receive regular updates from the Ubuntu official repository, which unlikely will include an upgrade to 3.6, only security patches. Nevertheless, due to recent changes in Mozilla updates policies, it is possible that some day you will get an upgrade to 3.6 from the official repositories.

> **zak_neutron said:**
> Also, from a web design perspective I should like to have FF 3.5 also back (and run both 3.5 and 3.6) - what do I use to get it back?

If you want to have both, then simply download the new version from [http://www.getfirefox.com/](http://www.getfirefox.com/), then extract it to any folder in your home. To start it, open the extracted firefox folder and click the firefox file.

---

### Post by zak_neutron on 2010-02-17
Thanks LovingLinux - most helpful. All sorted now.

I've come from a Fedora background and confess I'm a little muddled by the interactions between FF and Canonical - any good websites to clarify the practicalities of the policy changes you referred to.

Thanks again.....

---

### Post by lovinglinux on 2010-02-17
> **zak_neutron said:**
> Thanks LovingLinux - most helpful. All sorted now.

I've come from a Fedora background and confess I'm a little muddled by the interactions between FF and Canonical - any good websites to clarify the practicalities of the policy changes you referred to.

Thanks again.....

You are welcome.

See [https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

---


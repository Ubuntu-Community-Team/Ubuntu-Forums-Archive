---
title: "How do I hide the last panel?"
date: 2010-07-02
forum: General Help
---

### Post by morgue on 2010-07-02
Running The GNOME Panel 2.30.0, and since I'm using Avant Window Navigator, I'd like to hide the last panel.

I want to keep the shortcuts (like alt+f1, f2, etc...) so killing it isn't what I need.

I've been looking around but I always end up getting a 1px panel on top. Anyone has any suggestions for this?

Thanks!

---

### Post by nothingspecial on 2010-07-02
Press Alt-F2

Type ```
gconf-editor
```

Go apps > panel > default_setup > top_levels > top_panel and change autohide size from 1 to 0

---

### Post by morgue on 2010-07-06
> **nothingspecial said:**
> Press Alt-F2

Type ```
gconf-editor
```

Go apps > panel > default_setup > top_levels > top_panel and change autohide size from 1 to 0

Am I supposed to do something else? This isn't working.

I do this, then logout and log back in but the panel is still there...

---

### Post by whiskeylover on 2010-07-06
Also autohide the last panel

---

### Post by morgue on 2010-07-06
> **whiskeylover said:**
> Also autohide the last panel

It's checked on both top and bottom_panel, still not hidden though.

---

### Post by Simian Man on 2010-07-06
Under gconf-editor, go to desktop->gnome->session->required_componenets.  Then delete the entry for gnome-panel.

---

### Post by morgue on 2010-07-06
> **Simian Man said:**
> Under gconf-editor, go to desktop->gnome->session->required_componenets.  Then delete the entry for gnome-panel.

I want to keep the shortcuts (like alt+f1, f2, etc...) so killing it isn't what I need.

Thanks for the suggestion though.

---

### Post by nothingspecial on 2010-07-06
I don`t know what to say, here is a screenshot of my desktop.

[ATTACH]162609[/ATTACH]

What I posted works for me.

---

### Post by morgue on 2010-07-06
> **nothingspecial said:**
> I don`t know what to say, here is a screenshot of my desktop.

[ATTACH]162609[/ATTACH]

What I posted works for me.

After changing the setting to 0, what do you do?

---

### Post by nothingspecial on 2010-07-06
> **morgue said:**
> After changing the setting to 0, what do you do?

nothing

---

### Post by morgue on 2010-07-06
> **nothingspecial said:**
> nothing

Weird... I can't get it to work neither on my desktop nor laptop...

---

### Post by ScarletWyvern on 2010-07-06
From another thread here:

```
sudo chmod -x /usr/bin/gnome-panel
sudo reboot
```
That will disable gnome-panel entirely.

```
sudo chmod +x /usr/bin/gnome-panel
sudo reboot
```
And that will turn it back on.

---

### Post by Simian Man on 2010-07-06
> **morgue said:**
> I want to keep the shortcuts (like alt+f1, f2, etc...) so killing it isn't what I need.

Thanks for the suggestion though.

Wow, I never knew that the Alt-F2 shortcut was part of gnome-panel.  That seems like a poor design choice to me.  I never use those since I started using Gnome-Do which is what I'd recommend.

---

### Post by morgue on 2010-07-09
> **ScarletWyvern said:**
> From another thread here:

```
sudo chmod -x /usr/bin/gnome-panel
sudo reboot
```
That will disable gnome-panel entirely.

```
sudo chmod +x /usr/bin/gnome-panel
sudo reboot
```
And that will turn it back on.

I want to keep the shortcuts (like alt+f1, f2, etc...) so killing it isn't what I need.

Thanks for the suggestion though.

---

### Post by morgue on 2010-07-09
> **Simian Man said:**
> Wow, I never knew that the Alt-F2 shortcut was part of gnome-panel.  That seems like a poor design choice to me.  I never use those since I started using Gnome-Do which is what I'd recommend.

Thanks, but there really should be a way to hide it, having more programs running in the background seems like a bad solution.

---

### Post by Simian Man on 2010-07-09
> **morgue said:**
> Thanks, but there really should be a way to hide it, having more programs running in the background seems like a bad solution.

I agree with you in general...but gnome-panel is a horrible program and Gnome Do is crazy awesome so...

---


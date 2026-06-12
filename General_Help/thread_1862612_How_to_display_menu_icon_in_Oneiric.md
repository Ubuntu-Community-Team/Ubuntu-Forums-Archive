---
title: "How to display menu icon in Oneiric"
date: 2011-10-16
forum: General Help
---

### Post by ubuntu27 on 2011-10-16
Normally one will follow [this]("http://en.kioskea.net/faq/9010-ubuntu-display-icons-in-the-system-menu") or [this]("http://joesteiger.com/2010/05/23/add-icons-to-menus-and-buttons-ubuntu-10-04/")

But, it seems that they no longer work in Ubuntu Oneiric.
I tried to use 

```
gconftool-2 --type Boolean --set /desktop/gnome/interface/menus_have_icons True
```

But, it did not change anything even after restarting the X-server.

Do any of you know how to display the icons in the menus?


Thank you in advance. :popcorn:

---

### Post by fragos on 2011-10-16
Install Advanced Settings AKA Gnome tweak and look at the Theme settings.

---

### Post by ubuntu27 on 2011-10-16
Hello Fragos. Thank you for the reply.

Is there a way to do it without installing gnome-tweak-tool?

There are many dependencies that it wants to install including gnome-shell.

---

### Post by fragos on 2011-10-16
> **ubuntu27 said:**
> Hello Fragos. Thank you for the reply.

Is there a way to do it without installing gnome-tweak-tool?

There are many dependencies that it wants to install including gnome-shell.

You could try the Configuration Editor. That's what I had used before upgrading from 11.04 and that parameter carried over and still appears when running it. dconf-editor didn't seem to offer that parameter. Ubuntu Teawak has it but the current version is really for 11.04. At any rate, icons on buttons and in menus works for me.

---

### Post by rtimai on 2011-10-18
Ubuntu27,

I had the same symptoms after a recent large update -- menu icons were missing. And GConf-editor showed the option checked. But I found it unchecked in DConf-editor. Remember OGDI: Org.Gnome.Desktop.Interface > Menus have icons. There was no immediate change after enabling that option, but restarting did restore the icons in menus. Don't know if restarting X doesn't work, as you mentioned. Additinally, I never paid much attention to them before, but it looks like only the menu items that start a program have icons, while shell commands (?) don't have icons. Don't know if they were always like that, but anyway if so, I THINK the menu icons have been restored to my desktop, Oneiric on Unity desktop (upgraded with no major issues -- my experience was actually a LOT better than the upgrade to 11.04.)

---

### Post by rtimai on 2011-10-18
fragos,

There's something called GConf-helper running that appears to be some kind of daemon that moves settings from GConf to the new DConf "registry" database. I have notice settings getting moved, given time. I wonder if your settings simply got migrated more efficiently than for Ubuntu27 or me. It's possible that we both might see it fixed automatically just given some time. Just a thought.

---

### Post by fragos on 2011-10-18
> **rtimai said:**
> fragos,

There's something called GConf-helper running that appears to be some kind of daemon that moves settings from GConf to the new DConf "registry" database. I have notice settings getting moved, given time. I wonder if your settings simply got migrated more efficiently than for Ubuntu27 or me. It's possible that we both might see it fixed automatically just given some time. Just a thought.

This whole gconf dconf thing has gotten a bit murky. You can run both those editors and they don't always indicate the same configuration for those parameters found in both. To make things even less clear my dconf calls out some configuration settings that are different than what I see on the screen. I try to stick with the configuration control available in the aps themselves. That bit about GConf-helper is interesting. I just noticed that the dconf editor now shows more configuration parameters than it did last time I looked at it.

---


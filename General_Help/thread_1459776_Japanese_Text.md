---
title: "Japanese Text"
date: 2010-04-21
forum: General Help
---

### Post by HoodedHooligan on 2010-04-21
I'm new to both Ubuntu and forums so feel free to correct me at any point.

So here's the deal. I need to be able to switch between English and Japanese text when typing on my computer but I have no idea how to. I figured it out on both Windows and Mac but Ubuntu is giving me some trouble. I figure IBus is where I'm supposed to be going but even though I selected Japanese, it just isn't working.

Can someone help?

---

### Post by Rounin on 2010-05-16
Japanese can be input by installing the packages "ibus-anthy", "ibus-gtk" and "ibus-qt4".

When the installation is complete, "ibus-setup" should be started, and the IBUS daemon should be allowed to start. Then from the list of available languages in ibus-setup, add "Anthy" from the Japanese section to the list.

IBUS should automatically become the default input method for most applications from then on, and can also be activated in many applications by clicking on a text input field to get a context menu, navigating to the option to select an input method, and selecting IBUS. Applications that are already running may or may not have to be restarted.

Finally, it should be possible to activate Japanese input by pressing Ctrl + Space.

Some setup may be required to cause IBUS to start automatically upon booting, but I haven't tried to do that.

An alternative to IBUS which also works is scim-anthy (and scim-gtk2-immodule and scim-qtimm), which is installed and started much the same way. Yet another one is uim-anthy with whatever other modules UIM has.

---

### Post by frostschutz on 2010-05-16
I'm not sure about desktop Ubuntu, but netbook Ubuntu lets you add language in the system languages menu with like two clicks and it just works (installs ibus-anthy etc. for you)

---


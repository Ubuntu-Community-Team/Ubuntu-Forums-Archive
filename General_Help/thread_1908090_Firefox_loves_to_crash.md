---
title: "Firefox loves to crash"
date: 2012-01-12
forum: General Help
---

### Post by ZootNerper on 2012-01-12
Hi All,

All my Firefox wants to do is crash. Not at the moment, but it will.

I am running Ubuntu 11.10, Firefox 9.01, and have Ubuntu restricted extras installed. I have no Firefox addons installed. I frequently have 10-30 pages open.

I was running Ubuntu 10.10, with the latest Firefox from the firefox-stable ppa. Then I had some addons. It crashed frequently too.

I have a feeling this is linked to the Internet connection. I have ADSL, but the speed can vary. An Internet game I play always has a ping of 400-500ms and sometimes worse. Could be something like "Sync" fails to connect to it's site and then FF crashes? I used to have some pages automatically reload too. Just a feeling though.

Anyone have any ideas as to what I can do to stop these frequent crashes?

---

### Post by Buntumatic on 2012-01-12
What this crash looks like. Have you tried to run it from terminal, do you have plenty of RAM for opening multiple tabs.

---

### Post by coldraven on 2012-01-12
The only thing that crashes my Firefox is Flash.
Try getting the Flash-Aid add-on and get the latest version of Flash. It might make a difference.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by ZootNerper on 2012-01-12
I have 4GB of RAM of which now 1.4GB is being used.

The crash just goes to the FF report window.

I have not tried to run from a terminal. I will do (have to go to work now) and report back.

I do not have any windows with Flash in, but maybe it's in some advertisement somewhere. I will update this when I get back.

Thanks a lot for your help so far :)

---

### Post by ZootNerper on 2012-01-14
Sorry for the slow update.

I canNOT get FF to load this page! I sense and international conspiratory! This is coming to you via Chrome :}

Even if it only load the forum home page (i.e. no other tabs or windows open), and then I search for this page and then load it. I get the page displayed (not sure if all, put I can see my original post) and then poof FF has crashed.

I have not updated Flash. I ran FF from a terminal and got the following:

-------------

zoot@Bollocks8:~$ firefox

(firefox:7640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:7640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:7640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:7640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:7715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:7715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:7715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:7715): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
zoot@Bollocks8:~$ 

-----------------

Looking on Google I found this error and a possible solution being to  install:

sudo apt-get install gtk2-engines-pixbuf

This did stop the above errors, but FF still crashed. So, I have now removed the above.

Any ideas?

---

### Post by lovinglinux on 2012-01-20
Test Firefox in safe mode and report back

```
firefox -safe-mode
```

---

### Post by dragonfly41 on 2012-01-20
I've experienced firefox crashes and I find the firefox add-on session manager useful to selectively disable problem tabs (a menu of tabs is shown) and different sessions can be archived and started.

After installing look at the preferences in session manager.  Firefox > Get Add-ons > Session Manager > Preferences.

[https://addons.mozilla.org/en-US/firefox/addon/session-manager/](https://addons.mozilla.org/en-US/firefox/addon/session-manager/)

---

